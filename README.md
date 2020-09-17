# MyRaspberryNote
Raspberry Environment Build
------

目錄
------
* [Raspberry安裝](#Raspberry安裝)
* [Python3.7安裝](#Python3.7安裝)  
* [Tensorflow安裝](#Tensorflow安裝) 
* [librosa](#librosa) 
* [PyAudio](#PyAudio) 
* [Sox](#Sox) 
* [Keras](#Keras) 
* [Office](#Office) 
* [Git](#Git) 
* [Chinese_Input](#Chinese_Input) 
* [LCD3.5](#LCD3.5) 
* [OpenCV3.4](#OpenCV3.4)
* [PyTorch](#PyTorch)

Raspberry安裝
------
1. [Download Image](https://www.raspberrypi.org/downloads/raspberry-pi-os/)
2. Unzip
3. Write the disc image to your microSD card
4. Put the microSD card in your Pi and boot up

```
sudo apt update
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
sudo rpi-update
```

Python3.7安裝
------
> [python3.7](https://www.python.org/ftp/python/)
```
sudo apt install build-essential libsqlite3-dev sqlite3 \
bzip2 libbz2-dev zlib1g-dev libssl-dev openssl libgdbm-dev \
libgdbm-compat-dev liblzma-dev libreadline-dev libncursesw5-dev libffi-dev uuid-dev

wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz
tar zxvf Python-3.7.0.tgz
cd Python-3.7.0
sudo ./configure && sudo make && sudo make install

sudo rm /usr/bin/python
sudo ln -sf /usr/bin/python3 /usr/bin/python
```

Tensorflow安裝
------
> [Install Tensorflow](https://blog.csdn.net/zqxdsy/article/details/102910840)

> [Tensorflow Link](tensorflow：https://www.piwheels.org/simple/tensorflow/)

> 如果套件安裝速度緩慢, 直接至對應安裝包的網址下載再手動安裝 [piwheels](https://www.piwheels.org/)

```
sudo apt install python3-pip python3-dev libatlas-base-dev
wget https://www.piwheels.org/simple/tensorflow/tensorflow-1.13.1-cp37-none-linux_armv7l.whl
sudo pip install tensorflow-1.13.1-cp37-none-linux_armv7l.whl
```
##### Verification
```
import tensorflow as tf
hello = tf.constant('Hello!')
sess = tf.Session()
print(sess.run(hello))
```

librosa
------
> [librosa](https://librosa.github.io/librosa/)
```
sudo apt install llvm
sudo pip install scipy
sudo pip install librosa
```

PyAudio
------
> [PyAudio](https://pypi.org/project/PyAudio/)
```
sudo apt install python-all-dev portaudio19-dev
sudo pip install pyaudio
```

Sox
------
> [Sox](http://sox.sourceforge.net/)
```
sudo apt install sox
sudo apt install lame
sudo apt install libsox-fmt-all
```

Matplotlib
------
```
sudo pip install matplotlib
```

Keras
------
```
sudo apt install libhdf5-dev libatlas-base-dev libjasper-dev libqt4-test libqtgui4
sudo pip install keras==2.3.1
```

Office
------
```
sudo apt install libreoffice
libreoffice-writer ：文字處理器
libreoffice-calc ：電子表格
libreoffice-impress ：演示文稿
libreoffice-draw ：绘圖
libreoffice-base ：資料庫
libreoffice-math ：公式編輯器
libreoffice-filter-mobiledev ：移動設備過濾器
```

Git
------
> [Git](https://blog.jaycetyle.com/2018/02/github-ssh/)

> [How to use git](https://blog.jaycetyle.com/2018/02/github-ssh/)
```
sudo apt install git
git config --global user.email "s1064627@g.yzu.edu.tw"
git config --global user.name "recklight"
```
#### Setting key
```
ssh-keygen
cat /home/pi/.ssh/id_rsa.pub
```
#### Clone repost
```
mkdir Github
cd Github
git clone git@github.com:recklight/CONSE_matlab.git
```
#### Push new files
```
cd CONSE_matlab
git add --all
git commit -m "test"
git push -u origin master
```




Chinese_Input
------
> [Link](https://hugheschung.blogspot.com/2019/01/raspberry-pi_24.html)
```
sudo apt-get install scim-chewing
```

LCD3.5
------
> [LCD35 install](http://www.waveshare.net/wiki/3.5inch_RPi_LCD_(A)#.E8.AE.BE.E7.BD.AE.E6.98.BE.E7.A4.BA.E6.96.B9.E5.90.91)
```
git clone https://github.com/waveshare/LCD-show.git
cd LCD-show/
sudo ./LCD35-show
```
#### 畫面方向
```
cd LCD-show/
sudo ./LCD35-show X # X=0,90,180,270
```
#### 觸碰校準
```
sudo apt-get install xinput-calibrator
(Menu -> Preferences -> Calibrate Touchscreen)
```
#### 虛擬鍵盤
```
sudo apt-get install matchbox-keyboard
```
#### 切換顯示
###### LCD->HDMI: 
```
# LCD->HDMI: 
cd LCD-show/
./LCD-hdmi
```
###### HDMI -> LCD
```
cd LCD-show/
./LCD35-show
```

OpenCV3.4
------
#### Install OpenCV
>The latest version of openCV doesn't work on RPi
```
sudo pip3 install opencv-python==3.4.6.27
```

PyTorch
------
#### Install dependencies 
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt install libopenblas-dev libblas-dev m4 cmake cython python3-dev python3-yaml python3-setuptools \
libavutil-dev libavcodec-dev libavformat-dev libswscale-dev
```
#### Install PyTorch and PyTorch Vision using the pre-compiled Python wheel files
> Download wheel files from https://github.com/sungjuGit/Pytorch-and-Vision-for-Raspberry-Pi-4B 
```
sudo pip install replace_with_name_for_pytorch_wheel.whl
sudo pip install replace_with_name_for_pytorchvision_wheel.whl
```
#### Or, get the latest version by building PyTorch from the source
```
mkdir pytorch_install && cd pytorch_install
git clone --recursive https://github.com/pytorch/pytorch
cd pytorch && git submodule update --remote third_party/protobuf
export NO_CUDA=1
export NO_DISTRIBUTED=1
export NO_MKLDNN=1 
export NO_NNPACK=1
export NO_QNNPACK=1
python3 setup.py build
sudo -E python setup.py install
cd .. && mkdir pytorch_vision_install && cd pytorch_vision_install
git clone --recursive https://github.com/pytorch/vision
cd vision
sudo -E python setup.py install
```
#### Verification
```
python
import torch
torch.__version__
```
