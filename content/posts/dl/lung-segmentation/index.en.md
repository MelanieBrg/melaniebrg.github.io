---
title: "Achieving robust segmentation of lung regions in CT images irrespective to pathology"
date: 2023-07-19
description: Project
menu:
  sidebar:
    name: Lung Segmentation
    identifier: lung-segmentation
    parent: dl
    weight: 10
#tags: ["unity","game"]
hero: front.png
categories: ["project","deep learning", "segmentation"]
hide: false
---


For this research project, I collaborated with Clarisse Nouet and Clara Stavun under the supervision of Catalin Fetita, Noureddine Khiati and Antoine Didier from ARTEMIS departement.


## Introduction

### Context and Problem Statement

#### Infiltrative Lung Pathologies
Infiltrative lung diseases manifest as a progressive disintegration of lung tissues, resulting in impaired functioning. They can obstruct up to 40%, as depicted in the following images, representing lungs affected by IIP (fibrosis), Covid-19, and ARDS (consolidations).

![CT Scan of lungs of patients affected by IIP, Covid-19, and ARDS](lungs_patho.png)

#### Patient Monitoring and Segmentation
These patients require regular monitoring to track the progression of the disease and assess the effectiveness of treatments. The first step in this monitoring is lung segmentation. This method involves identifying and precisely delineating the lungs from medical scans, thereby obtaining quantitative measurements and specifying areas for study. This initial step will facilitate a comprehensive study of the disease, such as the proportion of diseased lung tissues or a study of tissue texture.

#### Problem Statement
Automated segmentation is relatively straightforward for healthy lungs. However, when a patient has infiltrative lung diseases, certain areas of the lungs appear clearer on CT scans, making differentiation between the lung and its contour difficult, especially when lung peripheries are affected. Therefore, our project aims to address the following problem: How to automate the segmentation of lungs affected by pathologies?


### State of the Art

#### Segmentation on Healthy Lungs

Today, there are numerous models of deep neural networks capable of segmenting lungs in CT scans. The most commonly used neural network architectures for lung segmentation are U-Net, cascaded convolutional networks, and residual networks. These models are trained on large annotated CT scan databases, enabling them to learn to identify lung contours and structures with increased accuracy.

Image preprocessing techniques such as intensity normalization, noise removal, and histogram matching are often used to improve the performance of lung segmentation models. Additionally, data augmentation techniques such as rotation, cropping, and scaling are used to increase the variability of training data and enhance model robustness.

Performance evaluation of lung segmentation models is typically done using measures such as Dice coefficient, Jaccard index, and sensitivity. Recent work has also focused on segmenting sub-structures within the lungs, such as blood vessels and nodules, to improve the accuracy and clinical relevance of results.

#### Segmentation on Diseased Lungs

There are few studies that use deep learning to address the segmentation problem of lungs with pathology. Other methods are used, such as in studies [1] and [2], which deal with automated segmentation on lungs with pathologies using graph search algorithms. Pu et al [1] developed an algorithm to correct borders to include parts of the lungs that were not detected. Hua et al [2] use a graph search algorithm to segment lung tissues. The algorithm utilizes image intensity and image gradient to define a cost function. This cost function is then used to guide graph search to achieve accurate segmentation of lung tissues. However, these methods are limited, and an approach with deep learning could make automatic segmentation more effective.


### Goals
The project aims to develop a robust lung segmentation method using
convolutional neural networks (CNN), initially for healthy lungs then
for those with infiltrative pulmonary pathologies.

### Tools

We carry out our project on the GPU of the ARTEMIS department with the framework
Python's PyTorch. We also use Wandb which allows us to easily visualize
online the curves of the evolution of the different parameters of the model.


## 1. Lung segmentation without pathology

### 1.1 Objective

Firstly our goal was to segment healthy lungs with a convolutional neural network (CNN). This network should be able to segment the right and left lung from the CT scan of a healthy patient : 

![CT Scan of lungs of patients of healthy patient and objective](objective.png)

Once a first CNN has been built and the first results have been obtained, we optimize the model in order to be able to make a good segmentation of the lungs presenting pathologies.

### 1.2 U-Net Model

#### 1.2.1 U-Net architecture

For our lung segmentation, we chose to use a U-Net architecture due to its common usage in medical segmentation problems. The U-Net model architecture is specifically designed to address the issue of semantic segmentation, where the objective is to classify each pixel of the image into different classes. The model gets its name from its "U" shape, which consists of a combination of convolutional layers and deconvolutional layers, also known as transpose layers. 

The uniqueness of the U-Net model lies in its encoder-decoder architecture, where information is progressively downscaled by convolutional layers in the encoder to extract features, and then restored to their original size by deconvolutional layers in the decoder to perform pixel-by-pixel segmentation. 

Additionally, the U-Net model utilizes residual connections between the layers of the encoder and decoder, allowing for direct connections between low-level and high-level information. This aids in preserving fine details of the image during segmentation.



<img src="/posts/dl/lung-segmentation/architecture.png" height="200">


### 1.3 Access to data

#### 1.3.1 Database presentation

We had access to a database comprising 57 patients, each with hundreds of CT scans (ranging from 300 to 600 scans). Each slice, meaning each CT scan, consists of the scan image and its associated mask where the lungs have been segmented. These images have a size of 512 x 512 pixels.

Moreover, to train, validate, and test the model on different data, the database was divided into three separate sets: the portion used for model training corresponds to 70% of the database, totaling 40 patients, the model validation corresponds to 20%, totaling 11 patients, and the remainder is used for testing, totaling 6 patients.

#### 1.3.2 Data generator

As we are working with relatively large datasets and have limited memory available, loading all the data at once is not feasible. Therefore, we utilized a data generator, a technique commonly used to efficiently load data into memory in small batches.

A data generator is a mechanism that generates and loads data iteratively, as needed, rather than loading it all at once. This significantly reduces memory consumption, as only the data needed at a specific time is loaded into memory.

The operation of a data generator typically relies on iterative loops. It divides the dataset into small parts called batches, and each batch is loaded into memory successively for processing. Once a batch is used, it is removed from memory to free up space.

Thus, the data generator allows us to efficiently load large amounts of data into our environment despite the limited memory available.


### 1.4 Training and validation of the network

#### 1.4.1 Training process and validation

Once the model is built and the data is loaded, the training and validation of the model start.
The training process starts by a loop on the specified number of epochs. One epoch corresponds to a complete iteration over the entire training dataset, meaning that each training sample has been presented to the model once. During each epoch, we loop through the training batches. The data and labels are loaded into GPU memory, and then the model is used to make predictions on the input data. We then compute the model's loss at each epoch using various metrics (see next section). The loss is backpropagated through the model, and the weights are updated using the optimizer. Initially, we opt for the Adam optimizer.

After each training epoch, we evaluate the model on the validation set. The validation data is loaded into GPU memory, and we make predictions using the model. We compute the total validation loss. Periodically, every few epochs, we save the model using checkpoints so that we can reload and reuse it later if needed. Once all epochs are completed, we save the final model to a .pth file. This iterative training and validation process optimizes the model weights to improve lung segmentation performance.


#### 1.4.2 Metrics used


In order to evaluate the performance of the model and measure its ability to accurately and consistently segment the lungs, we use different metrics:
- The dice loss, calculated at each epoch in training and validation, calculating the similarity between two sets (in our case the mask and the predicted image).
This metric helps evaluate how well the predicted segmentation matches the actual areas of the lungs. A Dice coefficient close to 1 indicates accurate segmentation similar to real labels, while a value close to 0 indicates inaccurate segmentation. Its formula is, with 𝑦 the mask and 𝑝 the prediction:


<img src="/posts/dl/lung-segmentation/dice.png" height="100">

- Dice Score: This metric, complementary to the Dice loss, is calculated as 1 minus the Dice loss.
Dice Score (y, p) = 1 - Dice Loss (y, p).

- Cross Entropy Loss: Widely used in classification tasks, it measures the accuracy of classification by assigning higher penalties to incorrect predictions. In the context of lung segmentation, it evaluates the model's ability to accurately predict the different classes of pixels.

- Total Loss: Calculated both during training and validation, the total loss is obtained by summing the Dice loss and the Cross Entropy loss for each batch, and accumulating it batch by batch. It is normalized by dividing by the total number of batches in each epoch. This metric allows us to evaluate the model's performance over epochs, and thus, we focus on it to evaluate and optimize our model.


#### 1.4.3 First results

With this initial model, we choose the following hyperparameters:
- Batch size of x (number of training samples used in one iteration during model training);
- Learning rate of x (determines the speed at which the model adjusts its weights based on the calculated error during training);
- Number of epochs of x.

As a result, we obtain training and validation loss curves:

<img src="/posts/dl/lung-segmentation/result1.png" height="300">

_Total training loss for the first model_

<img src="/posts/dl/lung-segmentation/result1b.png" height="300">

_Total validation loss for the first model_

Thus, we observe that the training loss stabilizes after 15 epochs and tends towards a loss of 2%. However, we notice instability in the validation loss, which may be due to overfitting (a situation where the model fits too closely to the training data and loses its ability to generalize to new data). For this reason, we will attempt to improve and optimize the model further.


### 1.5 Test

We carry out two types of test: on the one hand, in the same way as for validation, we study the performance of the model on data that it does not know, and on the other hand, we visualize and record the predictions on a few patients that the model did not encounter, neither in training nor in validation. As the curves of the first method are generally similar to the validation curves, we focus in the test part on the visualization.
For example, on section 100 of patient 47KD:

{{< split 4 4 4 >}}

<img src="/posts/dl/lung-segmentation/native.png" alt="Native Image" >
Native Image

---

<img src="/posts/dl/lung-segmentation/mask.png" alt="Mask" >
Mask

---

<img src="/posts/dl/lung-segmentation/prediction.png" alt="Prediction" >
Prediction

{{< /split >}}

We observe that the prediction was generally good, but with some inaccuracies at the borders of the lungs.


### 1.6 Model optimisation

#### 1.6.1 AdamW vs Adam

The first modification made is the use of the AdamW optimizer, a variant of the Adam optimizer previously used. AdamW has the advantage of applying weight decay regularization during the model's weight updates. This regularization helps reduce the risk of overfitting by penalizing high values of weights, thus promoting better model generalization. By incorporating this regularization directly into the optimizer, AdamW simplifies the training process by eliminating the need to manually adjust regularization hyperparameters.

#### 1.6.2 Accumulated gradient

To achieve better performance, we aim to increase the batch size. However, due to limited available memory, we cannot exceed a batch size of 4. Therefore, we use accumulated gradient. Instead of updating the model's weights after each mini-batch, gradient accumulation allows us to collect gradients over multiple mini-batches before updating the weights (the frequency of this update is defined by the hyperparameter grad_accum_step).

Furthermore, accumulated gradient can also improve training stability by reducing fluctuations in weight updates. By averaging gradients over several mini-batches, weight updates become smoother and less likely to fluctuate significantly from one iteration to another.

Here are the results obtained for the total training and validation losses:

<img src="/posts/dl/lung-segmentation/result2.png" height="300">

_Total training loss with and without accumulated gradient for 40 epochs_

<img src="/posts/dl/lung-segmentation/result2b.png" height="300">

_Total validation loss with and without accumulated gradient for 40 epochs_

Thus, we observe that the total training loss converges to a similar value in the cases without and with accumulated gradient, around 0.016. For validation, the difference is more pronounced. Indeed, without accumulated gradient, the total loss converges to a value of 0.15, whereas with accumulated gradient, the convergence value is better at 0.1.


### 1.6.3 Choice of Hyperparameters

- Number of epochs: We observed that in the case of the model with accumulated gradient, the total training loss reaches a plateau before stabilizing after 35 epochs. Therefore, we chose to train the model for 40 epochs subsequently.

- Batch size: Similar to previous settings, we maintained a batch size of 4.

- Learning rate: We opted for a learning rate of 0.01 as it fell within the recommended magnitude for our case.

- grad_accum_step: As mentioned earlier to mitigate overfitting, we artificially increase the gradient to 32 by setting grad_accum_step to 8 in addition to the batch size of 4. This allows us to train our model on a more diverse dataset, limiting overfitting.



### 1.7 Results

Using the accumulated gradient model, we obtain the following prediction :

<img src="/posts/dl/lung-segmentation/results3.png" height="300">


## 2. Lung segmentation with pathology

### 2.1 Objective

After segmenting healthy lungs, our goal is to segment lungs with pathologies also using a CNN. This network must be able to identify and extract each lung despite the present diseases:

<img src="/posts/dl/lung-segmentation/lungs_patho.png" height="200">
Examples of CT scans with real diseases


### 2.2 Generation of Pathologies

As we do not have a database of diseased lungs, we simulated diseases from scans of healthy lungs. For this, we created a function that takes an image and a mask of healthy lungs as parameters. Then, using the regionprops function, we detect the two largest boxes containing the lungs from the mask. After extracting the coordinates, we choose between 7 and 9 random positions in the two detected boxes to add circles at these locations on the original lung image. These added circles have random radius and transparency to simulate the diversity of plausible diseases as accurately as possible.

A limitation of our simulation is the circular shape of the diseases we insert, which may not necessarily be representative of the pathologies patients may encounter. Another limitation is the detection of bounding boxes for lungs on certain slices that do not show both lungs. In this case, we apply the addition of pathologies only when two lungs are detected.

<img src="/posts/dl/lung-segmentation/simulation.png" height="300">
Simulation of lung disease


#### 2.2.2 Implementation during training

Instead of saving all images with simulated pathology, we chose to implement them directly during training using an approach known as "on-the-fly" generation. This method involves applying random transformations to the data samples (CT lung scans without pathologies) during training. Thus, the pathology simulations described above are applied to lung images without pathologies during training. To ensure that the model is trained not only on lungs with pathologies but also on those without, pathology generation does not occur on every training image, but only on some, with a variable probability p.


### 2.3 Model Optimization
#### 2.3.1 Choice of Hyperparameters
All hyperparameters of the model remain unchanged compared to lung segmentation without pathologies.

#### 2.3.2 Adjustment of Pathology Appearance Frequency in Training
We run the models with various frequencies of pathology appearance:


{{< split 6 6>}}

<img src="/posts/dl/lung-segmentation/result4.png" height="200">


---

<img src="/posts/dl/lung-segmentation/result4b.png" height="200">


{{< /split >}}

Total loss for training and validation of the model with pathologies of frequency 0.6, 0.8 and 0.9

Whether during training or validation, we notice that the model with a frequency of appearance of pathologies at 0.8 has better performance.

## 2.4 Results

### 2.4.1 Results on images with simulated pathologies 

Here are the results obtained on a patient data unknown to the model : 

<img src="/posts/dl/lung-segmentation/table.png" height="300">

Thus we notice that the model trained with pathologies works just as well with as without pathologies, including when the diseases are present at the edge of the lung.

### 2.4.1 Results on images with real pathologies 

For this project, we simulated the presence of pathologies in the lungs due to a lack of real data. However, these simulations are not always very representative.
This is why we also did tests on some real scan images with pathology:

<img src="/posts/dl/lung-segmentation/table2.png" height="500">

We observe that the model has difficulties with cases of real pathologies. For it to have better performance, it would be interesting to train it on a large number of data with either a high simulated disease density, or directly with real scans of affected lungs.


## Conclusion

### Results
This project implements a method for segmenting healthy lungs and those affected by pathologies in CT-scan images. To achieve this, we deployed a U-Net model and evaluated its performance using various metrics, which characterize our results as satisfactory. Model optimization involved the addition of a data generator, without which the executed programs did not yield results. We also optimized the selection of our hyperparameters to achieve a satisfactory outcome.


### Limitations

It is important to note some limitations of this project. Firstly, the execution times are long. For a run of 40 epochs, it takes approximately 29 hours, making it less feasible due to the significant computational time required. Additionally, although our model yields acceptable performance, there is room for improvement.

Moreover, as previously discussed, the results obtained on real pathology images are less satisfactory. Therefore, it is necessary to consider potential avenues for improvement to achieve better performance, such as using scans with real pathologies during training or increasing the density of simulated pathologies.


## Areas for Improvement

We have considered several avenues for improvement, such as better simulating diseases to closely approximate the real aspect of pathologies. Indeed, we observed poorer estimations on real images of diseased lungs since the network is trained only on synthesized pathologies with a superimposition of circles. To address this, we could add more circles on the lungs, with the densities adding up to create obstructed areas. Additionally, we could manipulate the texture or add other shapes besides circles. Moreover, to obtain more training data for better performance, we could consider implementing additional augmentations and/or obtaining more scans with real pathologies.

Furthermore, we could use models like ResNet in the downward part to improve performance. Finally, the project could be extended to achieve a 3D rendering of the lungs for better visualization.
