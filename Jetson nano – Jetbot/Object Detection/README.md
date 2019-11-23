## 進入原始系統後之步驟
    $ sudo apt-get update 
    $ sudo apt-get upgrade
Jetson Nano -- [Two Days to a Demo](https://developer.nvidia.com/embedded/twodaystoademo)


#### 物件偵測_指令順序
    $ sudo apt-get install git cmake
    $ git clone https://github.com/dusty-nv/jetson-inference
    $ cd jetson-inference # change directory to jetson-inference
    $ git submodule update –init
    $ mkdir build && cd build
    $ cmake ../
    $ make
    $ sudo make install
    $ cd ~/jetson-inference/build/aarch64/bin
    $ ./detectnet-console peds-003.jpg output_3.jpg
![object](https://user-images.githubusercontent.com/57941572/69469983-b6d41d80-0dce-11ea-8728-b98950b040d4.jpg)
