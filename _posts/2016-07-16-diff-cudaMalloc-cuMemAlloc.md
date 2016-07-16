---
layout: post
title:	Difference between cudaMalloc and cuMemAlloc.
category: blog
---

by Alex Jia

cudaMalloc is runtime API, and is defined in cuda_runtime_api.h.
  
cuMemAlloc is Driver API, defined in cuda.h.
  
It is said that Driver API should be a little faster(lacking some status check) than runtime API,  but its advantage is vary limited.

A TIP: memory alloction shouldn't be used in loops.

reference: [nvidia devtalk forum](https://devtalk.nvidia.com/default/topic/387057/cuda-programming-and-performance/difference-between-cudamalloc-and-cudamemalloc-/)
