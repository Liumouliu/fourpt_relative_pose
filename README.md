# Robust and efficient relative pose with a multi-camera system for autonomous driving in highly dynamic environments

This contains a 4-point relative pose solver described in : [Robust and efficient relative pose with a multi-camera system for autonomous driving in highly dynamic environments](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8053815)


The code can be integrated into the OpenGV lib without much effort.

To adapt to the interface provided by OpenGV lib, the rotation matrix provided by OpenGV store the euler angles:

<pre>

Matrix3d rotation = adapter.getR12();

// three euler angles at frame 0

double pitch1 = rotation(0,0);
double roll1 = rotation(0,1);
double yaw1 = rotation(0,2);

// three euler angles at frame 1

double pitch2 = rotation(1,0);
double roll2 = rotation(1,1);
double yaw2 = rotation(1,2);

<pre>

Although our method only use roll and pitch angles (vertical direction), for IMU with high quality (that means the yaw angle is accurate, too), you can input the yaw angle, otherwise, set it to 0.

Note: 
-  the code works fine if the relative rotation angle is under 5 degrees.

-  If only intra-camera feature correspondences are used, the scale of translation cannot be recovered, however, it makes our method robust to high dynamic scene (seeing our paper). So, if you want to achieve the two goals simultaneously, please intergrate the Acc. from IMU or use extra inter-camera correspondences if the FoVs of your camera configuration overlap.

