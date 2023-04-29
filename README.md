# SLDL: Canny Edge Decorder
<br>
A embedded system level Canny Edge Decorder that can detect the edges on a wide range of objects with multi-stage algorithm.
<br>
## Description
<br>
This project involves implementing the Canny Edge Decoder in a SystemC-based SoC architecture. The goal is to demonstrate proficiency in system-level design using high-level modeling languages. The final deliverable will be a working implementation of the decoder with simulation and valuation results.
<br>
## Project Outcomes
The final deliverable of this project is a working implementation of the Canny Edge Decoder, with simulation and verification results that demonstrate its performance and accuracy. The implementation includes a pipeline architecture that allows for efficient processing of large images, and a memory management system that minimizes memory usage and maximizes throughput.
<br>
## Code Attribution
This project includes code from the following sources:
<br>
http://www.eng.usf.edu/cvprg/edge/edge_detection.html
Original Canny Edge Decoder implementation by Heath, M., Sarkar, S., Sanocki, T., and Bowyer, K., licensed under the USF license.
<br>
## Dependencies
<br>
Before installing and running this program, you will need to have the following dependencies installed:
* SystemC 2.3.1
<br>
You can download and install SystemC from the official website at http://www.accellera.org/downloads/standards/systemc. Once you have installed SystemC, make sure that the SYSTEMC_HOME environment variable is set to the installation directory.
<br>
This program has been tested and verified to work on the following operating systems:
* Ubuntu 20.04 LTS
* Windows 10
<br>
## Version History
<br>
* 0.6
    **Throughput optimization of the Canny Edge Decoder**
    * Trade-off between accuracy and speed
    Replace floating-point arithmetic with fixed-point calculations
<br>
* 0.5 
    **Pipelining and parallelization of the Canny Edge Decoder**
    * Slice the BlurX and BlurY blocks into parallel components
    DUT<br> 
    |------ Gaussian_Smooth gaussian_smooth<br> 
    | \\------ Gaussian_Kernel gauss<br> 
    |------ BlurX blurX <br>
    | |------ BlurX_Slice sliceX1 <br>
    | |------ BlurX_Slice sliceX2 <br>
    | |------ BlurX_Slice sliceX3 <br>
    | |------ BlurX_Slice sliceX4 <br>
    | |------ BlurX_Slice sliceX5 <br>
    | |------ BlurX_Slice sliceX6 <br>
    | |------ BlurX_Slice sliceX7 <br>
    | \\------ BlurX_Slice sliceX8 <br>
    |------ BlurY blurY <br>
    | |------ BlurY_Slice sliceY1 <br>
    | |------ BlurY_Slice sliceY2 <br>
    | |------ BlurY_Slice sliceY3 <br>
    | | [\...] <br>
    | \\------ BlurY_Slice sliceY8 <br> 
    |------ Derivative_X_Y derivative_x_y <br>
    |------ Magnitude_X_Y magnitude_x_y <br>
    |------ Non_Max_Supp non_max_supp <br>
    \\------ Apply_Hysteresis apply_hysteresis <br> 
<br>
* 0.4
    **Hierarchical DUT model of the Canny Edge Decoder**
    DUT canny <br>
    |------ Gaussian_Smooth gaussian_smooth <br> 
    | |------ Gaussian_Kernel gauss <br>
    | |------ BlurX blurX <br>
    | \\------ BlurY blurY <br>
    |------ Derivative_X_Y derivative_x_y <br>
    |------ Magnitude_X_Y magnitude_x_y <br>
    |------ Non_Max_Supp non_max_supp <br>
    \\------ Apply_Hysteresis apply_hysteresis <br>
<br>
* 0.3
    **Structural test bench model of the Canny Edge Decoder**
    Main / Top <br>
    |------ Stimulus stimulus <br>
    |------ Platform platform <br>
    | |------ DataIn din <br>
    | |------ DUT canny <br>
    | \\------ DataOut dout <br>
    \\------ Monitor monitor <br>
<br>
* 0.2
    **Initial SLDL Model of the Canny Edge Decoder**
    * Remove or replace all remaining dynamic memory allocation
    *Avoid Fragmentation*
    Embedded systems can run for years, Using dynamic memory can cause a severe waste of memory due to fragmentation.
    *Predictability*
    By using static memory allocation or pre-allocated memory pools, we can ensure that the amount of memory used is predictable and consistent, allowing for better resource management and system performance.
    *Efficiency*
    By using static memory allocation or pre-allocated memory pools, we can improve system efficiency and speed.
    *Reliability*
    By replacing dynamic memory allocation with static or pre-allocated memory, we can reduce the risk of such errors and improve the reliability of the system.
<br>
* 0.1
    **Bug fix in "non_max_supp" function** <br>
    A column of pixels at the right and a row of pixels at the bottom are not included in 
    the computation. Change the for loop end condition.
<br>
## Results
<br>
**Photo Result** 
* Original Photo
![orig](/Image/EngPlaza001.pgm.png)
* Canny Edge Result
![canny](/Image/EngPlaza001_edges.pgm.png)
<br>
<br>
**Throughput Optimization**
![canny](/Image/throughput_optimization.png)
