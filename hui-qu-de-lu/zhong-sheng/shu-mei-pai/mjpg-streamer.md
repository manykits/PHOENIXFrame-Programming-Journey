# 视频mjpg-streamer

## 启用摄像头功能

* 配置

sudo raspi-config

移动到第五项“Enable Camera”，回车进入，按tab键切换到“Enable”回车确认。回到主菜单，tab键切换到“Finish”回车确认。树莓派会自动重启。

* 安装依赖库

安装libjpeg的dev版本注：下面所有安装过程中出现是否继续时，统一选择继续：Yes

sudo apt-get install libjpeg62-dev

sudo apt-get install libjpeg8-dev

* 下载mjpg-streamer

wget[https://github.com/jacksonliam/mjpg-streamer](https://github.com/jacksonliam/mjpg-streamer)

或者直接到网站下载zip安装包mjpg-streamer-master.zip

使用unzip mjpg-streamer-master.zip解压

* 安装cmake

sudo apt-get install cmake

切换到mjpg的路径下：

cd  ~/mjpg-streamer-master/mjpg-streamer-experimental

sudo make clean all

* 安装mjpg-streamer

sudo make install

* 开启mjpg-streamer

sh ./start.sh 

器[http://:8080](http://:8080) 打开监控界面

# 双摄像头

mjpg\_streamer -i "/usr/lib/input\_uvc.so -d /dev/video0 " -o "/usr/lib/output\_http.so -w ./www -p 8001"

mjpg\_streamer -i "/usr/lib/input\_uvc.so -d /dev/video1 " -o "/usr/lib/output\_http.so -w ./www -p 8002"



