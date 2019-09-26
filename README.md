# Face Detection and Classification
This model performs realtime face detection and emotion/gender classification.
Model: Keras CNN and OpenCV
Datasets: [IMDB-WIKI](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/) and [FER2013 dataset](https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data)
* IMDB-WIKI gender classification test accuracy: 96%.
* FER2013 emotion classification test accuracy: 66%.

For more information please consult the [publication](https://github.com/oarriaga/face_classification/blob/master/report.pdf).

### Examples of emotion and gender classification
![alt tag](images/demo_results.png)

### Guided backpropagation
![alt tag](images/gradcam_results.png)

### Realtime demo
<div align='center'>
  <img src='images/color_demo.gif' width='400px'>
</div>

[B-IT-BOTS](https://mas-group.inf.h-brs.de/?page_id=622) robotics team :)
![alt tag](images/robocup_team.png)

## Instructions

### Run the realtime emotion demo
```
python3 video_emotion_color_demo.py
```

### Run the realtime guided backpropagation demo
```
python3 image_gradcam_demo.py
```

### Run inference on individual images
```
python3 image_emotion_gender_demo.py <image_path>
```

For example:
```
python3 image_emotion_gender_demo.py ../images/test_image.jpg
```

### Running with Docker

With a few steps one can get its own face classification and detection running. Follow the commands below:

```
docker pull ekholabs/face-classifier
docker run -d -p 8084:8084 --name=face-classifier ekholabs/face-classifier
curl -v -F image=@[path_to_image]  http://localhost:8084/classifyImage > image.png
```

### To train previous/new models for emotion classification:

* Download the dataset from [this Kaggle competition](https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data).

* Move the downloaded file to the folder face_classfication/datasets.

* Untar the file:
> tar -xzf fer2013.tar.gz

* Run the train_emotion_classification.py file
> python3 train_emotion_classifier.py

### To train previous/new models for gender classification:

* Download the imdb_crop.tar file from [here](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/) (It's the 7GB button with the tittle Download faces only).

* Move the downloaded file to the datasets directory inside this repository.

* Untar the file:
> tar -xfv imdb_crop.tar

* Run the train_gender_classification.py file
> python3 train_gender_classifier.py
