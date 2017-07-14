---
layout: post
title: "IP Camera" 
---

IP Camera was the main project I involved when I was working at [**Galaxycore Inc**](https://www.linkedin.com/company-beta/1054586/).
This project is planned to produce the multimedia SoC for digital video cameras commonly employed for surveillance. 
we customized the original linux-2.6 kernel to add our own features. The project has been kicked off for one year before I joined the company, 
and I was on it for one year. 

My roles in the project were as below:  
•	Bringing up modules  
•	Linux device driver programing  
•	Unit test and verification for modules  

I mainly take the responsibility for the core module - image signal processing (ISP) pipeline consisting of Sensor, ISP and Video Codec. 
I brought up sub-modules like sensors (OV2710, AR0130), ISP, overlay on streams in the diagnosis code branch (used for bringing up and testing single module), 
and then ported them to Linux device drivers. I designed the ISP module driver based on the Video for Linux Two (V4L2) framework. 
In this way, all the sub-modules were abstracted into sub-devices and formed a device graph, so that I could use uniform APIs like IOCTL and other system calls 
in user space for the whole pipeline. Furthermore, I optimized the memory allocation of project’s finite DRAM, which could adjust dynamically 
according to the sensor’s resolution and different scenes. 

![](/images/20150701/Pipeline.png){: .center-image }
***Figure 1.** Video Processing Pipeline for IP Camera*

I mainly programed under the Linux operating system using C language and arm-none-linux-gnueabi-gcc as the cross-compiler toolchain. 
In the process, I taught myself Linux device driver and V4L2 API specification, H.264 Codec knowledge etc. This project enhanced my understanding of ARM architecture, cache coherency and kernel memory management. 







