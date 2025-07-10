# Fruit Ripeness Detector AI

This is a AI that can tell you if a fruit is ripe or not. It uses detectnet on the jetson orin nano. The AI can tell you is an apple, banana, or mango is ripe, or unripe. I made this AI because i thought that sorting through ripe and unripe fruit was a long and tedious task that wasnt necessary with the development of AI. 






## How does it work?

The AI can detect this from the colors of the fruit and the shape of it. It uses the ai system detectnet to see each individual fruit, and say if it is ripe, or unripe. You can also download and train your own fruit datasets, and add fruits to detect. 
## Datasets
The AI is trained using the datasets below with 50 epochs.

https://data.mendeley.com/datasets/y3649cmgg6/3

https://www.kaggle.com/datasets/mdsagorahmed/fruit-image-dataset-22-classes (only the apple datasets from the second link)
## Installation guide

Download and prepare the datasets you want to use. 

Mine were:
https://data.mendeley.com/datasets/y3649cmgg6/3
https://www.kaggle.com/datasets/mdsagorahmed/fruit-image-dataset-22-classes (only the apple datasets from there)

Install an open VS code

Then put them in this format in your VS code files: 

    Dataset

        Train

            Ripe

                80% of ripe fruit images

            Unripe

                80% of unripe fruit images

        Val

            Ripe

               20% of ripe fruit images

            Unripe

                20% of unripe fruit images


Train the AI

by using the command: 

yolo task=classify mode=train model=yolov8n-cls.pt data=dataset epochs=50 imgsz=224

If using YOLOv8 (Classification):
yolo task=classify mode=predict model=runs/classify/train/weights/best.pt source=0


Testing:
yolo task=classify mode=val model=runs/classify/train2/weights/best.pt data=/home/nvidia04/final_project/dataset


Exporting to ONNX
Type this command:
yolo export model=runs/classify/train2/weights/best.pt format=onnx


