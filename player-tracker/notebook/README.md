# Player Tracker Setup

Note: Commands use Jupyter/Colab magics (!, %).

- YOLOv5 setup
```
!git clone https://github.com/ultralytics/yolov5
%cd yolov5
%pip install -qr requirements.txt
```

- YOLOv8 install
```
!pip install ultralytics
```

- Install tracking (ByteTrack)
```
!git clone https://github.com/ifzhang/ByteTrack.git
!cd ByteTrack && pip3 install -r requirements.txt
!cd ByteTrack && python3 setup.py develop
!pip install cython_bbox --quiet
!pip install onemetric --quiet
```