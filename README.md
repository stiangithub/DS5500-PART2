# DS5500-PART2

Summary

In this project, we are gonna explore a problem regarding on autonomous driving. Self-driving cars have been introduced since years ago and receives a lot attentions. So far the performance of self-driving cars is still not satisfactory enough. Consumers and lawmakers remain wary of adoption, in part because of doubts about vehicles’ ability to accurately perceive objects in traffic.

Baidu is a leading company in autonomous driving. Baidu's Robotics and Autonomous Driving Library (RAL), along with Peking University, hopes to close the gap of accurately identifying objects. They’re providing a dataset[1] with more than 60,000 labeled 3D car instances from 5,277 real-world images, based on industry-grade CAD car models.

Our goal is to implement algorithms to detect other cars and then estimate the absolute pose of vehicles from a single image in a real-world traffic environment.





Proposed plan

Baidu has put the dataset on Kaggle so that we can acquire the dataset easily. The next step is to understand what are in the dataset. This dataset contains photos of streets, taken from the roof of a car. We will attempt to predict the position and orientation of all unmasked cars in the test images. The primary data is images of cars and related pose information. The pose information is formatted as strings, as follows: model type, yaw, pitch, roll, x, y, z.

3D car models are provided, of all cars of interest are available for download as pickle files - they can be compared against cars in images, used as references for rotation, etc.

There are several challenges we have encountered: Transform image data to road  coordinates and the large amount of time to training the image. Most successful object detection algorithms enumerate a nearly exhaustive list of potential object locations and classify each due to the nature of image data. Such kinds of algorithms tend to give good end result but are inefficient and typically require a large amount of computational resource. In this project, instead of exhaustively classify all potential cars we would implement a center net model which is treat an object as a single point — the center point of its bounding box and then estimate the bounding as a regression problem. We imagine this approach would be much faster and in sufficient to detect and estimate the position of cars.
