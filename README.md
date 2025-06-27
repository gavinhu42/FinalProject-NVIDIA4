Jetson Nano New England Fish Detection Program
![image](https://github.com/user-attachments/assets/1ff9c056-3658-401b-8b9b-7676616ee6e7)

Project Overview:
This project takes in a dataset of different fishes that are commonly found across the New England area. Using imageNet and Yolov8 through the Jetson Nano Orim, this program can accurately classify and differentiate between images of these common fish species

Why:
Aspiring or veteran fishers all struggle with classifying fishes that they catch or want to catch. So, this program allowes fisherman in the New England area to be able to accurately determine their fish. This helps in many ways: it makes selling easier, offers convenience by removing the need for looking it up, and reduces the risk of mislabeling. 

Setup Instructions:

1. Export your model using YOLOv8:
  yolo export model=yolov8n-cls.pt format=onnx imgsz=224
2. Copy model to Jetson Nano:
  scp yolov8n-cls.onnx labels.txt nvidia@<JETSON_IP>:~/jetson-inference/finalproject/
3. Install Jetson Inference:
  git clone --recursive https://github.com/dusty-nv/jetson-inference
  cd jetson-inference/build
  cmake ../
  sudo make install

Run Classification:

imagenet dataset/mackerelFish/mackerel1.jpg output.jpg \
--model=yolov8n-cls.onnx --labels=labels.txt \
--input-blob=images --output-blob=output0


Requirments:

- Jetson Nano Orin
- YOLOv8
- Python 3
- ONNX-compatible classification model
