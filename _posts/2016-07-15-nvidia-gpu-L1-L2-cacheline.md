---
layout: post
title:	Nvidia Pascal GPU L1/texture cache and L2cacheline experiment
category: blog
description: 
---

by Alex Jia

It was said L1 cacheline is 128 bytes and L2 cacheline is 32 bytes, so I did this experiment to test it.

#Texture cache
cache block size: 1D 32 bytes
[Transactions from the texture cache are 32 byte units. ](http://docs.nvidia.com/nsight-visual-studio-edition/4.0/Nsight_Visual_Studio_Edition_User_Guide.htm#Analysis/Report/CudaExperiments/KernelLevel/MemoryStatisticsTexture.htm#Chart)

2D block data can be cached in texture, if you have an 1D linear access patterns, global memory may be more efficient.

#L1 cache
cache line size: 128 bytes

#L2 cache
cache policy: LRU
cache line  size: 32 bytes
