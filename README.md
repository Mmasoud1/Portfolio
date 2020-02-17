# SlideMasking Demo

Coded by: Mohamed Masoud <mmasoud@emory.edu> , 2019 <br>
<hr>

SlideMask Demo is a webix based interactive learning envirement to binary classify WSI regions of interest. It produces the heatmap and mask for the regoin of interests. It can run on local WSI or access remotely DSA images with OpenSeadragon.


![Webix Interface](https://github.com/Mmasoud1/SlideMask/blob/master/ShowMe/Slide1.png)



## Table of Contents
[User Guide](#user-guide)

1.    [Pre-Installations](#1.)  
2.    [Setup](#2.)  
3.    [Output](#3.)  
4.    [Run](#4.) 
5.    [Show me](#5.) 

## User Guide <a class ="anchor" id="user-guide"></a>

### 1. Pre-Installations <a class ="anchor" id="1."></a>

WSI_Mask may need update the following dependancies: <br>
````
   -grafi    (https://github.com/grafijs/grafi), 
             git clone git://github.com/grafijs/grafi.git
             
   -wheelzoom  git clone git://github.com/jackmoore/wheelzoom.git 

````
Also, access to DSA server is required.

### 2. Setup <a class ="anchor" id="2."></a>

For any WSI boundaries file generated copy it to `boundary/` folder in the main directory. For any features file created copy it to  `features/` folder. <br>
   

### 3. Output <a class ="anchor" id="3."></a>

All features saved in 'features/' folder with file name `{slideName}.{GridSize}.{ColorHistNum}` for grids boundaries, and `{slideName}.SPX.Num` for superpixels. The trained FNN model can be save as `{slideName}.{ColorHistNum}.FNN`

### 4. Run <a class ="anchor" id="4."></a>

To run, just start up both a local server from the root level of this repository:
````
python  -m SimpleHTTPServer 8xxx
````
Run flask app from the root level of this repository and install any dependencies needed:
````
python  features.py
````
Alternatively, for running the dockerized flask pull the docker as follows:
````
docker pull mmasoud2/wsi-masking:v1
````
After pulling, run this command from the terminal:
````
docker run --rm -p5555:5000 -v $(pwd)/:/output/:rw mmasoud2/wsi-masking:v1
````
If tcp  `0.0.0.0:5555 ` is in use, change `-pxxxx` to any available port. 

After entering `localhost:8000/WSI_Mask.html` in the browser, a prompt window will launch, enter the flask port such that:
````
  - For the decorizing version of flask enter port number:   5555  or the port number you use with -pxxxx
  Or
  - For python version enter port number :   3000
````
<br>

### 5. Show Me <a class ="anchor" id="5."></a>


![App Steps](https://github.com/Mmasoud1/SlideMask/blob/master/ShowMe/SlideMaskToShowSteps.gif)
