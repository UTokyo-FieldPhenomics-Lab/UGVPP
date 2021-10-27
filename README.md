# UGVPP

This repository contains supplementary files for the article "Development of a high-throughput field phenotyping rover optimized for size-limited breeding fields as open hardware" (in prep)

## Article
(to be added)

## Contents

### CAD
`cad/assembly.SLDASM` is a 3D CAD file of our field rover's geometry in [SolidWorks](https://www.solidworks.com/) assembly file format. It can be opened by free viewer software [eDrawings Viewer](https://www.edrawingsviewer.com/) 2021 as well as SolidWorks 2021. Files in `cad/parts/` are the components imported to the assembly file. The article also describes components used to assemble the robot.

### Configuration
`config/apRover_KU.kiss` is a [OpenKAI](https://github.com/yankailab/OpenKAI) config file we used for the field trial.

### Images
Files in `images/` are the images captured by the on-board cameras. They are from three cameras and can be used for 3D reconstruction with SfM software such as [COLMAP](https://colmap.github.io/) (open) and [Metashape](https://www.agisoft.com/) (commercial).

### How to setup?
First, get [OpenKAI](https://github.com/yankailab/OpenKAI) for the on-board computer (NVIDIA Jetson series). Log in to it from your computer via SSH (we used Ubuntu and its default terminal for this purpose, but you can use other environments as well).

```
git clone https://github.com/yankailab/OpenKAI.git
```

Then copy the setting file `config/apRover_KU.kiss` to `OpenKAI/kiss/app/` by

```
cp UGVPP/config/apRover_KU.kiss OpenKAI/kiss/app/
```

To execute setup of OpenKAI, run the commands in the following shellscript. Necessary packages, including the one needed to recognize fiduciary markers, are automatically installed. Note that this process requires internet connection. However, you should run the commands in the script on your terminal rather than directly executing the entire file. You have to reboot the computer several times during this process.

```
OpenKAI/sh/Setup/OpenKAI_dev_setup.sh
```

When you encounter an error in this, Omit steps that are commented as "optional", except you have to keep "Chilitag" section and sections immediately above it for marker recognition. Nonetheless, it may be helpful to remove all optional sections and try installing.

To run OpenKAI to start controlling the UGV, find

```
OpenKAI/ok.sh
```

This file contains the path to the config file. Open it and edit it to `config/apRover_KU.kiss` or some other name in case you renamed your setting file. After editing it as needed, reboot the computer and `ok.sh` is automatically run upon booting.

### Tuning
To help tuning the config parameters for your purpose, you can use `OpenKAI/sh/Setup/Gstreamer/gst.sh`. Note that this is to be used with your personal computer (preferably Ubuntu, but may work in other environments), not the on-board computer of the vehicle. Install [GStreamer](https://gstreamer.freedesktop.org/) first and then run `OpenKAI/sh/Setup/Gstreamer/gst.sh` when connnected to the on-board computer via network. You can see the input from the navigation camera and real-time marker detection results.

By default, the on-board computer is configured to run `ok.sh` upon booting. This may be inconvenient when you want to run it manually and configure parameters, because you have to restart `ok.sh` to reload the config file. In that case, rename it by `mv ok.sh ok_.sh` and run `ok_.sh` instead. This way, you can stop and re-run it as you like without rebooting the whole computer. Note that you must not run multiple instances of `ok.sh`, which causes overload to the computer and the responses will be delayed, leading to unexpected behaviors.

## Contributors
Ken Kuroki & Wei Guo
International Field Phenomics Research Laboratory, The University of Tokyo, Tokyo, Japan
