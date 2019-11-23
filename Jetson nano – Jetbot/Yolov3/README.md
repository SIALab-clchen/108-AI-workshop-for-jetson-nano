## 安裝CUDA，OpenCV，cuDNN
## Download
    $ git clone https://github.com/pjreddie/darknet.git
## 配置
    $ cd darknet
    $ sudo vim Makefile   #修改Makefile
## 將Makefile的前三行修改一下
    ~ GPU=1
    ~ CUDNN=1
    ~ OPENCV=1
    press esc and :wq to save Makefile
## 編譯
    $ make -j4
## 下載權重檔，這裡直接下載tiny版的權重檔
    $ wget https://pjreddie.com/media/files/yolov3-tiny.weights
## 測試
    $ ./darknet detect cfg/yolov3-tiny.cfg yolov3-tiny.weights data/dog.jpg
![dog](https://user-images.githubusercontent.com/57941572/69470161-d750a780-0dcf-11ea-8c33-7960be01880c.jpg)
