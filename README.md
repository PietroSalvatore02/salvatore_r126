# Robotics Lab 2026 - Classwork 0
**Author:** Pietro Salvatore
**Repository:** salvatore_r126

This repository contains the setup for the Docker environment required for Classwork 0 of the Robotics Lab 2026 course.

## Prerequisites
To run this project, you need a machine starting from a clean state with the following installed:
* A Linux environment (Native Ubuntu 22.04, WSL2, or a Virtual Machine).
* Git for version control.
* Docker installed and configured.

## How to Build and Run the Container

### 1. Make the scripts executable
Before running the scripts, grant them execution permissions:
`chmod +x docker_scripts/*.sh`

### 2. Build the Docker Image
To build the Docker image, run the build script:
`./docker_scripts/docker_build_image.sh rl26_image`

### 3. Run the Container
Start the container using the provided run script:
`./docker_scripts/docker_run_container.sh`
Select the image, set a container name, and provide the path `salvatore_rl26/src` when prompted for the folder to mount.

## How to Verify Task 2 Completion (Volume Persistence)
Once inside the running container, you can verify the ROS 2 setup:
* `echo $ROS_DISTRO` (Expected output: humble)
* `ros2 pkg list` (Verifies the package list)

**Testing Volume Persistence:**
1. Inside the container, create a test file in the mounted workspace:
   `touch /home/user/ros2_ws/src/test_persistence.txt`
2. Exit the container by typing `exit`.
3. Stop and remove the container from the host machine:
   `docker container prune -f`
4. Verify the file exists on the host machine in your `src/` folder:
   `ls src/`
If `test_persistence.txt` is listed, the host-container volume persistence works correctly.
