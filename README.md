# UMDrive
## Background
Robust and reliable Simultaneous Localization and Mapping (SLAM) systems are crucial for safety-critical applications such as mobile robots and autonomous driving. The past few years have witnessed significant advancements in RGB-based SLAM. While most of the previous works have improved the performance of RGB-based SLAM through modern learning methods and novel optimization algorithms, notable degradation in SLAM performance under diverse conditions has been consistently observed. In addition, there exists a scarcity of datasets that cover diverse environments, which are crucial for assessing and enhancing the robustness of SLAM systems. To this end, we propose \textbf{UMDrive}, a comprehensive full-cycle pipeline encompassing data generation, SLAM optimization, and downstream evaluations. Our pipeline makes three appealing contributions. 
- `1)` To improve the robustness of SLAM in dynamic environments, we propose a novel generative in-painting method for dynamic objects.
- `2)` We propose a novel assessment metric based on frame drop rates to identify the most reliable SLAM systems.
- `3)` Centered around the theme of robust and reliable SLAM, we establish a systematic data generation platform in CALRA to synthesize RGB data under diverse conditions. Extensive experiments demonstrate that our framework can evaluate and optimize the performance of SLAM systems.
## Dependency
