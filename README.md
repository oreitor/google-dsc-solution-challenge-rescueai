# Google Developer Student Clubs Solution Challange 2021 | RescueAI

This page related to RescueAI project prepared for Solution Challenge 2021 organized by Google Developer Student Clubs.

The purpose is to contribute to the [*Sustainable Development Goals*](https://sdgs.un.org/goals) announced by the United Nations with the RescueAI solutions which we developed using Google technologies. This project is about Reducing the *Negative Effects of Natural Disasters (Target 11.5)* under the title of *Sustainable Cities and Communities (Goal 11)*.

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/RescueAI.png">
</p>

The main goal determined for RescueAI is to make the search-rescue and emergency response processes after a natural disaster more effective with Artificial Intelligence, Computer Vision and Mobile Application solutions.

#### Google Technologies
* TensorFlow
* Earth Engine Apps
* Flutter
* Maps Platform API's

### Deep Learning with TensorFlow
Thanks to Artificial Intelligence and Computer Vision methods, it was requested to provide damage detection, status information or suggestions autonomously on the disaster area with instant satellite images or drone.

#### Dataset for Deep Learning Model Testing
In this stage, RescueAI can determine high accuracy whether buildings are Damaged or Normal with TensorFlow using the image data obtained from Google Earth Engine Apps. Natural disaster in Sint-Maarten, an island country in the Caribbean, has been chosen to serve as an exemplary case for testing RescueAI algorithm. This island was severely damaged by Hurricane Irma, Category 5, on September 6, 2017, and hundreds of houses were destroyed. In the following images taken from Google Earth Engine Apps, the disaster situation of the region examined before and after the hurricane is indicated.

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/before-disaster.jpg"><br /><span>Before Hurricane</span>
</p>

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/after-disaster.jpg"><br /><span>After Hurricane</span>
</p>

For the sample case model, 50 different houses damaged after the disaster were randomly selected in this area. As in the example below, a total of 100 selected houses before and after the disaster were collected in the [test_images](https://github.com/oreitor/google-hack-for-prosperity-hackathon/tree/main/test_images) folder and made ready to test the model.

<p align="center">
  <img width="200" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/test_images/a43.png"><span> &emsp;</span>
  <img width="200" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/test_images/b43.png">
</p>

#### Deep Learning Model and Parameters
Transfer Learning applications were preferred due to hardware limitations and the desire to create a professional deep learning model. With the trained Deep Learning model obtained from the scientific study encountered during the literature review, the process was accelerated with Transfer Learning through TensorFlow.

You can find detailed information about the scientific study titled *Structural Building Damage Detection with Deep Learning: Assessment of a State-of-the-Art CNN in Operational Conditions* [here](https://www.mdpi.com/2072-4292/11/23/2765/htm). For the RescueAI Deep Learning [model](https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/uav.rar), the model with a total of 2,336,725 parameters trained with the images taken by the Unmanned Aerial Vehicle in this study was preferred.

#### Test Result
Although the test accuracy of the model on the specified study is 90.8%, the accuracy rate of the test of 100 random images selected in this project is 81%. The reasons for the difference are related to the quality of the images taken on the map and the different positioning methods. Below is the Confusion Matrix regarding the test results from RescueAI's first model. With 0.8257, the F1 Score result is sufficient for now.

<p align="center">
  <img width="800" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/cm.PNG"><br /><span>Confusion Matrix</span>
</p>

<p align="center">
  <img width="800" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/cm_results.PNG"><br /><span>Confusion Matrix Result</span>
</p>

If we look at the random results taken from the test images prepared for the deep learning model as seen below, it is stated whether the 11 images selected out of 100 images are "Normal" or "Damaged". PC represents the Predicted Class and AC represents the Actual Class. Looking at the example, there is only 1 case of incorrect classification out of 11 images.

<p align="center">
  <img width="500" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/prediction.PNG"><br /><span>Test Result</span>
</p>

### Mobile Application with Flutter
Thanks to the Mobile Application Developed with Flutter, it is aimed that the teams in the disaster area can follow the situation instantly on the map. In addition, a simple, user-friendly RescueAI application has been designed in the region with main functions such as disaster information, support points, unmanned aerial vehicle information, communication network for teams, help request and status reporting. It is quite suitable for development with its side functions and AI solutions to be added. The design interfaces of the RescueAI brand are shown in the mock-up below.

The map used in the application was created using API's provided by Google Maps Platform.

<p align="center">
  <img width="1000" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/mockup.png"><span>RescueAI Mock-Up</span>
</p>
