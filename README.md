# Welcome to Podman-DuinoCoin 
This is guideline to run **DuinoCoin** inside a container by podman

**DuinoCoins** is belongs to [DuinoCoins Team](https://duinocoin.com/team).
Check their works in this [DuinoCoins-GitHub](https://github.com/revoxhere/duino-coin) link.


# Getting started
## LINUX Host
LINUX installation (any distro) is required to host container.
Install podman and its dependencies.

Please check this [official documentation](https://podman.io/getting-started/installation) about podman installation.

### Debian, Ubuntu and similar distros

    source /etc/os-release
    apt-get install curl wget gnupg2 -y
    sh -c "echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/ /' > /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list"
    wget -nv https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable/xUbuntu_${VERSION_ID}/Release.key -O- | apt-key add -
    apt-get update -qq -y
    apt-get -qq --yes install podman
    

### RedHat, Fedora, OracleLinux and similar distros

    yum install podman

## Container setup
In Linux terminal, download and run **alpine Linux** from docker library:
	
	podman pull docker.io/library/alpine
	podman run --name node-1 -h node-1 -dt  docker.io/library/debian 

it will create a container with name **node-1** and hostname **node-1**.
|       |note                      |
|-------|--------------------------|
|--name |container's name|
|-h |hostname|
|-d |detach terminal from container|
|-t |assign tty|

execute **ps** to print running container/s.
    podman ps

## Switch to container and install required software
Time to enter to container and continue setup.

    podman attach node-1

In container's shell:

    apk update
    apk add python3 git

Download and install DuinoCoin requirements:

    mkdir /duino-coin
    git clone https://github.com/revoxhere/duino-coin.git
    cd duino-coin/
    wget https://bootstrap.pypa.io/get-pip.py
    python3 get-pip.py 
    pip install requests

Run DuinoCoin for the first time:

    python3 PC_Miner.py 

**Answer the questions following the guideline from [DuinoCoin Getting Started PC](https://duinocoin.com/getting-started#computer)**

# Container management
## Getting help podman
    podman help
    podman <command> --help

## Start a container
From Linux host:

    podman start node-1

## Enter a container
From Linux host:

    podman attach node-1

## Exit/Detach from container
From inside a container:
    **ctrl+p** and **ctrl+q**

## Stop a container
From Linux host:

    podman stop node-1

## Destroy/Remove a container
From Linux host:

    podman rm node-1


___
GoodLuck
**//Denny**

