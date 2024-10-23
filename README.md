# Real-Time-Sign-Language-Detection-Numbers

## Overview
This project demonstrates real-time detection of sign language numbers (0-9) using hand gestures. The detection system utilizes a webcam to capture hand gestures, employs MediaPipe for hand pose estimation, and then predicts the corresponding number using a trained machine learning model (Random Forest). The model can accurately predict the numbers based on the hand landmarks' positions. For a demo, watch the video on [YouTube](https://studio.youtube.com/video/Krw_WpgB-X8/edit).

## Table of Contents
1. [Overview](#overview)
2. [Requirements](#requirements)
3. [Dataset](#dataset)
4. [Model](#model)
5. [Usage](#usage)
6. [License](#license)

## Requirements
Make sure you have the following dependencies installed:

- **Mediapipe**: `0.10.14`
- **OpenCV (cv2)**: `4.10.0`
- **Scikit-learn**: `1.5.2`

You can install them via pip:

```bash
pip install mediapipe==0.10.14 opencv-python==4.10.0 scikit-learn==1.5.2
```

## Dataset
I collected the dataset using my webcam, generating 1000 images for each class (numbers 0-9) using the `collect_images` module. Then, I processed these images with the `create_dataset` module to extract x and y coordinates from hand estimation landmarks. Each landmark array was labeled with the respective number and saved as a pickle file.

The complete dataset is around 6GB, so it's not uploaded here, but you can collect your own dataset using the aforementioned modules.

## Model
The machine learning model used is a Random Forest classifier, which achieved over 99% accuracy. The model was trained using the `train_classifier` module on the extracted coordinates from hand landmarks, and the trained model is saved as a `.p` file for future predictions.

## Usage
To use the system, run the `main.py` script. The script captures video from your webcam, uses MediaPipe for hand pose estimation, and passes the extracted landmarks' coordinates to the saved Random Forest model. The model predicts the number based on the hand gestures, displaying the result on a box around the hand.

```bash
python main.py
```

The system predicts numbers in real time, showing a number from 0-9 based on your hand gesture and position in each frame.

## License
This project is licensed under the MIT License. Feel free to use it in your projects or contribute to improve it.
