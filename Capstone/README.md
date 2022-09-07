<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">  

# Capstone Project



# Identifying Monkeypox lesions with Machine Learning Networks

## Contents

- [Executive Summary](#Executive-Summary)
- [Problem Statement](#Problem-Statement)
- [Background Research](#Background-Research)
- [Future Improvement](#Future-Improvement)
- [Conclusions](#Conclusions)

---
  
# Executive Summary  
Tapping onto technology and shared many images online to easily identify monkey pox through images of the skin lesions from the suspected patients. The possibility of identifying the infeected from Machine Learning models would reduce the number of patients that are suspected of monkeypox and hence lighten up the load for medical personel, lab/diagnostic staff, doctors and nurses. Resource would be directed and fully ultilized where is needed. Amid the manpower crunch in the medical sectors, we could look into machine learning models to reduce the physial and mental workload of the medical staff involved.  
  
For this project, I have taken data files from  
Training, validation and test images:  
https://www.kaggle.com/datasets/nafin59/monkeypox-skin-lesion-dataset  
Confirmed cases data:  
https://www.kaggle.com/datasets/aravindas01/monkeypox-cases-countrywise-data
Other images:  
https://www.kaggle.com/datasets/sachinkumar413/monkeypox-images-dataset  
  
In this project, we explore deep convolutional neural networks to predict Monkey pox from images of monkeypox lesions and lesions of other origin. This task would allow us to explore the full power of neural networks, deep neural networks can automatically extract features from the images to help understand and to make the prediction. 
  
Based on the dataset from kaggle, my model was able to attain an overall accuracy score of 0.89.  
  
  
# Problem Statement:
Covid19 have shown that even with great plans, fundings in place, our/global healthcare systems would be overwhelmed by the great influx of patients during a pandemic. Resulting in overworked doctors, nurses and other medical staff which would potentially cause more human errors in handling patients. Even with money, it would take time to train specialists to handle the crists which is not something we could afford to lose.  
  
This project aims to mitigate this issue by reducing the workload, time needed to identify a suspect with accuracy and allow medical instituitions to better optimize deployment of precious resources.
  
---

# Background Research
Symptoms develop over time with a incubation period of 8.5 days. Lesions with rash would develop over the patient's body and contact with contaminated fluids, droplets would result in viral infection. The virus is also animal-borne and may be airborne.  
Originated in Africa and spread outwards to Europe and the rest of the world via social workers who traveled there. Previous 2 outbreak was in Africa with least concern due to low death rates and not easily transmissible between human-human contact. The virus have mutated and evolved since then.  

---

# Future Improvement

#### Find more data for the models to train on
There is actually very little data despite the augmention of photos to increase the number of photos to train the model on. 
  
#### Explore more transfer learning models
I have tried VGG19, efficientnetB3 and self-made CNN models. There are many other models which yield greater potential. Even efficientnet itself have other variants.  

#### More Augment images varient
There are many other way to augment images, this would provide more variety of data to train on. 
  
#### Standardize images used
Photos used consist of close up and non close up shots. By standardizing the photo taking process, or by using only close up shots, it allows for easier learning. 

---
# Conclusions
We have discovered that EfficientNetB3 CNN is capable of predicting monkeypox positive patients with lesion images. There are more levels of optimisation that can be done, and more models that can be explored such as ResNet.  
  
One important realisation is the computational requirement of running such a model. It is true that running the model may be a one-off. However, I cannot emphasize the need for repeatability and optimisation for consumers.  
  
We can deploy the model to front line medical instituitions/departments who often are the first medical point of contact to the patients.  
  
---
