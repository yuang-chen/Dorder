## Configuration on Ubuntu

### Compiler: 
1. Intel for Gemini
    * ipcp & mpiicpc:
    * oneAPI 2021.2.0: ```l_HPCKit_p_2021.2.0.2997.sh```
    * after installation, set the environment: ```source /opt/intel/oneapi/setvars.sh```
    * it works for Gemini, but not for PowerGraph nor PowerLyra

2. GNU for PowerGraph and PowerLyra
    * g++ 4.4.7
    * download by firstly edit the ```/etc/apt/sources.list```: 
       - add: ```deb https://mirrors.ustc.edu.cn/ubuntu/  trusty  main universe```
    * in terminal: ```sudo apt update && sudo apt install g++4.4```
    * OpenMPI 4.0.3 (to test)
    * MPICH 3 (recommended, and to test)


### CMakeLists for PowerGraph & PowerLyra
    one must update the **CMakeLists** to fix the broken downloading links and LD_LIBRARY_PATH (this issue occurs in Ubuntu) 


## Configuration on CentOS
The Cluster with CentOS 7 raises a variety of issues 

### Cluster Setting: 
1. admin node: mu01 - the one we login using **ssh** (e.g., ```ssh yuang@10.26.1.30```)
2. computing node: gpu01~08 - the ones we can access via **rlogin**, **rsh**, and **rexec** from *mu01* (e.g., ```rlogin gpu01```)
3. storing node: mds01~02

Everything we install in /opt/soft/ are shared through the cluster.

### Compiler
1. Intel for Gemini
    * there exist an Intel ICC 18.0.1 that fails to compile Gemini, causing conflits!
    * install the oneAPI tool kit in *mu01* following the instrunction on Ubuntu
    * specify the installation path: ```source /opt/soft/oneapi/setvars.sh```

2. Update *libstdc++*
    * repeat following commands on every computing node, e.g., gpu01 ~ gpu08
    ```
    cp /opt/soft/libstdc++.so.6.0.26 /usr/lib64/ &&

    mv /usr/lib64/libstdc++.so.6 /usr/lib64/libstdc++.so.6.old &&

    ln -s /usr/lib64/libstdc++.so.6.0.26 /usr/lib64/libstdc++.so.6
    ```