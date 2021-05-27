## Configuration on Ubuntu

### Compiler: 
1. Intel for Gemini
    * ipcp & mpiicpc:
    * oneAPI 2021.2.0: ```l_HPCKit_p_2021.2.0.2997.sh```
    * after installation, set the environment: ```source /opt/intel/oneapi/setvars.sh```
    * it works for Gemini, but not for PowerGraph nor PowerLyra
    * when running Gemini, set the gcc&g++ to 9/10

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