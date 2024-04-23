# Pneumonia-Detection-via-Deep-Learning
### background
Pneumonia accounts for over 15% of all deaths of children under 5 years old internationally. In 2015, 920,000 children under the age of 5 died from the disease. In the United States, pneumonia accounts for over 500,000 visits to emergency departments  and over 50,000 deaths in 2015 , keeping the ailment on the list of top 10 causes of death in the country.

While common, accurately diagnosing pneumonia is a tall order. It requires review of a chest radiograph (CXR) by highly trained specialists and confirmation through clinical history, vital signs and laboratory exams. Pneumonia usually manifests as an area or areas of increased opacity  on CXR. However, the diagnosis of pneumonia on CXR is complicated because of a number of other conditions in the lungs such as fluid overload (pulmonary edema), bleeding, volume loss (atelectasis or collapse), lung cancer, or post-radiation or surgical changes. Outside of the lungs, fluid in the pleural space (pleural effusion) also appears as increased opacity on CXR. When available, comparison of CXRs of the patient taken at different time points and correlation with clinical symptoms and history are helpful in making the diagnosis.

CXRs are the most commonly performed diagnostic imaging study. A number of factors such as positioning of the patient and depth of inspiration can alter the appearance of the CXR , complicating interpretation further. In addition, clinicians are faced with reading high volumes of images every shift.





### Environment Setup

- Install Required Libraries
- Set Up Kaggle API
- Download and Unzip Dataset

The data set used in this project comes from: https://www.kaggle.com/competitions/rsna-pneumonia-detection-challenge/overview/evaluation
The model used in this project comes from: https://github.com/leekunhee/Mask_RCNN
The COCO pre-trained weights used in this project comes from: https://github.com/matterport/Mask_RCNN/releases/download/v2.0/mask_rcnn_coco.h5


### Code Implementation

- Data Loading and Preprocessing

Use the kaggle library to download the RSNA pneumonia detection challenge dataset through the Kaggle API.
Decompress and load data, read medical images, and perform preliminary image quality control and preprocessing.
- Adjust configuration class

In this configuration class, these parameters are set to simplified version values for demonstration, and may need to be adjusted according to specific needs in actual applications
- image enhancement
Perform the following processing on the images respectively.

> Geometric transformations: Slight scaling, translation, rotation and shearing of images.
> Brightness and contrast adjustment
> blur and sharpen

The processing effect is as follows:
![User Interface Example Image](https://github.com/chenjianxu75/Pneumonia-Detection-via-Deep-Learning/blob/main/1.png)

- Data partition


- Training model

train the model.
dataset_train and dataset_val are derived from DetectorDataset
DetectorDataset loads images from image filenames and masks from the annotation data
model is Mask-RCNN

- Visualization of training effects
![User Interface Example Image](https://github.com/chenjianxu75/Pneumonia-Detection-via-Deep-Learning/blob/main/2.png)

Learning progress:
The model's loss value shows an overall downward trend during the training process, which can show progress in the prediction task.
Overfitting tendency:
Although the loss value decreases, after a specific epoch, the loss value of the validation set increases, which may indicate that the model is overfitting. The performance improvements of the model on the training data do not transfer well to the validation data.
Classification performance:
The chart of classification loss shows that validation loss is relatively stable, with high volatility but no obvious upward trend. This may mean that the model generalization ability of the classification part is better.
Positioning performance:
The downward trend in localization loss indicates that the model is performing well in determining the location of objects in the image, but the fluctuation in validation loss also indicates that further optimization may be needed to improve the model's performance on unseen data.


## reasult
Comparison of predicted box and expected value:
![User Interface Example Image](https://github.com/chenjianxu75/Pneumonia-Detection-via-Deep-Learning/blob/main/3.png)

