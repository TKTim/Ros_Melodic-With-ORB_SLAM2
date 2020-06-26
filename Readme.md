#### 版本：Ubuntu 18
#### Ros版本：Ros_Melodic
#### 安裝套件：ORB_SLAM2  

#### 1. 下載Ros_Melodic  [官網教學](http://wiki.ros.org/Installation/Ubuntu) 記得要照著步驟做前，要確認是否為Melodic的教學。
#### 2. 下載Pangolin
```
    # Install dependencies
    sudo apt-get install libglew-dev -y
    sudo apt-get install cmake -y
    # Build Pangolin from source and install it
    curr_dir=`pwd`
    cd /tmp
    git clone https://github.com/gaunthan/Pangolin
    cd Pangolin
    mkdir build
    cd build
    cmake ..
    make
    sudo make install
    cd "$curr_dir"
```
#### 3. 下載 OpenCV 
> 請參閱 我的網站 [下載OpenCV](https://github.com/TKTim/NVidia-2080Ti-Cuda10.2-Cudnn8.0-Yolo-GPU-#%E4%B8%8B%E8%BC%89Opencv)

#### 4. 下載 Eigen3 強烈建議下載3.3.4版本
```
    curr_dir=`pwd`
    cd /tmp
    wget http://bitbucket.org/eigen/eigen/get/3.3.4.tar.gz
    tar xzvf 3.3.4.tar.gz
    cd eigen-eigen-*
    mkdir build
    cd build
    cmake ..
    sudo make install
    cd "$curr_dir"
```
#### 5. 下載 ORB-SLAM2
```
    mkdir -p ~/workspace
    cd ~/workspace
    git clone https://github.com/gaunthan/ORB_SLAM2
    cd ORB_SLAM2
    chmod +x build.sh build_ros.sh
    ./build.sh
    echo 'export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:'"`pwd`/Examples/ROS" >> ~/.bashrc
    ./build_ros.sh
```

以上部份教學來自：[參考網站](http://blog.leanote.com/post/gaunthan/Ubuntu-18.04-%E5%AE%89%E8%A3%85ROS-Melodic%EF%BC%8CORB-SLAM2)

