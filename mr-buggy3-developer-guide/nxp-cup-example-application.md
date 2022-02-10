# NXP Cup Example Application

## Running the example code

On the previous page, you flashed the PX4 software to your rover and set it up in QGroundControl. In the software you downloaded, there are two example applications for driving the MR-Buggy3 around a NXP Cup track. One is called `pixy_uorb`, and the other is called `nxpcup_work`. `pixy_uorb` uses the standard Pixy driver to publish Pixy vector data to uORB, the publish/subscribe protocol in PX4. This data is subscribed to by `nxpcup_work`, the application that tells the Buggy3 how to drive around the track using the Pixy data. To run this code, you can open QGroundControl and navigate to the Q logo -> Analyze Tools -> Mavlink Console and run:

```
nsh> pixy_uorb start
nsh> nxpcup_work start
```

Your car should start driving on the track by recognizing the two outer lines.
