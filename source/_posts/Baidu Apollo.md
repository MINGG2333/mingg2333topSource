---
title: Co-simulation of Baidu Apollo with Carla
date: 2024-2-3 22:18:17
tags:
 - Apollo
 - simulation
---

Modified: 2024-2-4 21:17:51

Co-simulation with Carla.

<!--more-->

# Quick start

```bash
# Build Apollo docker
bash docker/scripts/dev_start.sh stop
bash docker/scripts/dev_start.sh

# Introduce bridge scripts
cd carla_apollo_bridge
docker cp carla_bridge <apollo_container_name>:/apollo/modules/carla_bridge

# Build Apollo
bash docker/scripts/dev_into.sh
./apollo.sh clean
./apollo.sh build_gpu

# Build bridge
cd /apollo/modules/carla_bridge
chmod +x install.sh
./install.sh
source ~/.bashrc

# Visual Apollo channel
cyber_monitor

./scripts/bootstrap.sh stop
./scripts/bootstrap.sh

# Inject channel message
## start simulator
cd carla_apollo_bridge
cd carla_scripts
./stop_carla.sh
./docker_run_carla.sh
## start bridge
cd /apollo/modules/carla_bridge
python main.py

# Launch Apollo modules
bash docker/scripts/dev_into.sh
## perception module
mainboard -d /apollo/modules/localization/dag/dag_streaming_rtk_localization.dag
cyber_launch start modules/drivers/tools/image_decompress/launch/image_decompress.launch
cyber_launch start /apollo/modules/perception/production/launch/perception_lidar.launch
## turn on "Transform", "Routing", "Prediction", "Planning"
## set route
## control module
ps aux | grep -i apollo
```

<!--more-->

# Co-simulation with carla
