# Robotics Lab 2026 - Classwork 0: Docker Environment Setup

### Prerequisites
To download and set up the Docker scripts, follow these three steps:

1) Clone the repository:
```sh
git clone https://github.com/RoboticsLab2026/ros2_docker_scripts.git
```

2) Navigate into the repository folder and make the script files executable:
```sh
cd ros2_docker_scripts
chmod +x *.sh
```

3) Create the Docker image:
```sh
./docker_build_image.sh <IMAGE_NAME>
```
*Replace `<IMAGE_NAME>` with the name you want to assign to your Docker image.*


### Testing the Installation
After running the container, you can verify that the environment is working correctly by checking the ROS 2 distribution:

```sh
echo $ROS_DISTRO
```
If the output is `humble`, the image has been built successfully.

To further verify the installation, you can list the available ROS 2 packages:
```sh
ros2 pkg list
```

### Running the Container
Once the build is successful, you can run the container. Depending on your current folder structure, execute the script from the main directory:

```sh
./docker_scripts/docker_run_container.sh
```
Or, if you are already inside the folder containing the script:
```sh
./docker_run_container.sh
```

The script will prompt you for three inputs:
1. **Image Name**: Select the Docker image you created during the build process.
2. **Container Name**: Choose any name you prefer for your new container.
3. **Shared Folder Path**: Specify the local directory that will be mounted to the container. Any modifications made here will sync in real-time. 
   * *Recommended path:* `Desktop/<surname>_rl26/src` (the folder created in Step 1).


### Testing the Container Volume (Shared Folder)
Once you have answered all three prompts, the container will launch with a direct link to your local folder. To verify that the shared volume is working correctly, run:

```sh
touch prove.txt
```

This will create a file inside the container. Check your local folder on your computer: you should see `prove.txt` appear there. Any changes you make to this file (locally or inside the container) will update instantly in both environments.
