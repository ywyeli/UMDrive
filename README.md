# UMDrive
## Background
Robust and reliable Simultaneous Localization and Mapping (SLAM) systems are crucial for safety-critical applications such as mobile robots and autonomous driving. The past few years have witnessed significant advancements in RGB-based SLAM. While most of the previous works have improved the performance of RGB-based SLAM through modern learning methods and novel optimization algorithms, notable degradation in SLAM performance under diverse conditions has been consistently observed. In addition, there exists a scarcity of datasets that cover diverse environments, which are crucial for assessing and enhancing the robustness of SLAM systems. To this end, we propose `UMDrive`, a comprehensive full-cycle pipeline encompassing data generation, SLAM optimization, and downstream evaluations. Our pipeline makes three appealing contributions. 
- To improve the robustness of SLAM in dynamic environments, we propose a novel generative in-painting method for dynamic objects.
- We propose a novel assessment metric based on frame drop rates to identify the most reliable SLAM systems.
- Centered around the theme of robust and reliable SLAM, we establish a systematic data generation platform in CALRA to synthesize RGB data under diverse conditions. Extensive experiments demonstrate that our framework can evaluate and optimize the performance of SLAM systems.
## CARLA Synthetic Dataset Generation Guide
### Preparation
Download [CARLA v0.9.10](https://carla-releases.s3.eu-west-3.amazonaws.com/Linux/CARLA_0.9.10.tar.gz) and unzip it under `./CARLA_Simulator`. Follow the install instruction of `scenario_runner` of commit [ad71a2c](https://github.com/carla-simulator/scenario_runner/tree/ad71a2c7ed012d735be2b1158fca51b0761ff26b).

We test our repo with on Ubuntu 18.04 or 20.04.

### Data Collection

Turn on CARLA as default and then run the following shell script. 

`cd ./carla-nuscenes/scripts`

`bash routes_baselines.sh`

LiDAR configurations can be accessed at `./carla-nuscenes/hyperparams`. Camera configurations can be accessed in `./carla-nuscenes/scenario_runner/lidar.py`. The density of Vehicles and Pedestrians can be accessed on `Line 397-422` in `./carla-nuscenes/scenario_runner/srunner/scenarios/route_scenario.py`. The datasets can be accessed at `./carla-nuscenes/dataset`. 

Run the following code to create NuScenes-formatted labels.

`cp -r ./carla-nuscenes/dataset/[YOUR LIDAR PLACEMENT]/training/label_2 ./NuScenes_generate/label_2` 

`python ./NuScenes_generate/create_test_wide.py`

`python ./NuScenes_generate/create_trainval_wide.py`

Copy the folder `./NuScenes_generate/maps`, `./NuScenes_generate/v1.0-trainval` and `./NuScenes_generate/v1.0-test` to your dataset root. Replace the file `splits.py` in the NuScenes-devkit on your environment with our `./NuScenes_generate/splits.py`, otherwise the NuScenes-devkit can not recognize our dataset.

