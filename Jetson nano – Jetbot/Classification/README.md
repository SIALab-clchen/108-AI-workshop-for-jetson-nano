## 進入原始系統後之步驟
    $ sudo apt-get update 
    $ sudo apt-get upgrade
Jetson Nano -- [Two Days to a Demo](https://developer.nvidia.com/embedded/twodaystoademo)


#### 分類模型辨識北極熊_指令順序
    $ sudo apt-get install git cmake
    $ git clone https://github.com/dusty-nv/jetson-inference
    $ cd jetson-inference # change directory to jetson-inference
    $ git submodule update –init
    $ mkdir build && cd build
    $ cmake ../
    $ make
    $ sudo make install
    $ cd ~/jetson-inference/build/aarch64/bin
    $ ./imagenet-console polar_bear.jpg polar_bear_inferenced.jpg
![poloarbear](https://user-images.githubusercontent.com/57941572/69469768-a1aabf00-0dcd-11ea-81ad-708c7e77923c.png)
