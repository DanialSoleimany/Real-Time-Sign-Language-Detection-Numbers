# Real-Time Sign Language Detection For Numbers From 0 to 9

## Overview
This project demonstrates real-time detection of sign language numbers (0-9) using hand gestures. The detection system utilizes a webcam to capture hand gestures, employs MediaPipe for hand pose estimation, and then predicts the corresponding number using a trained machine learning model (Random Forest). The model can accurately predict the numbers based on the hand landmarks' positions.

<p align="center">
  <b>Sign Language Numbers (0-9)</b>
</p>

<p align="center">
  <img src="https://github.com/DanialSoleimany/Real-Time-Sign-Language-Detection-Numbers/blob/main/0-to-9.jpg" alt="Sign Language Numbers">
</p>

<p align="center">––––––––––––––––––––––––––––––––––––––––––––</p>

<p align="center">
  <b>Demo Video</b>
</p>

<p align="center">
  <a href="https://youtu.be/Krw_WpgB-X8">
    <img src="https://img.youtube.com/vi/Krw_WpgB-X8/0.jpg" alt="Watch the video" />
  </a>
</p>

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

One of the main challenges in creating the dataset was ensuring accurate predictions for different hand orientations, distances from the webcam, and positions in the frame. I handled this challenge by capturing diverse images in various conditions, but the model's accuracy can still improve with more frames at different distances and positions.

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
