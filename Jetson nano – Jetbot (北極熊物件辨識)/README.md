## 進入原始系統後之步驟
    $ sudo apt-get update 
    $ sudo apt-get upgrade
Jetson Nano -- [Two Days to a Demo](https://developer.nvidia.com/embedded/twodaystoademo)


## 分類模型辨識北極熊_指令順序
    $ sudo apt-get install git cmake
    $ git clone https://github.com/dusty-nv/jetson-inference
    $ cd jetson-inference # change directory to jetson-inference
    $ git submodule update –init
    $ mkdir build && cd build
    $ cmake ../
