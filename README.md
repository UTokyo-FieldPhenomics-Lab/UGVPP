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

### Hot to setup?
First, get [OpenKAI](https://github.com/yankailab/OpenKAI) for the on-board computer (NVIDIA Jetson series).

```
git clone https://github.com/yankailab/OpenKAI.git
```

Then copy the setting file `config/apRover_KU.kiss` to `OpenKAI/kiss/app/` by

```
cp UGVPP/config/apRover_KU.kiss OpenKAI/kiss/app/
```

To execute setup of OpenKAI, run the following. Necessary packages, including the one needed to recognize fiduciary markers, are automatically installed. Note that this process requires internet connection.

```
OpenKAI/sh/Setup/OpenKAI_dev_setup.sh
```

When you encounter an error in this step, edit `OpenKAI_dev_setup.sh` and remove steps that are commented as "optional", except you have to keep "Chilitag" section and sections above it for marker recognition. Nonetheless, it may be helpful to remove all optional sections and try installing. Also, to pinpoint the issue, copy commands from `OpenKAI_dev_setup.sh` and run them on your terminal one by one.





## Contributors
Ken Kuroki & Wei Guo
International Field Phenomics Research Laboratory, The University of Tokyo, Tokyo, Japan
