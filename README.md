## Automatic Number Plate Recognition

## Problem Statement
In the year 2020, there were about 590 violations daily to be processed by Singapore's Traffic Police. As a staff of the tech division in the Police force, you were tasked with exploring ANPR and its use cases and come up with ways that the traffice police can integrate ANPR into its process to improve operational efficiency.


## Executive Summary
In a bid to improve operational efficiency, a POC has been created to detect and recognise license number numbers off images of cars in Singapore. The POC made use of a combination of Object Detection (using YOLOv5) and Tesseract Optical Character Recognition (OCR), to extract license plate numbers from a given image.

Starting with data acquisition, we scrapped images of public accounts on Instagram. Collected images were then labelled using [Roboflow](https://roboflow.com/). Bounding boxes were specified around legible license plates in these photos. The saved annotations were exported to YOLO format. The custom dataset was then formated and split into train, validation, and test set.

Following the data preparation process, we trained YOLOv5 on our custom object (license plates) using the model’s pre-trained weights for transfer learning. The model's performance was evaluated using the mean Average Precision (mAP) metric. Our model performed pretty well as the mAP score was 80.72%. The closer our mAP score is to 100%, the better. Using this model we were able to detect and localise the bounding box coordinates of the bus panel contained in an image. We consider the model to be performing relatively well given that it is successful in generating predictions on new images. Finally, we incorporated both the custom object detection model and tesseract to transform the license plate numbers into raw text data with Tesseract OCR, ready to be exported or saved into databases.

### Additional Information
There are a total of three notebooks in this project, namely:
* [1_Data_Collection (Webscraping)](https://github.com/nahweijie1/Capstone/blob/main/code/1.%20Data%20Collection%20(Webscraping).ipynb)
* [2_YOLOv5_Custom_Training](https://github.com/nahweijie1/Capstone/blob/main/code/2.%20YOLOv5_Custom_Training.ipynb)
* [3_OCR.ipynb](https://github.com/nahweijie1/Capstone/blob/main/code/3.%20OCR.ipynb)

*Note: Notebook 2 is ran entirely on Google Colab. Google Colab is a free cloud service that supports free GPU*

## Conclusion
We  were able to create a working POC for deployment and tested that it is indeed tangible to make use of computer vision-based system to improve operational efficiency. We were able to train YOLOv5 on our custom dataset and found that YOLOv5 trains quickly, inferences quickly, and performs really well in detecting license plate(s) contained in an image. However, we were also limited by large of our dataset in terms of it's variablity and quantity.

### Future Exploration
* Try out our POC to ID containers
* Active learning 
* Train the object detection model on images taken with IR camera
* Exploring deployment of our model onto a web-app to allow ppl to upload their own images.
