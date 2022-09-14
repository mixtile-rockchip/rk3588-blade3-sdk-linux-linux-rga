## librga

RGA (Raster Graphic Acceleration Unit)是一个独立的2D硬件加速器，可用于加速点/线绘制，执行图像缩放、旋转、bitBlt、alpha混合等常见的2D图形操作。本仓库代码实现了RGA用户空间驱动，并提供了一系列2D图形操作API。

### 版本说明

**RGA API** 版本: 1.8.0

### 适用芯片平台

Rockchip RK3066 | RK3188 | RK2926 | RK2928 | RK3026 | RK3028 | RK3128 | Sofia3gr | RK3288 | RK3288w | RK3190 | RK1108 | RK3368 | RK3326 | RK3228 | RK3228H | RK3326 | RK1808 | RV1126 | RV1109 | RK3399 | RK3399pro | RK3566 | RK3568 | RK3588 | RK3326S | RV1106 | RV1103

### 目录说明

**core:** RGA用户空间驱动实现

**include:** 相关头文件

**im2d_api:** RGA API相关实现及头文件

**docs:** RGA API说明文档、RGA FAQ

**samples:** librga使用例程

**samples/sample_file：**示例图片

### 编译说明

* **Android Source Project**

下载librga仓库拷贝至android源码工程 hardware/rockchip目录，执行**mm**进行编译。根据不同的Android版本将自动选择Android.mk或Android.bp作为编译脚本。

* **Android NDK (build for android)**

修改toolchains/toolchain_android_ndk.cmake文件，修改为本地的NDK路径后，执行以下操作完成编译：

```bash
$ chmod +x ./cmake-android.sh
$ ./cmake-android.sh
```

​    **[编译配置]**

| 编译选项                            | 说明                                                        |
| ----------------------------------- | ----------------------------------------------------------- |
| CMAKE_ANDROID_NDK                   | 配置NDK开发包的绝对路径。                                   |
| CMAKE_SYSTEM_VERSION                | 配置Android平台版本，Android API-Level。                    |
| CMAKE_ANDROID_ARCH_ABI              | 配置选择架构，设置-DANDROID_ABI等于armeabi-v7a或arm64-v8a。 |
| CMAKE_ANDROID_NDK_TOOLCHAIN_VERSION | 配置使用的工具链为GCC/clang。                               |
| CMAKE_ANDROID_STL_TYPE              | 配置libc++_shared.so的链接模式。                            |

* **Cmake (buildroot/debian)**

修改toolchains/toolchain_linux.cmake文件，修改为本地的交叉编译工具路径后，执行以下脚本完成编译:

```bash
$ chmod +x ./cmake-android.sh
$ ./cmake-linux.sh
```

​    **[编译配置]**

| 编译选项       | 说明                         |
| -------------- | ---------------------------- |
| TOOLCHAIN_HOME | 配置交叉编译工具的绝对路径。 |
| TOOLCHAIN_NAME | 配置交叉编译工具名字前缀。   |

* **Meson(buildroot/debian)**

librga提供了meson.build，最新buildroot支持meson 编译。单独编译可以使用meson.sh 脚本进行config，需要自行修改meson.sh 内指定install 路径，以及PATH等环境变量，cross目录下是交叉编译工具配置文件，也需要自行修改为对应交叉编译工具路径。

执行以下操作完成编译:

```bash
$ ./meson.sh
$ ninja -C build-rga install
```

### 使用说明

* **头文件引用**

  * C++调用im2d api

    im2d_api/im2d.hpp

  * C调用im2d api

    im2d_api/im2d.h

* **库文件**

  librga.so

  librga.a

* librga应用开发接口说明参考以下文件：

  [IM2D API说明文档【中文】](docs/Rockchip_Developer_Guide_RGA_CN.md)

  [IM2D API说明文档【英文】](docs/Rockchip_Developer_Guide_RGA_EN.md)

* RGA模块FAQ文档：

  [RGA_FAQ【中文】](docs/Rockchip_FAQ_RGA_CN.md)

  [RGA_FAQ【英文】](docs/Rockchip_FAQ_RGA_EN.md)

