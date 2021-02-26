# Known Issues

## Before you start..

We want to make sure that contestants are aware of potential bugs and/or issues in the NXP Gazebo simulation. Below we will keep an updated list of these issues. If an issue has been fixed, it will be checked off.

* [ ] Bug: Sometimes Gazebo will not start successfully and show an invisible box. **FIX: Restart the simulation.**
* [ ] Bug: Sometimes micrortps\_client does not start automatically in the PX4 shell. **FIX: Run \`micrortps\_client start -t UDP\` to start it. You can check the status of micrortps by running \`micrortps\_client status\`**
* [ ] Bug: Sometimes the micrortps\_agent will fail \(Segmentation fault\) **FIX: Restart the simulation.**
* [ ] Issue: The self-driving example code does not currently drive around the track successfully. **There is currently no fix for this. We suggest you use your own self-driving code, but the example is there to help you get started and to show that the car does indeed drive in simulation.**



