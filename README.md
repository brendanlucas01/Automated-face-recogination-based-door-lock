# Raspberry Pi Based Smart Door Lock with Face Recognition, RFID, and Google Assistant

This project implements a smart door lock system that uses deep learning for face recognition, with additional unlocking methods including RFID and Google Assistant. The system is designed to be lightweight and efficient, making it suitable for deployment on a Raspberry Pi. The unlocking mechanism is controlled by a servo motor.

## Features

- **Face Recognition:** Utilizes a lightweight deep learning model to recognize authorized users.
- **RFID Unlock:** Allows unlocking the door using an RFID card or tag.
- **Google Assistant Integration:** Enables voice-controlled unlocking via Google Assistant.
- **Servo Motor Control:** A servo motor is used to physically lock and unlock the door.
- **Raspberry Pi Deployment:** The entire system is designed to run on a Raspberry Pi, making it a cost-effective and compact solution.

## How it Works

The face recognition process is divided into three main stages:

1.  **Face Detection:** The system uses a Multi-Task Cascaded Convolutional Neural Network (MTCNN) to detect and extract faces from the camera feed. The `MTCNN_Face_Extration.ipynb` notebook is used to process the training images and extract faces.

2.  **Face Embedding:** The extracted faces are then passed through a FaceNet model, which is a deep convolutional neural network that has been trained to map faces to a 128-dimensional Euclidean space. The `FaceNet_face_embedings.ipynb` notebook is used to generate these embeddings from the extracted faces.

3.  **Face Classification:** The 128-d embeddings are then used to train a Support Vector Machine (SVM) classifier. The trained SVM model is used to recognize and classify the faces in real-time. The `face_recoginize_mtcnn.py` script uses the trained model to perform the final face recognition.

## Usage

To use this project, you will need to install the following dependencies:

-   TensorFlow
-   Keras
-   scikit-learn
-   OpenCV
-   MTCNN
-   Jupyter Notebook

You can install these dependencies using pip:

```bash
pip install tensorflow keras scikit-learn opencv-python mtcnn jupyter
```

The Jupyter notebooks are used for training the face recognition model:

-   `MTCNN_Face_Extration.ipynb`: Use this notebook to extract faces from your training images.
-   `FaceNet_face_embedings.ipynb`: Use this notebook to generate the 128-d face embeddings.

Once you have trained your model, you can run the real-time face recognition script:

```bash
python face_recoginize_mtcnn.py
```

## Hardware

The following hardware components are required for this project:

-   Raspberry Pi (3B+ or newer recommended)
-   Raspberry Pi Camera Module
-   Servo Motor
-   RFID Reader
-   Breadboard and jumper wires

## Future Improvements

-   **Liveness Detection:** Implement a liveness detection mechanism to prevent spoofing attacks using photos or videos.
-   **Mobile Application:** Develop a mobile application for remote control, user management, and real-time notifications.
-   **Improved Model Accuracy:** Experiment with different face recognition models or fine-tune the existing model to improve accuracy.
-   **Smart Home Integration:** Integrate the smart door lock with other smart home platforms like Home Assistant or Amazon Alexa.