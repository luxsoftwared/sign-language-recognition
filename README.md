# sign-language-recognition

This project implements a sign language recognition app in Python that can detect and interpret sign language gestures in real-time using a webcam. It utilizes machine learning models to classify hand gestures and provides features for training new models, live recognition, and capturing gesture data for further training.

# Functionalities

* **Making or expanding Datasets**  
Using Google's Mediapipe solutions for identifying face and body landmarks, landmarks are extracted from camera feed, transformed and formatted using `numpy`, and saved locally. This can be used to make new datasets from scratch, or to improve existing datasets by either recording more instances for existing signs, or by creating a new class(new sign to be recognized) and recording samples for it.

* **Training and evaluating models**  
Using `keras` library for building and training neural networks, sequential model is formed with 6 layers - 3 dense layers, and 3 LSTM layers. Recurrent neural network is used because it enables easier detection of signs that are dynamic(have movement incorporated), because the app was made with Serbian sign language in mind, which has a lot of dynamic signs. Training is done on locally available dataset.
Evaluation and tracking of models is done using `sklearn.metrics` library and `TensorBoard`, by examining values for recall, precision, accuracy and F1 scores, and confusion matrix.

* **Recognition**  
In recognition mode, existing trained models can be loaded, and app turns on the camera and starts detecting and displaying signs from the live camera feed.

# GUI

![GUI_view](https://github.com/user-attachments/assets/b964bb39-48bd-4886-b3af-f62396ef2940)

## Overview
There are three modes:
- Live Mode: Displays the live webcam feed.
- Capture Mode: Allows you to select a gesture and record frames for that gesture.
- Live Recognition Mode: Recognizes and displays sign language gestures in real-time.
## Controls
Q / Esc: Exit the program.  
R: Start recording keypoint data for training new gestures.  
Spacebar: Start live sign language recognition (ensure the model is loaded first).  
N: Return to plain live feed mode.  
B: Delete the last letter from the recognized sentence.  
S: Start a countdown and record frames for a new gesture.  

# How to use
### Recording samples
By pressing `R`, you are prompted with a window where you can choose an existing class from a drop down menu, or type in the name of a new one.  
After selecting the sign, you can press `S` to start recording the sample. You have one second countdown to get in position, and then 30 frames of video are recorded, processed, and saved.

### Train new model / Load model
By clicking the `Train updated model and save it`, you start training the model with default settings on all samples of the current dataset (located in MP_data folder).  
By clicking the `Load model` button, you are prompted to choose from pre-trained models (from the Saved Models folder) to start recognition.

### Live recognition
By clicking `space` (after already loading a model), you enter the Live recognition mode.  
The app utilizes MediaPipe's hand and pose tracking to extract keypoints from the user's hands and pose. These keypoints are used as input to the model to predict the sign language gesture. The recognition results are then displayed on the screen.
A probability visualization is displayed on the left for the top 5 predictions, indicating the likelihood of each gesture. At the top is a list of signs recognized. You can press B to delete the last sign recognized from that list, or press the button Clear to delete the whole list.


![Live recognition](https://github.com/user-attachments/assets/923a037b-7a0f-4dc1-aacd-986f27efbda2)

