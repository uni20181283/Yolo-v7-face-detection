# Yolo v7 Face Detection

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
<img src=/>

## Citiation
Thanks [deepcam-cn](https://github.com/deepcam-cn/yolov5-face) for pretrained models.
