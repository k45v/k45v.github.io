---
layout: post
title: GPGPU simulator installation on Ubuntu 12.04 for a system without NVIDIA Graphics card
date: 2013-04-25
categories: [Parallel Computing]
---
Computation intensive applications which have high degree of data-level parallelism can very well harness the hardware capabilities provided a GPU. Enter the term [GPGPU](http://en.wikipedia.org/wiki/GPGPU).

You might want to try out the Parallel Computing platform [CUDA](http://www.nvidia.com/object/cuda_home_new.html) to gauge what kind of speed-up you can achieve in you current code by running it on a GPU. I wanted to use CUDA for one of my class projects but I do not have a compatible graphics card. Mine is an Intel Mobile 4 Series Chipset Integrated Graphics Controller, you can check yours using the command:
```shell
lspci | grep VGA
```
I spent a lot of time trying to install a GPU emulator but either I got stuck in some library dependency, or some of the downloaded packages were dependent on older gcc versions. The documentation online for installing emulators in systems which do not have a graphics card was insufficient. Finally, using few magical keywords in my Google search I located this [blog entry](http://barefeg.wordpress.com/2012/06/16/how-to-install-gpuocelot-in-ubuntu-12-04/) which provided detailed installation procedure for the [gpuocelot](http://code.google.com/p/gpuocelot/).

Here, I provide my version of the installation procedure to get a simple “Hello World” program up and running using GPGPU emulator.

1. Download the “CUDA Toolkit for Ubuntu Linux 10.10” from [here](https://developer.nvidia.com/cuda-toolkit-40) (v 4.0). Now start terminal (using ctrl + alt + t) and navigate to your Downloads directory. Change permissions for the installation file (mine was for 32bit) and install it. Hit enter if it asks for a change of destination directory.
```shell
chmod +x ./cudatoolkit_4.0.17_linux_32_ubuntu10.10.run
sudo ./cudatoolkit_4.0.17_linux_32_ubuntu10.10.run
```

1. Next install gcc and g++ v4.4 and update alternatives and priorities for gcc versions
```shell
sudo apt-get install gcc-4.4
sudo apt-get install g++-4.4
sudo update-alternatives \
--install /usr/bin/gcc gcc /usr/bin/gcc-4.6 40 \
--slave /usr/bin/g++ g++ /usr/bin/g++-4.6
sudo update-alternatives \
--install /usr/bin/gcc gcc /usr/bin/gcc-4.4 60 \
--slave /usr/bin/g++ g++ /usr/bin/g++-4.4
sudo update-alternatives --config gcc
```
Now select the version 4.4 (usually item 0). Check the current version using
```shell
gcc --version
```

1. Now you need to update the paths in your bashrc file
```shell
vi ~/.bashrc
```
In vi editor enter “G” to go to the end of file, then “i” to add data. Copy paste the lines below
```shell
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib:/usr/local/lib
export CPLUS_INCLUDE_PATH=/usr/local/cuda/include
```
Now enter “:wq” to save and exit. Update the sources using
```shell
source ~/.bashrc
```
The CUDA setup is completed now and you can check using the command
```shell
nvcc --version
```

1. Next download the following files:  
libboost-filesystem1.42.0_1.42.0-4ubuntu2_i386.deb from [here](https://launchpad.net/ubuntu/oneiric/+package/libboost-filesystem1.42.0)  
libboost-system1.42.0_1.42.0-4ubuntu2_i386.deb from [here](https://launchpad.net/ubuntu/precise/+package/libboost-system1.42.0) and  
libboost-thread1.42.0_1.42.0-4ubuntu2_i386.deb from [here](https://launchpad.net/ubuntu/oneiric/+package/libboost-thread1.42.0).  
I selected libboost-* in i386 (Release) and then downloaded the *.deb file below the Downloadable files section. Install by double clicking (it should open in the ubuntu software center, select install there).

1. Finally, download gpuocelot from [here](http://code.google.com/p/gpuocelot/downloads/list). I chose ocelot_2.1.1272_i386.deb. Install by double clicking.

## Hello World
1. Navigate to your home directory and create a folder hellocuda. Download the configuration file from [here](https://docs.google.com/file/d/0B5Ve5IFK3KWxeHdsQzM2MGdtOW8/edit) and the Hello World program from [here](https://docs.google.com/file/d/0B5Ve5IFK3KWxY0dWMXZ6b0hoZWc/edit). Place both these files in the hellocuda directory. You may go through [this page](http://code.google.com/p/gpuocelot/wiki/OcelotConfigFile) to understand the configuration file.

1. Now compile the code
```shell
nvcc -c hello.cu -arch=sm_20
g++ -o hello.out hello.o `OcelotConfig -l`
```
Next run it using
```shell
./hello.out
```
This code computes the dot product of two vectors a and b using the GPU (in our case on the CPU using emulation) and stores the result in c. The final output shows the result of the computation performed using GPU and CPU respectively.
