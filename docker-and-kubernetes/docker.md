Before Get into the Topic Container, We need to know why container came to world, to compete with resource sharing in 
VM technology.

First to Know that clearly that, Computer has been divided by two things,
	1. Hardware 
		Hardware is a physical devices, like CPU, RAM, ROM, which all are called as 			
		underlying technology of an computer.
	2. Software
		Software is a program or application to perform particular task by controlling 			
		Hardwares. 
		Ex : Chrome.

Above both are the essential part of computer system.  As we already specified that, each software (program) used to
perform aspecific task. As of that, can you think that, can you run chrome application directly to an hardware. 
Not it is not possible. Because Chrome only able to process hypertext information it does not know how to communicate
with system resource like CPU, RAM and ROM. Here it will depends on other programs that has the huge knowledge how to deal with 
system resources, that program call as Operating system.

Operating Systems :
 
Operating system is system software that manages computer hardware and software resources and provides common services for computer programs.
Simply, low-level software that supports a computer's basic functions, such as scheduling tasks and controlling peripherals. 

if you are came from computer science person, then you will have a question at this point, then where kernel.

Kernel :
The kernel is the central module of an operating system (OS). It is the part of the operating system that loads first.
In operating system, the kernel is a computer program that manages input/output requests from software, and translates them into data processing 
instructions for the central processing unit and other electronic components of a computer

Simply,  the kernel is responsible for memory management, process and task management, and disk management. The kernel connects the system hardware
to the application software. Every operating system has a kernel. For example the Linux kernel(NOT OS) is used numerous operating systems including
Linux, FreeBSD, Android and others.
Kernel is a part of an operating system - the most crucial part. However, kernel alone will not make any OS work; there must be some softwares and other
related things working together with kernel, that is called OS.

So we know all the basic can we talk about container. No, Container is new born child of 21th century. So we have to first know about his father Hypervisor. 

Hypervisor :
What is a Hypervisor? 
A hypervisor (virtual machine monitor), is a process that creates and runs virtual machines (VMs). A hypervisor allows one host computer to support multiple 
guest VMs by virtually sharing its resources, like memory and processing. Generally, there are two types of hypervisors. 
Type 1 : Bare metal -  run directly on the host’s hardware. 
Virtualization software that has been installed directly onto the computing hardware.This type of hypervisor controls not only the hardware, 
but one or more guest operating systems (OSes)
Type 2 :  hosted - run as a software layer on an operating system, like other computer programs. 

Why use a Hypervisor?
Hypervisors make it possible to use more of a system’s available resources and provide greater IT mobility since the guest VMs are independent of the host hardware.

Host and Guest Machine ?
A computer on which a hypervisor runs one or more virtual machines is called a host machine, and each virtual machine is called a guest machine. 

What are VMs?
     A virtual machine (VM) is an emulation of a computer system on an one computer.
However VM, can take up a lot of system resources. Each VM runs not just a full copy of an operating system, but a virtual copy of all the hardware 
that the operating system needs to run. This quickly adds up to a lot of RAM and CPU cycles. That’s still economical compared to running separate actual computers,
 but for some applications it can be overkill, which led to the development of containers.
Here the problem came then container cames into running.
	Note : Due to this we can said, VM (hpervisor) is out of market. Each of this can have advandage and disadvandage.

Benefits of VMs:
All OS resources available to apps
Established management tools
Established security tools
Better known security controls

Popular VM Providers:
VMware vSphere
VirtualBox
Xen
Hyper-V
KVM
Now we can start our topic,
What are Containers?
With containers, instead of virtualizing the underlying computer like a virtual machine (VM), just the OS is virtualized.

Containers sit on top of a physical server and its host OS — typically Linux or Windows. Each container shares the host OS kernel and, usually, 
the binaries and libraries, too. Shared components are read-only. Sharing OS resources such as libraries significantly reduces the need to reproduce the 
operating system code, and means that a server can run multiple workloads with a single operating system installation. 
Containers are thus exceptionally light — they are only megabytes in size and take just seconds to start.

Types of Containers :
1. Linux Containers (LXC)
LXC is a Linux operating system level virtualization method for running multiple isolated Linux systems on a single host
2. Docker 
Docker started as a project to build single-application LXC containers, introducing several changes to LXC that make containers more portable and flexible to use. 
It later morphed into its own container runtime environment. At a high level, Docker is a Linux utility that can efficiently create, ship, and run containers.

Difference Between VM's and Containers :
VM'S :
1. Heavy weight
2. Limited performance
3. Each VM runs in its own OS
4. Hardware-level virtualization
5. Startup time inminutes
6. Allocates required memory
7. Fully isolated , hence more secure

Containers :
1. Light weight
2. Native performance
3. All containers share the host OS.
4. OS virtualization
5. Startup time in milliseconds
6. Requires less memory space
7. Process level, so less secure

Ok, Now we are ready to jump into the topic Docker world (containner based application). 
Lets Start................................

Docker :
WHY? 
Docker makes it really easy to install and run software without worrying about setup or dependencies.
What is Docker ?
Docker is a platform or ecosystem, around creating and running containners.
Docker terminology :
1. Docker Client (Basic inferface for user, to communicate with server)
2. Docker Server (Tool, that isresponsible for creating Images, running conainers, managing containners, etc..)
3. Docker Machine
4. Docker Image
5. Docker Hub
6.Docker Compose

Concept Of Docker:
1. Image
	Single file with all the dependency and config required to run a program.
2. Containner: (We already learned lot):
	Quick Note - Container is a program with its own isolated set of hardware resources, and Make use of it's Host OS.
In docker, Containner is a instance of Image, Runs a program.

Install Docker on you system.
You can confirm, Docker is installed or not by running below command,
 >> docker version

Docker Important Commands:
1. Creating and running a container from Image
	>> docker run <image_name>

Ex:
	docker run busybox
First docker look at current system cache with named busybox, if it not available in local then it will look at docker hub.
if image available there then first download that image locally and then start that image to create containners.
  
Overriding Defaul Commands: 
	docker run busybox echo hi there
	docker run busybox ls
	docker run busybox sh
	docker run busybox ping google.com
if user use any commands, then it should be available in that containner.
	>> docker run busybox ls
	because that ls commands does not known by that container.

Listing All running Containers:
	>> docker ps
All container cache in current system,
including stopped containner, running containner list.
	>> docker ps --all 

Container Life cycle :
	1. Create a container
		>> docker create <image_name>
	2. Start a container  
		>> docker start <container_id_from_create>
			Return id ofthe container
		>> docker start -a <image>
			To watch a output coming from container, and print out 
	docker run = docker create + docker start

Stop a Container :
	>> docker stop <container_id>
	It will generate SIGNAL TERM to primary process to stop a containner, then container will take some time 
	to clean up process. After all process container will be stoped. So it is immediate stop command. 
	If process does not stop with in some period of time (probably 10s), then it will be automatically kill by process.
	
Kill a Container :
	>> docker kill <container_id>
	It is a immediate process to stop a containner. It does not care about state / process / cleaing up. 
	It will generate KILL SIGNAL to primary process to immediately stop a containner.

Restaring Stopped Containner : 
	First get id of stopped containner.
	Once the container created then restaring container user can't do any changes on container, only thing is 
		last stopped container can start (like default container override) 

	>> docker start -a <container_id>

Remove stopped container (or) clearing docker cache :
	>> docker system prune

Retrieving log output from a container :
	>> docker logs <container_id>

Multi Command Containners & Executing Commands in Running Containers :
	To Executing an additional command in a container
	>> docker exec -it <container_id> <commands>
	-it flag -> interactive shell / input to containner (if -it is not included then user can't give input)
		1. STDIN
		2. STDOUT
		3. STDERR
		>> docker exec -i -t <container_id> <commands>
		>> docker exec -i <container_id> <commands>
			-i input STDIN 
			-t show up it result in Shell

Sample :
Open in First CMD/Shell
	>> docker run redis
	
Open another CMD/Shell Type below command:
	>> docker exec -it <containner_id> redis-cli

Open shell from container:
	>> docker run -i -t busybox sh
	>> docker exec -it <c-id> sh
=======================================================

Creating Custome Docker Image (Custome light OS):
	Process :
		Dockerfile >> Docker client >> Docker server >> Usable Image
		Base Docker Image >> Download additional dependency >> specify command to run on containner
Goal Docker Redis Image :
	>> mkdir docker-redis-image
	>> 
