### NVIDIA Jetson Nano 安裝手冊_clchen
### NVIDIA Jetson Nano 實際使用難不難？從入手到安裝系統、開機與遠端連線
  $ https://blog.cavedu.com/2019/04/03/jetson-nano-installsystem/
### 格式化SD卡 SD Memory Card formatter
  $ https://www.sdcard.org/cht/downloads/formatter/eula_windows/index.html
### 安裝Image 檔進SD卡
### Etcher – A Modern USB and SD Card Image Writer Tool for Linux
  $ https://www.fossmint.com/etcher-usb-sd-card-bootable-image-creator-for-linux/
### 下載
  $ https://developer.nvidia.com/embedded/dlc/jetson-nano-dev-kit-sd-card-image
### 進入原始系統後之步驟
  $ sudo apt-get update
  $ sudo apt-get upgrade
### 1)  檢查CUDA
### Jetson-nano中已經安裝了CUDA10.0版本，但是此時你如果運行 nvcc -V是不會成功的，需要你把CUDA的路徑寫入環境變數中。OS中自帶Vim工具 ，所以運行下面的命令編輯環境變量
 
  $ sudo vim  ~/.bashrc
### 在最後添加
   ~ export CUBA_HOME=/usr/local/cuda-10.0
   ~ export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64:$LD_LIBRARY_PATH
   ~ export PATH=/usr/local/cuda-10.0/bin:$PATH
 
### 然後保存退出
### 對了最後別忘了source一下這個檔。
  $ source ~/.bashrc
### source後，此時對此再執行nvcc -V執行結果如下
  $ nvcc -V
### nvcc: NVIDIA (R) Cuda compiler driver
### Copyright (c) 2005-2018 NVIDIA Corporation
### Built on Sun_Sep_30_21:09:22_CDT_2018
### Cuda compilation tools, release 10.0, V10.0.166
 
 
### （2）檢查OpenCV
 
### Jetson-nano中已經安裝了OpenCV3.3版本，可以使用命令檢查OpenCV是否安裝就緒
  $ pkg-config opencv --modversion
### 如果OpenCv安裝就緒，會顯示版本號，我的版本是3.3.1
### （3）檢查cuDNN
### Jetson-nano中已經安裝好了cuDNN，並有例子可供運行，我們運行一下例子，也正好驗證上面的CUDA
  $ cd /usr/src/cudnn_samples_v7/mnistCUDNN   #進入例子目錄
  $ sudo make     #編譯一下例子
  $ sudo chmod a+x mnistCUDNN # 為可執行檔添加執行許可權
  $ ./mnistCUDNN # 執行
 ### 如果成功，如下所示
### beckhans@Jetson:/usr/src/cudnn_samples_v7/mnistCUDNN$ ./mnistCUDNN
### cudnnGetVersion() : 7301 , CUDNN_VERSION from cudnn.h : 7301 (7.3.1)
### Host compiler version : GCC 7.3.0
### There are 1 CUDA capable devices on your machine :
### device 0 : sms  1  Capabilities 5.3, SmClock 921.6 Mhz, MemSize (Mb) 3964, MemClock 12.8 Mhz, Ecc=0, boardGroupID=0
### Using device 0
 
### Testing single precision
### Loading image data/one_28x28.pgm
### Performing forward propagation ...
### Testing cudnnGetConvolutionForwardAlgorithm ...
### Fastest algorithm is Algo 1
### Testing cudnnFindConvolutionForwardAlgorithm ...
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.325104 time requiring 3464 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.387500 time requiring 0 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.540729 time requiring 57600 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 4.965156 time requiring 207360 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 7: 5.201146 time requiring 2057744 memory
### Resulting weights from Softmax:
### 0.0000000 0.9999399 0.0000000 0.0000000 0.0000561 0.0000000 0.0000012 0.0000017 0.0000010 0.0000000 
### Loading image data/three_28x28.pgm
### Performing forward propagation ...
### Resulting weights from Softmax:
### 0.0000000 0.0000000 0.0000000 0.9999288 0.0000000 0.0000711 0.0000000 0.0000000 0.0000000 0.0000000 
### Loading image data/five_28x28.pgm
### Performing forward propagation ...
### Resulting weights from Softmax:
### 0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 0.9999820 0.0000154 0.0000000 0.0000012 0.0000006 
 
### Result of classification: 1 3 5
 
### Test passed!
 
### esting half precision (math in single precision)
### Loading image data/one_28x28.pgm
### Performing forward propagation ...
### Testing cudnnGetConvolutionForwardAlgorithm ...
### Fastest algorithm is Algo 1
### Testing cudnnFindConvolutionForwardAlgorithm ...
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.113750 time requiring 0 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.119792 time requiring 3464 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.236198 time requiring 28800 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 1.031719 time requiring 207360 memory
### ^^^^ CUDNN_STATUS_SUCCESS for Algo 5: 5.049948 time requiring 203008 memory
### Resulting weights from Softmax:
### 0.0000001 1.0000000 0.0000001 0.0000000 0.0000563 0.0000001 0.0000012 0.0000017 0.0000010 0.0000001 
### Loading image data/three_28x28.pgm
### Performing forward propagation ...
### Resulting weights from Softmax:
### 0.0000000 0.0000000 0.0000000 1.0000000 0.0000000 0.0000714 0.0000000 0.0000000 0.0000000 0.0000000 
### Loading image data/five_28x28.pgm
### Performing forward propagation ...
### Resulting weights from Softmax:
### 0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 1.0000000 0.0000154 0.0000000 0.0000012 0.0000006 
 
### Result of classification: 1 3 5
 
### Test passed!
 
### 1. 安裝pip
### 因為Jetson Nano中已經安裝了Python3.6版本，所以安裝pip還是比較簡單的
 $ sudo apt-get install python3-pip python3-dev
### 安裝後pip是9.01版本，需要把它升級到最新版，升級後pip版本為19.0.3。這裡面升級後會有一個小Bug，需要手動改一下
 
$ python3 -m pip install --upgrade pip  #升級pip
$ sudo vim /usr/bin/pip3   #打開pip3文件
### 將原來的
~ from pip import main
~ if __name__ == '__main__':
~ sys.exit(main())
### 改成
 
~ from pip import __main__
~ if __name__ == '__main__':
~ sys.exit(__main__._main())
### 修改結束後保存。運行pip3 -V成功後顯示
 
$ beckhans@Jetson:~$ pip3 -V
$ pip 19.0.3 from /home/beckhans/.local/lib/python3.6/site-packages/pip (python 3.6)
###2. 安裝那些機器學習領域如雷貫耳的包
$ sudo apt-get install python3-scipy
$ sudo apt-get install python3-pandas
$ sudo apt-get install python3-sklearn
### 這裡面沒有numpy和matplotlib，不是說他倆不重要，而是安裝其它包時，這兩個也會被自動安裝。
 
### 3. 安裝TensorFlow GPU版
 ### （1）確認CUDA已經被正常安裝
$ nvcc -V
### 如果能看到CUDA版本號，即為正確安裝
 ### （2）安裝所需要的包
 $ sudo apt-get install python3-pip libhdf5-serial-dev hdf5-tools
### （3）安裝TensorFlow GPU版本 
 $ pip3 install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu==1.13.1+nv19.3 --user
### 經歷了漫長的等待，下載過程中好幾次斷網了幾次，不過終於安裝成功了，沒出什麼異常。
 
### 4. 安裝Keras
### 既然有了TensorFlow，那就把Keras也安裝上。我自己很喜歡keras，讓TensorFlow變得更加簡單
 
$ sudo pip3 install keras
### 安裝完成後，進入python3，檢查一下安裝成果，import keras時，下方提示using TensorFlow backend,就證明Keras安裝成功並使用TensorFlow作為backend。
 
### beckhans@Jetson:~$ python3
### Python 3.6.7 (default, Oct 22 2018, 11:32:17)
### [GCC 8.2.0] on linux
### Type "help", "copyright", "credits" or "license" for more information.
 $ >>> import keras
### Using TensorFlow backend.
### >>>
