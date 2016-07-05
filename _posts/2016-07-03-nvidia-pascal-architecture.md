---
layout: post
title:	Talk about nvidia's new Pascal architecture.
category: blog
description: Some data we should remember about pascal architecture compared with previous ones
---

by Alex Jia

Nvidia has announced its new pascal architecture in GTC 2016. There are 4 new features coming with it. In this blog, I want to list some data about this architecture, and compare it with previous Kepler and Maxwell architecture.

The 4 features are ranging from computing ability to GPU memory performance. I will list performance data about these features of Tesla P100, Maxwell M40 and Kepler K40 devices below, to give you a general idea of differences between them.

## Extreme Computing Performance

<table style="border: 1px solid #ccc" width="700" border="10" height="200">
<tr>
	<th width="250" style="border: 1px solid #ccc"><left>Architecture</left></th>
	<th width="150" style="border: 1px solid #ccc"><center>Pascal</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Maxwell</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Kepler</center></th>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>Model</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>P100</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>M40</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>K40</center></td>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>Compute Capability</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>6.0 (sm_60)</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>5.2 (sm_52)</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>3.5 (sm_35)</center></td>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>Peak Double Precision(FP64)</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>5.3 TFLOPS</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>0.2 TFLOPS</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>1.7 TFLOPS</center></td>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>Peak Single Precision(FP32)</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>10.6 TFLOPS</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>6.8 TFLOPS</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>5.0 TFLOPS</center></td>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>Peak native Half-precision(FP16)</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>21.2 TFLOPS</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>not support</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>not support</center></td>
</tr>

</table>
<font style="line-height:1.5;">
<br/>
</font>

## NVLink
<table style="border: 1px solid #ccc" width="700" border="10" height="100">
<tr>
	<th width="250" style="border: 1px solid #ccc"><left>Architecture</left></th>
	<th width="150" style="border: 1px solid #ccc"><center>Pascal</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Maxwell</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Kepler</center></th>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>GPU-to-GPU data transfer</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>NVLink: 160GB/s bi-direct</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>PCIe 3.0x16 lane: 16GB/s bi-direct</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>PCIe 3.0x16 lane: 16GB/s bi-direct</center></td>
</tr>
</table>

<font style="line-height:1.5;">
<br/>
</font>

## HBM2
<table style="border: 1px solid #ccc" width="700" border="10" height="100">
<tr>
	<th width="250" style="border: 1px solid #ccc"><left>Architecture</left></th>
	<th width="150" style="border: 1px solid #ccc"><center>Pascal</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Maxwell</center></th>
	<th width="150" style="border: 1px solid #ccc"><center>Kepler</center></th>
</tr>
<tr>
	<td width="250" style="border: 1px solid #ccc"><left>GPU-to-GPU data transfer</left></td>
	<td width="150" style="border: 1px solid #ccc"><center>720 GB/s</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>288 GB/s</center></td>
	<td width="150" style="border: 1px solid #ccc"><center>288 GB/s</center></td>
</tr>
</table>

<font style="line-height:1.5;">
<br/>
</font>

## Unified Memory and Compute Preemption
Unified memory is not very related to GPU performance, so I just list the name here. 
Let's talk about Compute Preemption, which is an important hardware and software feature added to GP100. 
In Kepler and Maxwell, compute tasks are preempted at thread block granularity, thread block of next compute task in same stream will wait until one of SMX avaliable. 
In Pascal, compute tasks can even be switched on instruction level, which could allow to you shared you GPU resources better. 
But there might be some performance issues, because frequent task switching will make GPU spend a lot of time on storing one state or loading another.


 