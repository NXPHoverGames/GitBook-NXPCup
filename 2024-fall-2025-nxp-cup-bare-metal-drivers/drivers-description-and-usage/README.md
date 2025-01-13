# Drivers description and usage

To develop software for your car, we provide dedicated drivers for all the components listed. These drivers, located in the **`include`** and **`src`** folders, are built on top of the [Autosar ](https://en.wikipedia.org/wiki/AUTOSAR)Real-Time drivers, which can be found in the **`RTD`** folder. In this section, we will explain the car driver API in detail, including how to use and test each driver.

## Testing the car

Most drivers have a test function you can use to ensure everything is connected and working properly. You can find the test functions in the **main\_functions.c** file. After you validated everything, remove these functions from your code as they never return to main.

Note: Some test functions, like the Linear camera test, require a display.
