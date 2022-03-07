ImageNet

例程：#（默认网络是googlenet）
cd jetson-inference/build/aarch64/bin
./imagenet.py images/orange_0.jpg images/test/output_0.jpg

ps：位置参数不写出来 不写DIR=
====================================================
DetectNet：

例程：#（默认网络SSD-Mobilenet-v2）
cd jetson-inference/build/aarch64/bin
 ./detectnet.py --network=ssd-mobilenet-v2 images/peds_0.jpg images/test/output.jpg

我的jojo项目：
python3 train_ssd.py --dataset-type=voc --data=./my_data/data_img/ --model-dir=./models/（没成功 因为 label.txt文件需要在某一个文件夹）
python3 train_ssd.py --dataset-type=voc --data=./my_data --model-dir=./models/
python3 onnx_export.py --model-dir=models/
python3 onnx_export.py --model-dir=models/my_jojomodle （未运行，因为默认生成的labels.txt需要和生成的onnx文件在同一个文件夹，运行会缺少txt）
NET=./models/
detectnet --model=$NET/ssd-mobilenet.onnx --labels=$NET/labels.txt           --input-blob=input_0 --output-cvg=scores --output-bbox=boxes             /dev/video0


标准：
train.py    my_projecet_models  my_project: labels.txt  7个文件夹

python3 train_ssd.py --dataset-type=voc --data=./my_project --model-dir=./my_projecet_models/

python3 onnx_export.py --model-dir=./my_projecet_models/

NET=./my_projecet_models/

detectnet --model=$NET/ssd-mobilenet.onnx --labels=$NET/labels.txt  --input-blob=input_0 --output-cvg=scores --output-bbox=boxes             /dev/video0

===================================
1 Building the project from Source

#
$ sudo apt-get update 
$ sudo apt-get install git cmake libpython3-dev python3-numpy 
$ git clone --recursive https://github.com/dusty-nv/jetson-inference 
$ cd jetson-inference 
$ mkdir build 
$ cd build 
$ cmake ../ 
$ make -j $( nproc ) 
$ sudo make install 
$ sudo ldconfig
#
====================================
Classifying Images with ImageNet
#
cd jetson-inference/build/aarch64/bin/
./imagenet images/orange_0.jpg images/test/output_0.jpg 
./imagenet images/orange_0.jpg images/test/aa_0.jpg
./imagenet --network=resnet-18 images/jellyfish.jpg images/test/bbb.jpg 
# use * can all traverse
Processing a Video Magenet
#
wget https://nvidia.box.com/shared/static/tlswont1jnyu3ix2tbf7utaekpzcx4rc.mkv -O jellyfish.mkv
./imagenet --network=resnet-18 jellyfish.mkv images/test/jellyfish_bbb.mkv
fail
#摄像头图像分类 画面混乱远没有detect效果好
/imagenet.py /dev/video0
=====================================
Locating Objects with DetectNet
#
./detectnet --network=ssd-mobilenet-v2 images/peds_0.jpg images/test/a.jpg
./detectnet " images/peds_*.jpg " images/test/peds_output_%i.jpg//fail run follow
./detectnet --network=ssd-mobilenet-v2 "images/peds_*.jpg" images/test/peds_%i.jpg
#
detect mkv failed also
#
./detectnet /dev/video0  
#
=======================================
制作好数据集后（一定要检测空白行 BackGround是不算class num的）
Readme.md可以查找train方法
#
python3 train_ssd.py --dataset-type=voc --data=data/data --model-dir=models/my_test_model2022
python3 onnx_export.py --model-dir=models/my_test_model2022
NET=./models/my_test_model2022
detectnet --model=$NET/ssd-mobilenet.onnx --labels=$NET/labels.txt  --input-blob=input_0 --output-cvg=scores --output-bbox=boxes /dev/video0
#

