# Openmpi containers

### What
Openmpi containers for running distributed computing programs (for lab) in local pc

### For who?
(Mostly) [NITK](https://infotech.nitk.ac.in/) students who want to work on distributing computed lab without access to the actual cluster.

### Requirements:
- Linux PC
- [Docker](https://docs.docker.com/engine/install/)
- User in the `docker` group

### How
- Build the image
	
	  docker build . -t openmpi
	
- Start the cluster
	
	  docker-compose up --scale head=1 --scale node=<n>

- View the running containers 

	  docker container ls

- Login to head

	  docker container exec -it bash <name of head node>

- Current directory will be accesible in `/mnt`
	
	  ls /mnt

- Compile the example program

	  mpicc test.c -o test

- Execute it in current node
	
	  mpirun test

- Prepare a hosts list. From the output of `docker container ls`
	
	  echo <host name> >> host_list.txt

- Run your program on all hosts

	  mpirun --hostfile host_list.txt test
	 
- Cleanup
	
          docker-compose down
	

## Credits

This repository is forked from https://github.com/oweidner/docker.openmpi
