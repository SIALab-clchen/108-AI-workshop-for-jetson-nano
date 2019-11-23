## 採用Intel RealSense VF0800  不用改camera 子目錄
## 請輸入以下的指令將視訊的裝置指定為 /dev/video0， 也就是一般預設的USB Camera的裝置位置。
## 網路攝影機 C200
 
 $ sed -i 's/DEFAULT_CAMERA\s* -1/DEFAULT_CAMERA 0/' ~/jetson-inference/detectnet-camera/detectnet-camera.cpp
 
 $ cd ~/jetson-inference/build
 $ make detectnet-camera
 
 $ cd ~/jetson-inference/build/aarch64/bin
 $ ./detectnet-camera facenet
