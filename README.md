# fourpt_relative_pose
Multi-camera relative pose estimation with vertical direction


This is the implementation of our work: **Robust and Efficient Relative Pose with a Multi-camera System for Autonomous Driving in Highly Dynamic Environments **.

Currently, the code can be integrated into** OpenGV **lib without much effort.

To adapt to the interface provided by ** OpenGV **lib, the rotation matrix provided by OpenGV store the euler angles:

Matrix3d rotation = adapter.getR12();

// three euler angles at frame 0

double pitch1 = rotation(0,0);
double roll1 = rotation(0,1);
double yaw1 = rotation(0,2);

// three euler angles at frame 1

double pitch2 = rotation(1,0);
double roll2 = rotation(1,1);
double yaw2 = rotation(1,2);

Although our method only use roll and pitch angles (vertical direction), for IMU with high quality (that means the yaw angle is accurate, too), you can input the yaw angle, otherwise, set it to 0.

Note: 
-  the code works fine if the relative rotation angle is under 5 degrees.

-  If only intra-camera feature correspondences are used, the scale of translation cannot be recovered, however, it makes our method robust to high dynamic scene (seeing our work). So, if you want to achieve the two goals simutanlously, please intergrate the Acc. from IMU or use extra inter-camera correspondences if the FoVs of your camera configuration overlap .

