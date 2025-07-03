# Guide for building & running the development container

This guideline explains how to build the development container (which is based on Orbit) and run the RL environments for training & testing.

1) Install the *suggested* GPU drivers for Isaac Sim from the Nvidia website, docker, and nvidia-container-toolkit if not installed already.
2) Install IsaacSim and IsaacSim WebRTC app.
3) Create a document in which you will put all the development related files/repos for the container. Let's say this folder is called documents_oo for this guide. Also, at the same hierarchy of this folder, add the "usd" folder here, which is supposed to contain all the relevant custom usd files, and an empty folder called "logs".
4) Go inside documents_oo. Clone the following repos to this folder: eurostars-lambda/[IsaacLab, lambda-gym, lambda-robots]. You can also pull eurostars-lambda/lambda-cv, but it is not necessary at this point as it runs independently. 
    - If you are planning to do development in these repos, it makes sense to create your branches at this point (e.g., lambda-aica and lambda-circuli-ion) according [this guideline](CROSS_INSTITUTIONAL_REPO_BRANCH_SYNC_GUIDE.md).
5) Check the [Isaaclab docker container deployment guidelines] (https://isaac-orbit.github.io/orbit/source/deployment/docker.html) to learn how to use `container.sh`. We will use the same but using "sbtc" profile. 
6) Adapt the file paths within `docker-compose.yaml` inside the `IsaacLab/docker/` directory for lambda: basically change the sbtc-gym to lambda-gym and sbtc-robots to lambda-robots. Make sure to map other relevant folders correctly, such as usd and logs.
7) Run `python3 container start sbtc` inside the `IsaacLab/docker/` directory to build and start our docker container. The resulting container should be "isaaclab-sbtc".
8) Enter the container with `python3 container enter sbtc` command. Run `runisaac.sh` bash script (under `/workspace/IsaaLab/` of the container) to start the isaac-sim in WebRTC mode. The first time could take a while as it needs to cache files. Once you see the  "Isaac Sim Headless WebRTC App is loaded." message, it means Isaac Sim started, and you need to go to IsaacSim WebRTC app (install it from website),  use `localhost` for IP address if on the same pc, use a supported browser!. 
9) Understand the folder structure and the source files a bit.
10) Use launch file entries or tmux bash script to train.
11) The END :)
