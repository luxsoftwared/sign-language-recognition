# sign-language-recognition

This project is a python app for sign language recognition. App has three independent main functionalities:  
* **Making or expanding Datasets**  
Using Googles Mediapipe solutions for identifying face and body landmarks, landmarks are extracted from camera feed, transformed and formatted, and saved locally. This can be used to make new datasets from scratch, or to improve existing datasets by either recording more instances for existing signs, or by creating a new class(new sign to be recognized) and recording samples for it.

* **Training and evaluating models**  
Using keras library for building and training neural networks, sequential model is formed with 6 layers - 3 dense layers, and 3 LSTM layers. Recurrent neural network is used because it enables easier detection of signs that are dynamic(have movement incorporated), because the app was made with Serbian sign language in mind, which has a lot of dynamic signs. It can still be used for other sign languages, even static ones, but for them it would have slower performance than some other model would have. 
Evaluation and tracking of models is done using sklearn.metrics library and TensorBoard, by examining values for recall, precision, accuracy and F1 scores, and confusion matrix.

* **Recognition**  
In recognition mode, existing trained models can be loaded, and app turns on the camera and starts detecting and displaying signs from the live camera feed.
