[Quora: Why are GPUs well-suited to deep learning?](https://www.quora.com/Why-are-GPUs-well-suited-to-deep-learning/answer/Tim-Dettmers-1)

The real reason GPUs are faster than CPUs for deep learning is memory bandwith, not neccessarily parallelism.

CPUs are latency optimized.
GPUs are bandwith optimized.

Can imagine this as a CPU being like a Ferrari and a GPU being like a pickup truck. Both can deliver items from point A to point B. A Ferrari will travel those distances faster, but will need to make more trips to deliver all items. In the same way, CPU is good at fetching a small amount of memory quickly, while the GPU is good at fetching large amounts of memory period.

GPUs hide their low latency under thread parallelism. They can use many threads to hide the low latency, CPUs cannot because they have a smaller amount of cores. 

Consider an example where you now have a large fleet of Ferraris vs. a large fleet of Big Trucks. Even if you have a larger amount of Ferraris, unloading takes a larger amount of time for the Ferraris than the big truck. As a side note, this is why adding more threads for a CPU does not make sense. 

This example relates to the first step where memory is fetched from the main memory (RAM) to the local memory on the chip (L1 cache and registers). Here, the bottleneck for performance in this second step (grabbing local memory) is the size of the memory. Normally we want to keep memory size low because it takes up space, and space adds distance, which is critical for fast access to local memory. So, usually you have your local memory stores very close to L1 cache and registers.

The advantage of GPUs is that you can have a small pack of registers attached to each processing unit (stream processor), of which the GPU has many. Thus, on a GPU, we can have a lot of register memory, which makes it fast and also means that overall we can have a ton more register memory. Register memory is fast access, so the more we have, the faster our programs. 

Aggregate register sizes for GPUs are about 30x the aggregate register size of CPUs. 

Register size needs to be fine tuned. NVDA has developed compiler tools that help with this. They can tell you whether you're using too much or too little register memory per stream processor. 

https://timdettmers.com/2023/01/30/which-gpu-for-deep-learning/#Overview

Order of importance for GPU performance: 
Tensor Cores >> Memory Bandwith of a GPU >> Cache Hierarchy >> FLOPS of a GPU 

Tensor Core => Meant for Matrix Multiplication