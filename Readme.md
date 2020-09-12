#### 版本：Ubuntu 18
#### Ros版本：Ros_Melodic
#### 安裝套件：ORB_SLAM2  

#### 0. [相機校正課程](https://blog.csdn.net/heroacool/article/details/51023921)


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

#### 6. 測試階段

[Follow here](https://github.com/raulmur/ORB_SLAM2#6-rgb-d-example)
1. 下載fr1/xyz 的 tgz
2. 下載associate.py 並用來生成自己的 associations.txt 
```
python associate.py PATH_TO_SEQUENCE/rgb.txt PATH_TO_SEQUENCE/depth.txt > associations.txt
```
3. 在/ORB-slam內運行 
```
./Examples/RGB-D/rgbd_tum Vocabulary/ORBvoc.txt Examples/RGB-D/TUM1.yaml /home/user/Downloads/rgbd_dataset_freiburg1_xyz/ /home/user/Downloads/rgbd_dataset_freiburg1_xyz/associations.txt
```

[ORB-test](https://www.youtube.com/watch?v=-EJFDlO215o)


#### 7. Webcam 
```
解壓 /root/catkin_ws/src/ORB_SLAM2/Vocabulary
tar zxvf ORBvoc.txt.tar.gz 
```
到catkin_ws/src/ORB_SLAM2/Examples/ROS/ORB_SLAM2 的CmakeLists.txt
將find_package後改成自己的版本
![image](https://github.com/TKTim/Ros_Melodic-With-ORB_SLAM2/blob/master/Screenshot%20from%202020-09-12%2012-57-27.png)


第一步
```
roscore
```

第二步
```
roslaunch usb_cam usb_cam-test.launch
```
第三步
```
確保以下檔案存在
rosrun ORB_SLAM2 Mono /root/catkin_ws/src/ORB_SLAM2/Vocabulary/ORBvoc.txt /root/catkin_ws/src/ORB_SLAM2/Examples/ROS/ORB_SLAM2/Asus.yaml
```
實作影片 [影片](https://www.youtube.com/watch?v=oc9EedC1OCY)
---

額外網站資源：
[g20解說](https://www.cnblogs.com/gaoxiang12/p/5304272.html)
[Webcam with ORB-SLAM2](https://zhuanlan.zhihu.com/p/29629824)

以上部份教學來自：[參考網站](http://blog.leanote.com/post/gaunthan/Ubuntu-18.04-%E5%AE%89%E8%A3%85ROS-Melodic%EF%BC%8CORB-SLAM2)

