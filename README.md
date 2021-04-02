# regionGrowing:
A recursive region growing algorithm for 2D and 3D grayscale image sets with polygon and binary mask output. 
## matlab
## regionGrowing3D:26-neighbor
This function performs "regiongrowing3D" in 3D data from a specified seedpoint (x,y,z)

#### J = regiongrowing(I,x,y,z,t) 
I : input 3Ddata 
J : logical output result of region
x,y,z : the position of the seedpoint (if not given uses function getpts)
t : maximum intensity distance (defaults to 0.2)

####
The region is iteratively grown by comparing all unallocated neighbouring pixels to the region. The difference between a pixel's intensity value and the region's mean, is used as a measure of similarity. The pixel with the smallest difference measured this way is allocated to the respective region. This process stops when the intensity difference between region mean andnew pixel become larger than a certain treshold (t)

#### Example:
load('ct.mat');
I=squeeze(ct);
J=regiongrowing3D(I,245,268,26,0.05);
volumeViewer(J);

## regionGrowing2D:8-neighbor

#### J = regiongrowing(I,x,y,t) 
I : input image 
J : logical output image of region
x,y : the position of the seedpoint (if not given uses function getpts)
t : maximum intensity distance (defaults to 0.2)

#### Example:
I = im2double(imread('medtest.png'));
x=198; y=359;
J = regiongrowing(I,x,y,0.2); 
figure, imshow(I+J);

