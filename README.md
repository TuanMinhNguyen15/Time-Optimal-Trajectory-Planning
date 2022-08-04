# Time-Optimal Trajectory Planning
The trajectory planner is divided into 3 layers. The first layer takes in the x- & y-coordinates of the middle track line and then optimizes the track using the Convex Elastic Smoothing (CES) algorithm which takes into account the mobile robot's minimum turning radius to output the shortest and kinematically feasible track. In the second layer, the time-optimal trajectory planning along that optimized track (from layer 1) is formulated as a Second Order Convex Cone Programe (SOCP) whose outputs are the required velocities in x- & y-direction e.g. $vx$ and $vy$ such that the robot is driven to the goal point as quickly as possible while satisfying actuation limits. To determine the required longitudinal velocies $(v)$ and steering angles $(\phi)$ that can feasibly drive the robot to closely match the desired vx and vy , the third layer formulates the robot's inverse kinematics model and its velocity and steering constraints into a linear program (LP). 

The robot control limits are:

$0 \le v \le 1$

$-\pi/3 \le \phi \le \pi/3$

## Original Tracks
### Square Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/square.png)
### Double-Squares Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/double_square.png)
### Star Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/star.png)

## Optimized Tracks (Layer 1)
### Square Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/optimized_square.png)
### Double-Squares Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/optimized_double_square.png)
### Star Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/optimized_star.png)

## Optimized Controls (Layer 2)
The optmized track is then parametrized with respect to a "progress" parameter $s \in [0,1]$ where $s=0$ corresponds to the starting point and $s=1$ corresponds to the ending point.
### Square Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vx_square.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vy_square.png)
### Double-Squares Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vx_double_square.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vy_double_square.png)
### Star Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vx_star.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/controls_vy_star.png)

## Driving Mobile Robot (Layer 3)
A PID-controller is also integrated into the planner to minimize tracking errors caused by model mismatch, numerical inaccuracy, etc. To demonstrate the planner's robustness, the robot's starting position is offsetted from the planned starting position, and we can see that the robot will eventually converge to the planned trajectory. 
### Square Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_path_square.png)

![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_vel_square.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_steer_square.png)
### Double-Squares Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_path_double_square.png)

![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_vel_double_square.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_steer_double_square.png)
### Star Track
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_path_star.png)

![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_vel_star.png)
![alt text](https://github.com/TuanMinhNguyen15/Time-Optimal-Trajectory-Planning/raw/main/images/demo_steer_star.png)

## References
[Convex Elastic Smoothing](https://arxiv.org/abs/1506.01085)

[Time-Optimal Trajectory Planning Along Predefined Path](https://escholarship.org/uc/item/58r3063m)

[Inverse Kinematics Model of Car-like Robots - Chapter 13](http://hades.mech.northwestern.edu/index.php/Modern_Robotics)
