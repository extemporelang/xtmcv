# XTMCV

A small C wrapper for OpenCV 4 designed primarily for binding to Extempore.

## Prerequisites

You will need to build (statically) opencv 4.
Make sure you also do the install step 
You should end up with a directory with
libs and include.

At the time of writing this readme this was
expected to look something like:

### On Windows
install/include/opencv2
install/x64/vc15/staticlib

### On OSX ??

## Building

You need to provide the path (CV4_DIR) to the opencv build install directory.

### Windows example
cmake -A x64 -D CV4_DIR:PATH="D:/Downloads/opencv-4.0.1/build/install" ../
cmake --build . --config Release

## THANKS

This project was bootstrapped by pilfering parts of the GoCV project.
https://github.com/hybridgroup/gocv/blob/master/README.md

## License

Licensed under the Apache 2.0 license.
