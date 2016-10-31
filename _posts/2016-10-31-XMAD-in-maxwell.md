---
layout: post
title:	XMAD instructions in Maxwell Architecture
category: blog
description: XMAD instruction
---

by Zhe Jia

As njuffa talked in [this nvidia dev-forum thread](https://devtalk.nvidia.com/default/topic/804281/cuda-programming-and-performance/maxwell-integer-mul-mad-instruction-counts/post/4423835/), from Maxwell architecture many IMAD instructions could be emulated by XMAD insstruction. Because for 32 bit multiplies, XMAD shares FFMA hardware unit which could have 4x throughput than that of IMAD, and it only cost 3 XMADs to implement an IMAD. Thus there will be a net win of 1.3x (4.0/3.0).

Thanks to Scott Gray pointed [the usage of XMAD in this reply](https://groups.google.com/forum/#topic/maxas-discuss/4rovrjSRzKA)
(shamelessly copy them here)
XMAD is a 16 bit multiply 32 bit accumulate.

A single unsigned 16bit mad(flags for signed mode are available):
XMAD d, a, b, c;

A 16 bit times a 32 bit:
XMAD d, a, b, c;
XMAD.PSL d, a.H1, b, d;
or
XMAD d, a, b, c;
XMAD.PSL d, a, b.H1, d;

A 32 bit times a 32 bit and just keeping the lower 32 bits of result:
XMAD.MRG x, a, b.H1, RZ;
XMAD d, a, b, c;
XMAD.PSL.CBOC d, a.H1, x.H1, d;

But I still cannot able to figure out the meaning of each individual suffix.
If anyone see this blog happens to know the details of this instruction, please correct me or help me.:D
