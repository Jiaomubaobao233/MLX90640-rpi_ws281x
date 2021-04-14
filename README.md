# MLX90640-rpi_ws281x

19年12月做的课程设计。效果有限，未解决多接口驱动灯带因此显示效果经常有bug。以下是不成熟的技术总结。

![](https://github.com/Jiaomubaobao233/MLX90640-rpi_ws281x/blob/main/cover.jpg)

### 单片机

树莓派4B(4GB RAM)，vs code for 树莓派

### 传感器

热成像（thermal camera）：MLX90640传感器（微雪4pin，110°x75° 广角款）

（本来是考虑哈尔滨冬天很冷故采用热成像探头，但现在清华建馆室内勉强可用，成像时对比度在4-5摄氏度左右），在室外效果不错，但距离远（3m以上）了就不行。且i2c线不能过长，会无法使用，固直接用单片机驱动效果并不好。

code from a_kore on github，需要opencv库：[https://github.com/a-kore/mlx90640-python](https://github.com/a-kore/mlx90640-python?fileGuid=cJkwkrKqgCJtXjGG)

(需要python3)

接口库smbus2：[https://pypi.org/project/smbus2/](https://pypi.org/project/smbus2/?fileGuid=cJkwkrKqgCJtXjGG)可直接pip

### 灯光（可编程LED灯带）之ws2812b，5050

ws2812b：适合DIY使用，压强较低：[https://item.taobao.com/item.htm?spm=a1z09.8149145.0.0.2ee530a7zQH4Q6&id=522197656009&_u=628mbbso76fa](https://item.taobao.com/item.htm?spm=a1z09.8149145.0.0.2ee530a7zQH4Q6&id=522197656009&_u=628mbbso76fa&fileGuid=cJkwkrKqgCJtXjGG)

功率计算：5V * 60mA/珠 * 30珠/m * 1m = 9W（1m，30珠）

5050：适合实际工程使用，24V可20m不加压，一般用60珠/m

灯带宽度与压强无关，一般最小为8-10mm

可用DC供电（安全）或单独变压器供电（便宜）

树莓派教程：[https://tutorials-raspberrypi.com/connect-control-raspberry-pi-ws2812-rgb-led-strips/](https://tutorials-raspberrypi.com/connect-control-raspberry-pi-ws2812-rgb-led-strips/?fileGuid=cJkwkrKqgCJtXjGG)

用到neopixel（[https://pypi.org/project/adafruit-circuitpython-neopixel/](https://pypi.org/project/adafruit-circuitpython-neopixel/?fileGuid=cJkwkrKqgCJtXjGG)）但pip失败，就用本地的库

用到的资源：[https://github.com/jgarff/rpi_ws281x](https://github.com/jgarff/rpi_ws281x?fileGuid=cJkwkrKqgCJtXjGG)

_rpi_ws281x.so是python2版本，python3读不了，需要

```
sudo pip install rpi_ws281x
```
（[https://github.com/rpi-ws281x/rpi-ws281x-python](https://github.com/rpi-ws281x/rpi-ws281x-python?fileGuid=cJkwkrKqgCJtXjGG)）
### 传感器控制灯光具体代码实现

多线程处理，见廖雪峰的教程（比菜鸟教程好）：

[https://www.liaoxuefeng.com/wiki/1016959663602400/1017629247922688](https://www.liaoxuefeng.com/wiki/1016959663602400/1017629247922688?fileGuid=cJkwkrKqgCJtXjGG)

### 灯带的外壳

a-独立外壳后再与杆件绑扎，会比较突兀，需要想一个好办法

b-与杆件共同配外壳，外壳很粗，强度较低，但视觉效果好

### 灯光（光纤）

布光类型两种：尾端和均布

弯直两种：弯的按卷买便宜一些，直的按米卖很贵

### 冷光线

类似均布光纤，相对暗一些，长一些，细一些。黑暗中效果很好

完成几件事比较现实，每个人做设计或者完成技术专题


