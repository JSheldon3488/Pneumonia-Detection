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

<< Insert Algorithm Flowchart >>

**DICOM Checking Steps:**

**Preprocessing Steps:**

**CNN Architecture:**


### 3. Algorithm Training

**Parameters:**
* Types of augmentation used during training
* Batch size
* Optimizer learning rate
* Layers of pre-existing architecture that were frozen
* Layers of pre-existing architecture that were fine-tuned
* Layers added to pre-existing architecture

<< Insert algorithm training performance visualization >> 

<< Insert P-R curve >>

**Final Threshold and Explanation:**

### 4. Databases
 (For the below, include visualizations as they are useful and relevant)

**Description of Training Dataset:** 


**Description of Validation Dataset:** 


### 5. Ground Truth



### 6. FDA Validation Plan

**Patient Population Description for FDA Validation Dataset:**

**Ground Truth Acquisition Methodology:**

**Algorithm Performance Standard:**
