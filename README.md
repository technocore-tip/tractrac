# TracTrac PTV Software: a fast multi-object tracking algorithm for motion estimation

<div align="center">
<img src="http://perso.univ-rennes1.fr/joris.heyman/img/anim-1.gif" loop=infinite style="width:680px">
</div>

TracTrac is an open-source Matlab/Python implementation of a robust and efficient object tracking algorithm capable of simultaneously tracking several thousands of objects in very short time. Originally developed as an alternative to particle image velocimetry algorithms for estimating fluid flow velocities, its versatility and robustness makes it relevant to many other dynamic sceneries encountered in geophysics such as granular flows and drone videography. In this article, the structure of the algorithm is detailed and its capacity to resolve strongly variable and intermittent object motions is tested against three examples of geophysical interest.

TracTrac is a Particle Tracking Velocimetry (PTV) software which is fast (more than 10000 points tracked per second) and accurate (up to 0.01 pixel resolution), forming thus a good concurrent to the state-of-the art PIV algorithms. It allows to track anything that moves: birds, ants, grains, water flows... It runs on Python (v2.7/3.6 with OpenCV2) or Matlab (>2014a with Computer Vision and Statistics toolbox). Give it a try !


# Reference
TracTrac has been tested in the following reference:

Heyman J., TracTrac: A fast multi-object tracking algorithm for motion estimation, Computers & Geosciences, Volume 128, 2019, Pages 11-18,doi: 10.1016/j.cageo.2019.03.007

The article is available in <a href="https://perso.univ-rennes1.fr/joris.heyman/PDF/tractrac_final.pdf" > my personal webpage </a>

Contact: joris.heyman@univ-rennes1.fr 


# User guide Matlab
1) Installation 
Download and extract the Git repository. Make sure you have Matlab version >2014a with Image Processing Toolbox and Statistics and Machine Learning Toolbox installed.  

2) In the Matlab folder, run TracTrac Graphical User Interface with 
> tractrac 

# User guide Python2 and Python3
1) Installation
Download and extract the Git repository. Make sure you have a working installation of python2.7 or python3.xx. Install the extra packages scipy, opencv-python, imutils, h5py, parse via the terminal :
> pip install scipy opencv-python imutils h5py parse --user


2) In the Python folder, run test case, plot and save average velocities with
> python tractrac.py -p 1 -a

3) Get help on available commands with :
> python tractrac.py --help

4) Other sample cases may be run as
> python tractrac.py -f "../Sample_videos/videotest.avi" -p 1

or
> python tractrac.py -f "../Sample_videos/PIVChallenge/*.tif" -p 2

or
> python tractrac.py -f "../Sample_videos/RiverDrone/*.tif" -p 2

Run live-treatment by webcam acquisition by
> python tractrac.py -f "0" -p 1 -cmax 50

Details of parameters and commands are given in the publication <a href="https://perso.univ-rennes1.fr/joris.heyman/PDF/tractrac_final.pdf" > Heyman (2019) </a>.

# Output formats

A basic level of output is obtained with the average velocity maps saved as 32bit tiff image files (option -a in python). The images can then be post-treated with an image software such as Fiji/ImageJ. Image filenames contain extremum field values "[min,max]" so that images can be scaled appropriately.

A second level of post-processing is available in the Matlab GUI, with specific plotting functions on a defined grid. A post-processing binary matlab file is generated for further used. It contains cell arrays with trajectories mapped on the defined grid. 

If these two levels are not sufficient, the raw trajectories can also be saved in ASCII or binary files (hdf5) for further use.
