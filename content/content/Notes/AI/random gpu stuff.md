
* **Head-of-Line (HOL) Blocking**  is a performance problem where a packet at the front of a data queue gets delayed, holding up all subsequent packets, even if they are destined for different places and could move ahead
	* To avoid this problem, packets have a virtual lane (VL). 
		* Each virtual lane is assigned credits through **credit-based flow control** and the packets are independently buffered (credits represent buffer space at the next hop). This way you can send packets to one virtual lane while another is congested!
	* VL mapping is done through a **service lane** (SL) --> VL mapping table that is configured by OpenSM (or whatever is the **subnet manager**) on the NIC 

* Cluster Launch Control allows you to write persistent kernels while maintaining load balancing and preemption really easily (thread block work stealing will fail if a higher priority kernel launches)
https://hazyresearch.stanford.edu/blog/2025-09-22-pgl

* GPUs have page tables. But it's not like CPUs where you have different processes and you want to abstract away memory addressing logic by giving each process a virtual address space and a page table. 
	* On NVIDIA GPUs, the fundamental unit is a **CUDA context**. These are managed internally by the process issuing the kernels. 
		* `cudaSetDevice(1)` sets the CUDA context to the context for device 1
	* Kernels are launched into a context, so kernels with the same context share the same virtual address space. The context is per device.
* Unified Virtual Addressing (UVA)
	* with the limitation that it applies only within a single process
	* UVA enables “Zero-Copy” memory, which is pinned host memory accessible by device code directly, over PCI-Express, without a `memcpy`. This is cool!
```
cudaDeviceCanAccessPeer(&can, 0, 2);
cudaSetDevice(0);
cudaDeviceEnablePeerAccess(2, 0);
cudaSetDevice(2);
cudaMalloc(&p, size);
```

CUDA installs PTEs in GPU 0’s page table

* Symmetric heaps
	* CUDA VMM API allows you to explicitly manage virtual address ranges, ` cuMemCreate`, `cuMemMap`, `cuMemRelease`, etc. 
	* NVSHEM cannot use peer mappings as exemplified above, because the same VA needs to correspond to a physical page on every device.

