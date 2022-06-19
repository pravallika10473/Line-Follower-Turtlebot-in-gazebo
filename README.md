# Line Follower Turtlebot in gazebo
Turtlebot waffle follows a custom build line in gazebo
![snapshot](https://user-images.githubusercontent.com/68220390/174467984-efb12d9f-8402-4ebf-97a4-ab887dbde2f9.png)

# Overview
This project uses ROS noetic to demonstrate a simple line following Turtlebot in a simulated Gazebo environment . Line following is an easy to design application for a robot as all it requires is a robot with a camera and some tape. These robots can be made to follow these paths in periodic intervals autonomously and hence automate the function of the entire material handling system in a highly cost efficient way.
# Implementation
In this project , a turtlebot is launched into a gazebo line world as above. follower node subscribed to an image topic called /camera/rgb/image_raw which publishes the image data of turtlebot camera .As ROS passes around images in its own sensor_msgs/Image message format, CvBridge is used to convert into bgr format. Then the image is converted to HSV format which can be used for color thresholding.

