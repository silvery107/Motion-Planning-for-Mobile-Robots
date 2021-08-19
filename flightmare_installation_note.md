# Flightmare Installation Note 

This note is for installing Flightmare in Ubuntu 18.04 with ROS Melodic.

## Filghtmare Installation

*Note: Using Python 2.7 for compiling flightmare*

Follow the official installation guideline to install Flightmare for both ROS and python version.

> https://github.com/uzh-rpg/flightmare/wiki

- flightlib

    `pip install -e src/flightmare/flightlib/.`

    Add the `-e` option instead of pure install.

## Extral Packages Installation:

- CMake 3.21.1
    
    `pip install cmake`

    The version of CMake will be outdated if using `sudo apt install cmake`.

- OpenCV

    >https://docs.opencv.org/4.5.1/d7/d9f/tutorial_linux_install.html

- Open3D

    > http://www.open3d.org/docs/release/compilation.html
    > https://github.com/isl-org/open3d-cmake-find-package
    
    Compile and install Open3D

    ```bash
    git clone --recursive https://github.com/intel-isl/Open3D.git
    cd Open3D
    mkdir build
    cd build
    cmake -DBUILD_SHARED_LIBS=ON -DCMAKE_INSTALL_PREFIX=${HOME}/open3d_install ..
    cmake --build . --config Release --parallel 12 --target install
    cd ../..
    ```

- OMPL
    > https://ompl.kavrakilab.org/core/installation.html

    `apt-get install libompl-dev ompl-demos`

    This will install both ompl for C++ and ROS, but not including python bindings.

- OpenCL
    > http://joey771.cn/2019/01/18/ubuntu%E5%AE%89%E8%A3%85OpenCL%E8%BF%90%E8%A1%8C%E5%8F%8A%E7%BC%96%E8%AF%91%E7%8E%AF%E5%A2%83/
    > https://www.jianshu.com/p/c1133c01ce4e?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation

    ```bash
    sudo apt install clinfo
    sudo apt install ocl-icd-libopencl1
    sudo apt install opencl-headers
    ```

## Issues & Errors

- Could not load the Qt platform plugin "xcb"
    > https://github.com/wkentaro/labelme/issues/842

    Just remove the damn `/usr/lib/python3.7/site-packages/cv2/qt/plugins` then everything is fine....

- DRM_IOCTL_I915_GEM_APERTURE failed
    ```
    sudo apt-get remove beignet
    sudo apt purge beignet
    ```

- beignet-opencl-icd: no supported GPU found
    ```
    sudo apt-get remove beignet-opencl-icd
    sudo apt purge beignet-opencl-icd
    ```
