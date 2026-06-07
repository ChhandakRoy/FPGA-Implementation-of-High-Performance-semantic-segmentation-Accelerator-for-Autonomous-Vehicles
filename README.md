ThisworkpresentstheFPGAhardwareaccelerationof theContextualPyramid
(CTP)module,originallyproposedaspartofCTPNet [13]—alightweightreal-time
semanticsegmentationarchitectureacceptedforIEEETransactionspublication[13].
ThehardwareacceleratorisolatesandmapstheCTPmodule’smulti-scalecontextag
gregationontoafullypipelinedFPGAdatapath,enablingindependentbenchmarking
ofthemodule’sinferenceefficiencyonedgehardware

Parameter and computational efficiency. The CTP module, at 0.03M param
eters and 0.167GFLOPs, is 10–70× more parameter-efficient and 24–75× leaner in
computation than full networks such as ERFNet [19] and ICNet [18], and reduces
FLOPs by 75–200× relative to the heavyweight contextual modules ASPP [14] and
PPM [15]. This reduction is achieved through Stage 1 channel compression and the
use of depthwise dilated convolutions in place of standard 3×3 operations.
Throughput and latency. Operating at 774FPS, the proposed accelerator outper
forms every full-network FPGA result in Table 14 by a substantial margin—6× faster
than BiSeNetV2 [20,21] (102FPS) and over 11× faster than ICNet [18] (68FPS).
The 1.29ms module-level latency provides considerable headroom for integration
with a full encoder–decoder backbone while maintaining the real-time constraint of
≤33ms at 30FPS.
Power and on-chip resource utilisation. The 0.77W on-chip power consump
tion is 4–19× lower than full-network FPGA implementations, including ENet [16]
(7.3W), BiSeNetV2 [20,21] (14.8W), and SegNet [17] (25.0W). With 15.3% LUT
utilisation, over 84% of the Virtex-7 fabric remains available for the backbone and
post-processing pipeline. The higher LUT count relative to SE-Block [26,27] (11k)
and CBAM [25,26] (24k) is attributable to the substantially richer representational
capacity of the CTP module, as reflected in its superior accuracy contribution.
Accuracy contribution. The CTP module delivers a +3.0% mIoU improvement,
closely matching the gains of ASPP [14] (+3.8%) and PPM [15] (+4.1%) while
requiring 75–200× less computation. Against hardware-efficient alternatives, Ligh
tASPP [23,24] (+2.1%) and CBAM [25,26] (+1.5%), the CTP module provides a
superior accuracy boost within a competitive FPGA footprint.
Overall assessment. The proposed accelerator establishes a Pareto-optimal op
erating point across accuracy, throughput, power, and resource utilisation. By
delivering accuracy gains comparable to heavyweight contextual modules at a frac
tion of their computational cost—and at frame rates far exceeding all comparable
FPGA implementations—the CTP module constitutes an effective plug-in context
aggregation block for real-time semantic segmentation on resource-constrained edge
platforms.
