# Driver-Drowiness-Detection

## Introduction

With the advancement of Artificial Intelligence, Computer vision came into the scene in the late 1960s. The purpose of this technology is to increase the intellect of the artificial mechanism by installing the cameras  into  them  and describe  whatever  they  see just  like  a human’s  visual  system. 
Driver drowsiness detection is a form of car safety technology and is used to prevent accidents that are caused by the driver of the car getting drowsy or sleepy. In this project, we have used CNN through Python and data provided by Prasad Patil on kaggle to teach the model how to detect a driver’s drowsiness through eye monitoring.


## How the code works?

## Training Part
1. Images are loaded from any folder to specify, resize them to 80x80 and loaded into an 'image' array.
2. First, all training images are imported and given label value '0' for opened eyes and '1' for closed eyes. Then they are both added to get a whole array.
3. The images are converted into an array, reshaped and scaled by dividing them by 255.
4. train_test_split function is used to divide the data into training and validation sets.
5. Next, the model architecture is created. First, previous sessions are cleared and we instantiate the model. Then, 
    1. Define the first 3 convolutional layers
    2. add the max pooling layer
    3. add 2 more convolutional layer
    4. add the last pooling layer
    5. flatten the array of the image to allow it to enter the dense layers
    6. adding first dense layer which has 256 nodes
    7. add a dropout layer so we can prevent overfitting
    8. add the output dense layer with sigmoid activation function
    9. compile the model
6. Then, the summary of the model is viewed and fit to a model to start training (batch size= 800, epochs=15)
7. PlotLossesKeras() function is used to view our training in real-time. And the model is evaluated.
 *pic of the graph
 8. Then, the F-1 score, Accuracy, Precision & Recall is calculated.
 9. The Cohens Kappa Score, ROC AUC Score, and confusion matrix is displayed.
 10. The model will then be saved for image detection in testing phase.

## Testing Part: Real-time Image Detection
1. Modules playsound, CMake, face_recognition and soundevice is installed.
    playsound: to play the alarm
    face_recognition: to recognise left and right eyes
    sounddevice: to record own alarms
2. The trained model previously is loaded using keras.
3. Users can choose to record their own alarm or use a default one.
4. eye_cropper function is used to crop user's eyes from the rest of their face.
5. Webcam is initiated for real-time image detection.
6. Continuous frames are captured by the webcam to send to the eye_cropper function.
7. Images are scaled, reshaped and resized into the model.
8. Prediction is done and class of the Eyes are decided based on the prediction (closed eyes = of the range of 0.4 - 0.9 ++, Open eyes = of the range of less than 0.001)
9. When the eyes are opened, the state of the driver will be declared as Active. It means that the driver is awake, hence no alarm sound will be played. 
10. When the eyes are closed, the counter is increased by 1. However, it is still declared as ‘Active’ because closed eye detection is considered a blink. 
11. If the value of the counter is larger than 3 (meaning that the else statement has executed three times). This means the eyes have been closed for 3 loops, so it is not classified as a blink anymore. The driver is considered sleeping. It will be declared as ‘Driver Sleeping’ in the middle of the screen. Whichever alarm we have chosen will play until our eyes reopen. 
12. Then, the counter is set to 1 again. 
13. 27 or the Escape key is our exit key. 
14. Lastly, we let go of the webcam and close the application.

## How to run it?

Image Detection
1. Run the Drowsiness_Detection_3.ipynb 
2. Choose to record your own alarm or use a default one

## Result

<img src="https://user-images.githubusercontent.com/85062756/120106400-5ece6200-c18f-11eb-93ea-bc892dd6a2d4.png" width="300" height="400" />
<img src="https://user-images.githubusercontent.com/85062756/120105676-912a9000-c18c-11eb-883c-5fe43a9dd587.png" width="300" height="400" />
<img src="https://user-images.githubusercontent.com/85062756/120105697-a30c3300-c18c-11eb-8bc6-08294a1f4984.png" width="300" height="400" />
<div style="width:360px;max-width:100%;"><div style="height:0;padding-bottom:56.11%;position:relative;"><iframe width="360" height="202" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameBorder="0" src="https://imgflip.com/embed/5bhpvs"></iframe></div><p><a href="https://imgflip.com/gif/5bhpvs">via Imgflip</a></p></div>
