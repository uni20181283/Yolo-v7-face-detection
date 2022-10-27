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
## Other pretrained models
You can use any model from [yolov5-face](https://github.com/deepcam-cn/yolov5-face) repo. Default models are saved as entire torch module and are bound to the specific classes and the exact directory structure used when the model was saved by authors. To make model portable and run it via my interface you must save it as pytorch state_dict and put new weights in `weights/` folder. Example below:
```python
model = torch.load('weights/yolov5m-face.pt', map_location='cpu')['model']
torch.save(model.state_dict(),'path/to/project/weights/yolov5m_state_dict.pt')
```
Then when creating YoloDetector class object, pass new model name and corresponding yaml config from `models/` folder as class arguments.
Example below:
```python
model = YoloFace(weights_name='yolov5m_state_dict.pt',config_name='yolov5m.yaml',target_size=720)
```

## Result example
<img src="/results/result_example.jpg" width="600"/>

## Citiation
Thanks [deepcam-cn](https://github.com/deepcam-cn/yolov5-face) for pretrained models.
