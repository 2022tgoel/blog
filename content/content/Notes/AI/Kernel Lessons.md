
* Triton runs tuning: discard the first run of your kernel
- Be consistent about emptying the cache!
- Be consistent about the gpu you are using! They actually have different performances and run at different clock speeds and stuff
- Don’t use tensor cores when you are checking correctness… tf32 is really bad.
- operate under the assumption a black-boxed GPU kernel is non-deterministic! A common example is that any atomic operation will be executed in an unknown order and result in different floating point accumulations. Lots of cuBLAS and cuDNN kernels are non-deterministic. 