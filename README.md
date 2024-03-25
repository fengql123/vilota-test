### Task 1
##### Part a
It was quite interesting to learn about some applications of linear algebra in computer vision. I tried to create a spiral path of an object.

##### Part b
The open3d library was quite new to me so I took some time to learn about the functionalities. Overall, I used information that was provided to me to create a simple wireframe of the camera (looks exactly like the one in the video) and then created a simple animation of it rotating about its endpoint. I did not have time to explore more on the animation and open3d as these 2 weeks are my exam weeks (mid term). Nonetheless, It is always interesting to learn about new tools and technology.

### Task 3
##### Implementing the algorithm
1. Convert Pixel Coordinates to Normalized Coordinates (Mainly because have to consider focal lengths and the optical center, the paper assumed that the coordinates are normalized)
2. Compute the radial distance `r` from the optical center in this normalized coordinate system
3. Calculate theta using the polynomial formula mentioned in the paper (I used the opencv one as the result looks better, my understanding is that a polynomial will output a curve using the theta, hence looking like an output of fisheye)
4. Calculate distorted points using `theta` and `r`
5. Project them back as pixels