# Line Follower Turtlebot in gazebo
Turtlebot waffle follows a custom build line in gazebo
![snapshot](https://user-images.githubusercontent.com/68220390/174467984-efb12d9f-8402-4ebf-97a4-ab887dbde2f9.png)

# Overview
This project uses ROS noetic to demonstrate a simple line following Turtlebot in a simulated Gazebo environment . Line following is an easy to design application for a robot as all it requires is a robot with a camera and some tape. These robots can be made to follow these paths in periodic intervals autonomously and hence automate the function of the entire material handling system in a highly cost efficient way.
# Implementation
In this project , a turtlebot is launched into a gazebo line world as above. follower node subscribed to an image topic called /camera/rgb/image_raw which publishes the image data of turtlebot camera .As ROS passes around images in its own sensor_msgs/Image message format, CvBridge is used to convert into bgr format.Filtering on RGB values turns out to be a surprisingly poor way to find a particular color in an image, since the raw RGB values are a function of the overall brightness as well as the color of the object.Slightly different lighting conditions would result in the filter failing to perform as intended. Instead, a better technique for filtering by color is to transform RGB images into HSV images.We can then apply a threshold for hues near yellow to obtain a binary image in which pixels are either true (meaning they pass the filter) or false (they do not pass the filter).Then, we will use the OpenCV moments() function to calculate the centre of the blob of the binary image that passes our filter. To follow the detected line Proportional Controller(P-Controller) is used ,the error signal is the distance between the centerline of the image and the center of the line we are trying to follow.The velocity commands are send via topic /cmd_vel to the turtlebot.
# Dependencies
* ROS Noetic
* Gazebo
* Catkin
* rospy package
* sensor_msgs package
* geometry_msgs package
* OpenCV
* numpy
