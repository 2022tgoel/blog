
https://arxiv.org/pdf/2404.02258 and https://arxiv.org/pdf/2502.11089 are interesting papers since they take different approaches at implementing token sparsity and there are a lot of things I don't understand yet. 

The MoD paper highlights some key design challenges:

1. One issue is that the gradient of a top-k selection is 0. MoD handles this by weighting the result of attention by the routing score. 

In math, this means that 

$x^{l+1}_i = \begin{cases} r^l_i \text{SparseAttn} (X^l) + x^l_i & r^l_i \text{ in top k } \\ x^l_i & \text{ otherwise} \end{cases}$ 

2. Another key issue:

> While expert-choice routing has a number of advantages, it has one distinct problem: the top-𝑘 operation is non-causal. This means that whether a given token’s routing weight is among the top-𝑘 for the sequence depends on the values of the routing weights for tokens that come after it, which we don’t have access to when autoregressively sampling.


DeepSeek's approach to these problems: 

* Instead of having a global routing weight, there is per-query routing.
	* Key insight here is that this choice completely avoids problem #2 from the paper above. This feels like the better choice. 
* For good performance, they implement chunkwise-routing/sparsity, chunking query heads and temporally contiguous segments of the KV-cache together. 
* The solution to problem #1 is not really addressed in the paper. The best answer I could find is this: https://github.com/lucidrains/native-sparse-attention-pytorch/blob/7ebebcaa5248a4cb827026d22ed7bab9746237e8/native_sparse_attention_pytorch/triton_native_sparse_attention.py#L1060

* They set $d < l$ to avoid "information fragmentation". It's not clear to me what this really means. 


Actually fla has an implementation:

https://github.com/fla-org/native-sparse-attention/tree/main