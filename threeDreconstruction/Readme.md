##### SfM 3d Reconstruction

编译opencv，附加扩展模块

gitee下载opencv 及 opencv_contribs，修改.git/config远程网址为github，运行

```
git pull
cd opencv
mkdir install
cmake -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=../install -DWITH_LIBV4L=ON -DWITH_CUDA=OFF -DWITH_TBB=ON -DWITH_OPENMP=ON -DWITH_OPENGL=ON -DOPENCV_EXTRA_MODULES_PATH=/home/wz/github/opencv_contrib/modules -DOPENCV_ENABLE_NONFREE=ON ..
make -j16
make install
```

修改CMakeLists.txt opencv_dir

build

```
mkdir build
cd build
cmake ..
make
./reconstruct
```