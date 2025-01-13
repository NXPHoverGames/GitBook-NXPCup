# NXP Cup Example Application

## Reading the example code

The example code in the PX4 repository you cloned on the last page is located at `PX4-Autopilot/src/examples/nxpcup/`. The only file you should have to edit is `nxpcup_race.cpp`. This file contains the raceTrack() function, which is where your self-driving algorithm code should live. You can use the pixy\__vector\__&#x73; structure to write your algorithms. The structure is as follows:

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

You will use this data to populate the roverControl control{} structure which contains steer and speed values. The steer value is rad/s, and the speed value is m/s. This structure is returned in the raceTrack function and is used in the nxpcup\_work.cpp file to control the rover. The nxpcu&#x70;_\__&#x77;ork file should not be edited.

## Running the example code

On the previous page, you flashed the PX4 software to your rover and set it up in QGroundControl. In the software you downloaded, there are two example applications for driving the MR-Buggy3 around a NXP Cup track. One is called `pixy_uorb`, and the other is called `nxpcup_work`. `pixy_uorb` uses the standard Pixy driver to publish Pixy vector data to uORB, the publish/subscribe protocol in PX4. This data is subscribed to by `nxpcup_work`, the application that tells the Buggy3 how to drive around the track using the Pixy data. To run this code, you can open QGroundControl and navigate to the Q logo -> Analyze Tools -> Mavlink Console and run:

```
nsh> pixy_uorb start
nsh> nxpcup_work start
```

Your car should start driving on the track by recognizing the two outer lines.
