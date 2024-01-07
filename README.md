# 5056-MAXSwerve-LabVIEW
## Preliminary Information
This will not include any robot-specific code, so it should require only minimal effort to tune to your setup, assuming that you are also using Spark MAX controllers, NEO/550 motors, and an IMU.
With that being said, **I will not be generalizing the code**, so pay careful attention to a few things:

## Build Destination Directory
This will probably still be set to our local user. If you don't edit this (right click FRC Robot Boot-up Deployment under Build Specifications) you will error out when attempting to build the program.

### Libraries
This project uses the [CTRE](https://github.com/CrossTheRoadElec/Phoenix-Releases/releases) (There have been some changes to the Phoenix framework, and idk if LabVIEW is supported anymore), [REV Robotics](https://docs.revrobotics.com/sparkmax/software-resources/spark-max-api-information#labview), and [navX](https://pdocs.kauailabs.com/navx-mxp/software/roborio-libraries/labview/) repositories, not to mention the base FRC suite. Please ensure these are installed to prevent any suicidal tendencies.

### MHZLib
I would hope it isn't a problem since it's in the base directory, but ensure that all the auto-populating folders are, in fact, auto populating. If correct, it should look like this:

![This is an example of what your lvproj file should look like:](/image.png)

Note the custom MHZLib VIs! A lot of these are simply for cleanliness, like the Drive and Steer initialize VIs.

### Target
Pretty sure your team number isn't 5056, so you should *probably* change the target address... or don't. I can't tell you what to do.

### We use dashboard values!
I will try to document what exactly is being read from the dashboard, and I may eventually just add the DB to the project, but just so you know there are some values that will be overridden by their DB Read default. Make sure you bypass or change this if you don't use DB values!

### Check the controller mappings
Some controllers' axis indexes can vary. This code only accounts for a Dualshock 4 or Xbox One controller, so remap those as needed.

## Concluding Thoughts
I rammed my head into a desk for 3 months straight over this, hopefully I can save someone else the trouble.

You might see some loop timing errors in the logs of the DS. If you're concerned you can turn the main Periodic Tasks wait time (ms) up, but in my experience this issue will go away once the code is compiled instead of running real-time. If you increase that wait time too far, the math is unable to keep up with the rotation of the robot during a strafe, and there will be a *very* noticeable drift. I also would like to note that nearly all the programming I've done is in Begin or Periodic Tasks.

**Happy Programming!**
