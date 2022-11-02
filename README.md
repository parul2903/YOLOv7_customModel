# YoloV7_customModel
YoloV7 applied on custom dataset. The dataset is collected from Google's OpenImages Dataset and data pre-processing and augmentation steps are done using Roboflow.

# How to implement YOLOV7 in Google Colab:
```bash
git clone https://github.com/WongKinYiu/yolov7
```

Download training weights:
```bash
!wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7_training.pt
```

Training model on custom dataset:
!python train.py --workers 8 --device 0 --batch-size 32 --data data/custom.yaml --img 640 640 --cfg cfg/training/yolov7-custom.yaml --weights 'yolov7_training.pt' --name yolov7-custom --hyp data/hyp.scratch.custom.yaml


Performing detections:

1) On Images
```bash
!python detect.py --weights /content/yolov7/runs/train/yolov7-custom3/weights/best.pt --conf 0.25 --img-size 640 --source /content/car2.jpg
```

2) on Videos
```bash
!python detect.py --weights /content/yolov7/runs/train/yolov7-custom3/weights/best.pt --conf 0.25 --img-size 640 --source /content/traffic.mp4
```

Testing model on custom dataset:
```bash
python test.py --data data/custom.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights yolov7_training.pt --name yolov7_640_val
```

# References:
https://github.com/WongKinYiu/yolov7

https://storage.googleapis.com/openimages/web/index.html

https://roboflow.com/
