# Abstract
In this project, i implement the task of car detection by using yolov5 model. 

# Data preparation
For visualization of dataset architecture, i only upload a few images and labels into the "dataset/car" folder. You can prepare your own custom dataset by follow format of the folder "dataset/car" of this project. 

Data used for training is placed in folder "dataset/car", which has 3 subfolders "train", "test" and "valid". In each of these 3 folders, there are 2 subfolders "images" and "labels" that store images and annotations for corresponding images. For example, file "dataset/car/train/labels/00007_jpg.rf.449c08b30f6d323bfbf203d65fd50877.txt" contains bounding box annotation for the image "dataset/ar/train/images/00007_jpg.rf.449c08b30f6d323bfbf203d65fd50877.jpg". The annotation information is stored in the yolov5 format.

For more detail on how to prepare custom dataset for training, please follow guide from this link : https://blog.roboflow.com/how-to-train-yolov5-on-a-custom-dataset/

# Installation 
Please install required environment by running the command "pip install -U -r requirements.txt" 

# Train 
To train, please run this command :
python train.py --img 416 --batch 16 --epochs 1 --data car/data.yaml --cfg models/custom_car_yolov5s.yaml --name yolov5s_results --nosave --cache --name best_car

After training completed, a weight file named "best_car.pt" will be saved into folder "weights".

# Test 
For demo, i have upload a pretrained model with path "weights/best_car.pt" into this project. To test, simply run this command: 
python detect.py --weights weights/best_car.pt --img 416 --conf 0.4 --source inference/images

By running this command, it would detect car in all images saved in folder "inference/image", and the result would be saved into folder "inference/output".

