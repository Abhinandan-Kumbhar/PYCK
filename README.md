## Summary
The objective of the project is to implement Keras framework for deep learning to train a model to classify different types of tumors.
The weights of a pre-trained model called EfficientNetB1 is used and retrained on given dataset.
## Implementation details
**1. Clone the Github Repo to access the Dataset and import necessary Libraries**  
    1.	The dataset from github repo was copied in local directories and import necessary libraries  
**2. Creating local libraries to store the cropped images:**  
    The os library was used to create directories where cropped images will be stored as training and testing sets  
**3. Create a Function to crop images:**  
    1.	The images in dataset are having extra plain black regions surrounding the actual image  
    2.	Since this extra region does not add any value and does not catch any important feature, we have to crop extra region  
    3. We start with converting colored images into gray image using COLOR_BGR2GRAY method of opencv library  
    4. We then use GaussianBlur method to remove insignificant gray regions and keep only significant contours which helps to learn important features of image  
    5. We then reshape this cropped images in shape of (224,224) and save them to respective directories to be accessed later  
**4. Data Augmentation:**  
    Since we have limited number of examples, we use data augmentation techniques to expand the dataset. We rotate, flip and translate the images to create new images  
**5. Prepare the Train, Validation and Test Dataset:**  
**6. Build and Compile the Model:**  
    1.	The EfficientNetB1 is used to create the required model with CNN framework with input of size (224,224,3)  
    2.	We need output of size 4x1, since there are 4 classes. Since, the output of EfficientNetB1 is not 4x1, we have to add a dense layer which outputs 4 units along with dropout regularization and global average pooling  
    3.	We compile this model using Adam optimizer with learning rate of 0.001. We use categorical cross entropy and use accuracy as metric  
**7. Model Training and Model Evaluation:**  
    1.	We train the model with 7 epochs and we have to use early stop checkpoints  
    2.	The EarlyStopping method stops the optimization, if the validation accuracy does not improve for 5 iterations (patience level)  
    3.	The test accuracy comes out to be 0.9%  
The below graph shows improvement in performance over different epochs. The green graph is for training and red is for validation  
 ![metric](https://github.com/Abhinandan-Kumbhar/PYCK/blob/main/pyck.png)
## Conclusion
The traning dataset acccuracy is 94.7% and the test accuracy is also good i.e  90%. We can say the model is trained properly.
