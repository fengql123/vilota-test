### Task 1
##### Part a
It was quite interesting to learn about some applications of linear algebra in computer vision. I tried to create a spiral path of an object.

##### Part b
The open3d library was quite new to me so I took some time to learn about the functionalities. Overall, I used information that was provided to me to create a simple wireframe of the camera (looks exactly like the one in the video) and then created a simple animation of it rotating about its endpoint. I did not have time to explore more on the animation and open3d as these 2 weeks are my exam weeks (mid term). Nonetheless, It is always interesting to learn about new tools and technology.

### Task 2
##### Key Learning Points
1. Robot pose on a plane (2D) can be represented by 2 values, `t` and `R`, representing the robot's coordinate on the plane and the direction that it's facing (amount of rotation clockwise/anti-clockwise) respectively
2. Bearing angle is the angle between the direction of robot and the target landmark
3. In order to obtain the (relative position) / (direction vector) of the landmark from the perspective of the robot, imagine translate robot back to (0, 0) and facing 90 degrees, then we have to translate the position of the landmark by the same as well, thus `landmark_body = pose.inverse() * landmark`
4. Next we can use trigo to obtain the bearing angle between landmark and robot
4. The optimization target is to obtain poses that minimize the bearing angle and the distance to 3 landmarks
5. Hence, there are two loss functions defined, one is calculating difference between robot's current bearing angle and target bearing angle, while the other is distance
6. Applying non-linear optimization algorithms on these two loss functions will result in what we want
7. We can see that by running the optimization algorithm, we have robots' optimal starting poses to travel to the 3 different landmarks

##### Some Thoughts
It is exciting for me to think about the possible applications by being able to calculate the relative position of an object to the robot itself. Robots will be able to know where are the obstacles hence being trained to be able to avoid it or able to go to a place and just grab some stuff. These applications are exactly my interested areas, It would be exciting for me to work on the data that the robots see/process, the algorithms applied on them, designing and optimizing a complicated software system.

### Task 3
##### Implementing the algorithm
1. Convert Pixel Coordinates to Normalized Coordinates (Mainly because have to consider focal lengths and the optical center, the paper assumed that the coordinates are normalized)
2. Compute the radial distance `r` from the optical center in this normalized coordinate system
3. Calculate theta using the polynomial formula mentioned in the paper (I used the opencv one as the result looks better, my understanding is that a polynomial will output a curve using the theta, hence looking like an output of fisheye)
4. Calculate distorted points using `theta` and `r`
5. Project them back as pixels