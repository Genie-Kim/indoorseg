# Indoor-segmentation
## Introduction
  This is an implementation of DeepLab-ResNet in TensorFlow for Indoor-scene segmentation on the [ade20k](http://sceneparsing.csail.mit.edu/) dataset. This code is inherited from [tensorflow-deeplab-resnet](https://github.com/DrSleep/tensorflow-deeplab-resnet) by [Drsleep](https://drsleep.github.io/). Since this model is for `robot navigating`, we `re-label 150 classes into 27 classes` in order to easily classify obstacles and road.  

### Re-label list: 
```
1 (wall)      <- 9(window), 15(door), 33(fence), 43(pillar), 44(sign board), 145(bullertin board)
4 (floor)     <- 7(road), 14(ground, 30(field), 53(path), 55(runway)
5 (tree)      <- 18(plant)
8 (furniture) <- 8(bed), 11(cabinet), 14(sofa), 16(table), 19(curtain), 20(chair), 25(shelf), 34(desk) 
7 (stairs)    <- 54(stairs)
26(others)    <- class number larger than 26
26보다 작은 id의 class들 중에 여기 없는 것들은 id가 그대로 유지된다.
color map은 color150.mat 참고, id 정보는 https://github.com/CSAILVision/sceneparsing/blob/master/objectInfo150.csv
```

  
## Install 
python3.5
Install tensorflow-gpu1.1.0
```
sudo docker pull tensorflow/tensorflow:1.1.0-gpu-py3
```
or
```
pip install tenworflow-gpu==1.1.0
```

and
```
pip install -r requirements.txt

```

First get restore checkpoint from [Google Drive](https://drive.google.com/drive/folders/0B9CKOTmy0DyaQ2oxUHdtYUd2Mm8?usp=sharing) and put into `restore_weights` directory.

Run `inference.py` with `--img_path` and `--restore_from`
```
python inference --img_path=FILENAME --restore_from=./restore_weights/ResNet101
```
## Result
### Video
[![Demo video](https://img.youtube.com/vi/4OqW3M-eqaQ/0.jpg)](https://youtu.be/4OqW3M-eqaQ)
### Image
Input image                |  Output image
:-------------------------:|:-------------------------:
![](https://github.com/hellochick/Indoor-segmentation/blob/master/input/IMG_0416_640x480.png)  |  ![](https://github.com/hellochick/Indoor-segmentation/blob/master/output/IMG_0416_640x480.png)
![](https://github.com/hellochick/Indoor-segmentation/blob/master/input/IMG_0417_640x480.png)  |  ![](https://github.com/hellochick/Indoor-segmentation/blob/master/output/IMG_0417_640x480.png)
![](https://github.com/hellochick/Indoor-segmentation/blob/master/input/IMG_0418_640x480.png)  |  ![](https://github.com/hellochick/Indoor-segmentation/blob/master/output/IMG_0418_640x480.png)
