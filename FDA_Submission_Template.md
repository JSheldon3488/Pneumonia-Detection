# FDA  Submission

**Your Name:** Justin Sheldon

**Name of your Device:** Deep Neural Network Pneumonia Detector

## Algorithm Description 

### 1. General Information

**Intended Use Statement:** Used to aid in detection of Pneumonia from Digital Radiography chest images (chest x-rays).

**Indications for Use:** This algorithm should be used to aid in detection of high risk patients for pneumonia so that these x-rays
can be flagged as urgent for a radiologist to take a closer look. This algorithm could be employed as soon as the x-ray is processed.
The algorithm must be used with Digital Radiography images that are of the patients chest area. It will work with both 
PA (Posterior->Anterior) and AP (Anterior->Posterior) views and can be used for patients of any age male or female. 
Details about the dataset that the algorithm was trained on can be found in the EDA notebook.

**Device Limitations:** Due to the severity of pneumonia we wanted to catch as many positive cases as possible without sacrificing too much precision.
This lead to choosing a low threshold for classifying a case as positive. Due to this, the algorithm will have a high false positive rate
(64.5% on our validation dataset). We believe this is an good trade off because this algorithm is only intended to be an aid to the 
radiologist so that they can view high risk cases as soon as possible. The radiologist will still be the one deciding if the patient
has pneumonia or not, the algorithm just helps them see high risk cases sooner in their workflow.

**Clinical Impact of Performance:** Due to the severity of pneumonia it is important to detect high risk patients as soon 
as possible and this algorithm could help in alerting radiologist to high risk patients so that they can move these patients
up in their queue of cases to look at.

### 2. Algorithm Design and Function

![](images\Dicom_FlowChart.png)

**DICOM Checking Steps:** To verify that the DICOM file is correct for our algorithm we need to make sure the image modality
is equal to 'DX' (Digital Radiography), we need to check that the position of the patient during the scan is either 'PA' or 'AP',
and we need to make sure that the body part examined is 'CHEST'.

**Preprocessing Steps:** The preprocessing for this model is very simple. All we do is rescale the pixel values from the
range of 0-255 down to 0-1 by dividing each pixel by 255. This helps when training the network.

**CNN Architecture:** The model used is a pre-trained DenseNet201 architecture with a single fully connected output layer of
size 1 to output a probability of pneumonia. The model was pre-trained on the 'imagenet' dataset. The entire DenseNet architecture
is explained in this [paper](https://arxiv.org/pdf/1608.06993.pdf). 


### 3. Algorithm Training

**Parameters:**
* Types of augmentation used during training: horizontal flip, rotation_range=20, shear_range=0.1, zoom_range=0.15
* Batch size: 128
* Optimizer learning rate: 1e-5
* Layers of pre-existing architecture that were frozen: First 160
* Layers of pre-existing architecture that were fine-tuned: Last 40
* Layers added to pre-existing architecture: Single output layer changed from 1000 class classification to a single class classification.

![](images\DenseNet_history.png)

![](images\DenseNet_f1_score.png)

**Final Threshold and Explanation:** Based on the indications of use statement, we would like this algorithm to have high
recall in order to aid the radiologist with detecting high risk pneumonia cases early in their workflow. That being said we still
would like some precision so that we are not sending too many false positives to the radiologist. Based on these factors and looking
at the precision recall curves above, I used a threshold value of 1.35.

### 4. Databases
 (For the below, include visualizations as they are useful and relevant)

**Description of Training Dataset:** 


**Description of Validation Dataset:** 


### 5. Ground Truth



### 6. FDA Validation Plan

**Patient Population Description for FDA Validation Dataset:**

**Ground Truth Acquisition Methodology:**

**Algorithm Performance Standard:**
