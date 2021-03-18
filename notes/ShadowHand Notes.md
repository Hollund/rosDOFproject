# get the ROS melodic image 

    bash <(curl -Ls bit.ly/run-aurora) docker_deploy product=hand_e sim_hand=true container_name=dexterous_hand_simulated  tag=melodic-release launch_hand=true reinstall=true nvidia_docker=true

# nvidia_docker ubuntu ROS

<https://nvidiasettlement.com/install-nvidia-docker>

curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - distribution=$(./ etc/os-release; echo $ID$ VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee/ etc/apt/sources. list.d/ nvidia-docker.list