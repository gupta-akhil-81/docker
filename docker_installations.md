# On Mac
We can run Linux containers on Mac which will run on top of a thin hyvervisor from Docker caller HyperKit.

# On Linux
* uninstall docker
> sudo apt-get remove docker docker-engine docker-ce docker.io
* update packages
> sudo apt-get update 
* add docker repo to apt-get
> sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
> sudo apt-get update
* install docker
> sudo apt-get install docker-ce
* verify docker installation
> docker version

# On Windows
Download and install Docker Desktop or Docker for Windows.
It will also deploy Linux Kernel and Hyperversion.


# On AWS
* Launch a new VM instance.
* Select image as CentOS 
* Select a general purppose micro instance
* Start the instance and connect to it using SSH.
* deploy the community edition Docker CE for CentOS.

