# ULOG file
ULOG format: Sometimes, it’s helpful to have very verbose output regarding the internal workings of the PX4 flight control system. After catastrophic landings (crashes) the ULOG files provide a type of “black box” permitting post-crash diagnostics. Separate from ROS1/ROS2, and not limited only to ModalAI hardware, there is a method of logging mavlink messages generated as μORB topics in the flight stack. As an aside, the Ardupilot flight stack has a comparable feature. On older autopilots, such as the Pixhawk
Cube, a 4,8, or 16 GB SD card is placed directly in the autopilot to capture such logs. Generally, a log is created every time you arm the system, for both real and simulated setups. 

### Locating ULOG file
Now, with our setups, for simulated vehicles the default log location is:

```
PX4-Autopilot/build/px4 sitl default/rootfs/log/<date>/<time>.ulg,
```

and here for the real modalai vehicles:
```
/data/px4/log/<date>/<time>.ulg
```
Read here for an overview: https://docs.px4.io/main/en/dev log/ulog file format.html. 

### PX4-Flight Review
There is a method of displaying this collected data as well, known as “Flight Review”: https://github.com/modalai/px4-
flight-review. 

### Pyulog
You can break ULOG files out into individual .csv files using pyulog (’pip install pyulog’ on your host machine). Also, here’s the source code: https://github.com/PX4/pyulog

### Plotjuggler
You can also use an aaplication named plotjuggler (https://index.ros.org/p/plotjuggler/)
to plot all types of log files, including ROSbags and Ulogs. You can also convert these files to csv format and could also replay this files alike pusblihing on the topic at a real time. You can also subcribe to the topics which are puslishing at a real time and you can plot graph of them as well. This is really handy tool and you should look into this as well.

### Controlling what should be logged
You should be able to find the “SDLOG” parameters from QGC-Tools which control which topics are saved to the ULOG file. A complete parameter reference is here:
https://docs.px4.io/main/en/advanced config/parameter reference.html

## About this repository

I have uploaded here a sample ulog file and I have also shared my python jupyter notebook where I have used pyulog library to open the ulog file and plotted graphs of the desired parameters.


Here I wanted to plot graphs of 
1. Euler angles
2. Velocities in all axis
3. Position in all axis