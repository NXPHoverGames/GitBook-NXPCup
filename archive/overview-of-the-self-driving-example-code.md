# Overview of the self-driving example code \[PX4]

## Quick guide

### Function overview

Inside the NXP Gazebo stack, there is a pre-determined function for self-driving code that gets called upon by the NXP Cup scheduled work item. That function is `roverControl raceTrack(const pixy_vector_s &pixy)` inside of `nxpcup_race.cpp`.

### Data structures and variables

The `pixy_vector_s` data structure is outlined in a uORB topic definition within the PX4 firmware. Here is the contents of that uORB topic: 

```
uint64 timestamp
# Vector 0 head and tail points
uint8 m0_x0    # Tail of vector @ x
uint8 m0_y0    # Tail of vector @ y
uint8 m0_x1    # Head of vector @ x
uint8 m0_y1    # Head of vector @ y

# Vector 1 head and tail points
uint8 m1_x0    # Tail of vector @ x
uint8 m1_y0    # Tail of vector @ y
uint8 m1_x1    # Head of vector @ x
uint8 m1_y1    # Head of vector @ y
```

This data structure contains the head and tail points of two vectors from the simulated pixy camera as well as a timestamp. You will just need to use the `uint8` points from this data structure to write your self-driving code. 

In the example code provided, we create two `Vector` variables and store the data from the `pixy` argument in the function. To do this we provide a function called `Vector copy_vectors(const pixy_vector_s &pixy, uint8_t num)` to perform this copy. You can see this at lines 74 and 75:

```
Vector vec1 = copy_vectors(pixy, 1);
Vector vec2 = copy_vectors(pixy, 2);
```

The Vector data structure is outlined in `nxpcup_race.h` and is as follows:

```
struct Vector
{
	void print()
	{
		char buf[64];
		sprintf(buf, "vector: (%d %d) (%d %d)", m_x0, m_y0, m_x1, m_y1);
		printf(buf);
		printf("\n");
	}

	uint8_t m_x0;
	uint8_t m_y0;
	uint8_t m_x1;
	uint8_t m_y1;
};
```

The data structure contains `uint8_t` variables for the head and tail points of a vector (or line segment). This is the same way that the real pixy camera presents line data, so your existing self-driving code should be compatible. The Vector struct also contains a print statement for debugging purposes.

Once we have copied vector data into the `Vector` data structure, we initialize some variables such as `frameHeight`, `frameWidth`, and `window_center`. These variables are for calculating steering angle, and we will go over that later in this guide.

Next, we create a data structure with the type `roverControl`. This type is as follows:

```
struct roverControl {
	float steer;
	float speed;
};
```

This structure is very simple - just speed and steer. You will use your self-driving algorithms to apply a torque and steering angle to the car using this structure. The `nxpcup_work.cpp` file uses this data to set an attitude setpoint within PX4. 

Some other variables are `hrt_absolute_time`, `time_diff`, `first_call`, and `num_vectors`. Descriptions of these variables are below:

`hrt_absolute_time` is the absolute timer value within PX4. This is used for stopping the car when no vectors are found.

`time_diff` is also used for stopping the car when no vectors are found.

`first_call` is used when no vectors are found to start the timer.

`num_vectors` is used to determine what algorithm to use. A function called `uint8t get_num_vectors(Vector &vec1, Vector &vec2)` returns the number of vectors that the simulated Pixy camera is publishing. Vector data defaults to 0s if no vector data is found, and the vector data is filled in sequentially as vectors are found. 

### Switch statement

The switch statement within `nxpcup_race.cpp` performs different instructions depending on how many vectors are found. 

#### Case 0

If no vectors are found (case 0), then a timer will start and tell the vehicle to stop after 10000 usec. 

#### Case 2

If two vectors are found, then the example algorithm will find the offset in the x direction of the average of the two head points of each vector. This will give us a steering value that will steer the cup car in the correct direction. This value is stored in `control.steer`. The speed value will get set to `SPEED_FAST` as configured in `nxpcup_race.h`. This value is stored in `control.speed`.

#### default

If one vector is found, the case will switch to default. The default case finds the gradient of the vector and stores that in `control.steer`, and the `control.speed` value will be set to `SPEED_NORMAL`. 

### Return

Finally, the `control` variable will be returned for use in `nxpcup_work.cpp`.
