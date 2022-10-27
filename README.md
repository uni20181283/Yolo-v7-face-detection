# Yolo v7 Face Detection

# 추가할 것들
1. readme 깔끔하게( ~ 10/30)
2. train한 결과물 올리기( ~ 11/6)
3. 코드 편하게 사용할 수 있도록 수정 후 올리기 ( ~ 11/13)


## Description
The project is a wrap over [yolo v7](https://https://github.com/WongKinYiu/yolov7) repo.
Model detects faces on images and returns bounding boxes.
## Installation
```bash
pip install -r requirements.txt
```
## Usage example
```python
from face_detector import YoloDetector
import numpy as np
from PIL import Image

model = YoloDetector(target_size=720,gpu=0,min_face=90)
orgimg = np.array(Image.open('test_image.jpg'))
bboxes,points = model.predict(orgimg)
```
You can also pass several images packed in a list to get multi-image predictions.
```python
bboxes,points = model.predict([image1,image2])
```
If you want to use model class outside root folder, export it into you PYTHONPATH
```bash
export PYTHONPATH="${PYTHONPATH}:/path/to/yoloface/project/"
```

## Result example
<img src=./result_example.jpg>

## Citiation
Thanks [deepcam-cn](https://github.com/deepcam-cn/yolov5-face) for pretrained models.
