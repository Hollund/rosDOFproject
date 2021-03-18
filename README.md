# rosDOFproject

## Description

This project will use the dexterous_hand_simulated from shadow hand company to analyse and use the many degrees of freedom it posses.

for more information about the shadow hand, please follow the link <https://dexterous-hand.readthedocs.io/en/latest/>.

## Workflow

the workflow of this project is to implement behavior that then commands the docker container of the shadow hand.

## Documentation

### working with docker

### setting the shadow hand

for full documentation follow <https://dexterous-hand.readthedocs.io/en/latest/user_guide/1_3_setting_up_a_simulated_hand.html>

quick guide:

```bash
bash <(curl -Ls bit.ly/run-aurora) docker_deploy product=hand_e sim_hand=true container_name=dexterous_hand_simulated  tag=melodic-release launch_hand=true nvidia_docker=true reinstall=true
```

to use without nvidia_docker remove the tag nvidia_docker=true

to reinstall add the tag reinstall=true

### testing nvidia_docker

full guide: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker

```
sudo docker run --rm --gpus all nvidia/cuda:11.0-base nvidia-smi
```

### starting sim

First we need to launch the docker container with the ROS Shadow Hand

```script
docker start dexterous_hand_simulated
```

Now we need to launch ROS and we use the the established roslauncher by shadow hand to

```ros
roslaunch sr_robot_launch sr_right_ur10arm_hand.launch
```


```
```
```
```


