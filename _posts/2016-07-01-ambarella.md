---
layout: post
title: "Smart Rate Control Library" 
---

Smart rate control (SRC) library is an algorithm to do rate control based on the video analysis result for Ambarella's 
S2L and S3L Linux SDK. H.264 and H.265 are very mature video codec standard, so it's usually difficult to have huge optimization for generic scene.
So, instead of looking for a magic receipt to optimize them in generic scene, SRC library seeks for improvement at a particular scene.

![](/images/20160701/H265_optimization.png)
***Figure 1.** Typical H.265 optimization direction [1]*

Most security IP cameras are working at situation A, B or C shown in Figure 1. Some may have been optimized to situation D or E. However, SRC library is able to work at 
situation F. In detail, it not only keeps the advantages of situation D ane E, but also has its own characteristics. It can save more
bits for static areas in a certain frame, and use these saved bits for other motion areas. 

![](/images/20160701/Smart_rate_control_main_loop.png)
***Figure 2.** Schematic of SRC library's main control loop [1]*

Figure 2 shows the schematic of SRC library’s main control loop. Firstly, SRC will initialize control parameters for all the four stream quality level (low, medium, high and ultimate) according to FPS and stream resolution. 
User interface is supplied to select control style for SRC, and quality level can be specified for each stream. Then, motion detection (MDET) will generate new motion value and motion matrix for each frame.
Based on obtained motion and noise value, SRC library will switch profile and update corresponding parameters. Both frame and coding tree block (CTB) level parameters are finally issued to DSP for video codec calculation.

![](/images/20160701/parameter_adjustment.png)
***Figure 3.** Schematic of SRC library's CTB level parameter adjustment [1]*

SRC library can adjust parameters in both traditional frame level and new coding tree block level (here, it’s called as ROI in SRC’s APIs). Combined with MDET library, application is able to distinguish dynamic areas (foreground) with static areas (background) for every frame, and then apply different parameters to corresponding areas.
For any frame, application will save the presentation time stamp (PTS) and then set parameters according to the motion matrix for the relative PTS. In motion detection algorithm, 4x4 ME0 data (8X downscaled from source buffer) is calculated to an average value as input, and outputs the CTB based motion matrix. 
After image processing, a new CTB level motion matrix is generated to specify corresponding parameters for motion and static areas. Finally, this frame level parameter setting is applied to the pre-saved PTS.


***Please note that all the figures are used under the agreement of Ambarella Inc., and only be used here for study and share. Commercial purpose is strictly prohibited!***
### Reference
1. S3L Flexible Linux SDK User Guide: Smart Rate Control Library




