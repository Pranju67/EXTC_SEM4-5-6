```
%Exp=8:Image Denoising
clc;
clear all;
close all;
Image = imread('Peppers.bmp');
%convert image to gray scale
Igray=rgb2gray(Image);
%convert to double format with range 0 to 1
I= im2double(Igray);
[R,C] = size(I);
figure; imshow(I,[]);
title('Input Image');
%Add noise to Image
I1 = imnoise(I,'gaussian',0,0.01);
I2 = imnoise(I,'salt & pepper',0.1);
figure;imshow(I1,[]);
title('Gaussian Noise');
figure;imshow(I2,[]);
title('Salt & Pepper Noise');

%% Removal of Gaussion Noise by simple averaging
%simple Averaging
W=3; % w = size of matrix
mask1=ones(W,W)/(W*W);
[R1,C1]=size(mask1);
Xpad = (R1-1)/2;
Ypad = (C1-1)/2;
%Pad image by pixel replication
Ipad=padarray(I1,[Xpad,Ypad],'replicate');
%2D convolution


Iout1 = zeros(R,C);
for x=1:R
      for y=1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1);
        Iout1(x,y)=sum(sum(Isub.*mask1));
      end
end
figure;imshow(Iout1,[]);
title(' Remove of Gaussian by Simple Average');

%% Removal of Salt & Pepper Noise by simple averaging
%simple Averaging
W=3; % w = size of matrix
mask1=ones(W,W)/(W*W);
[R1,C1]=size(mask1);
Xpad = (R1-1)/2;
Ypad = (C1-1)/2;
%Pad image by pixel replication
Ipad=padarray(I2,[Xpad,Ypad],'replicate');
%2D convolution
Iout1 = zeros(R,C);
for x=1:R
    for y=1:C
       Isub = Ipad(x:x+R1-1,y:y+C1-1);
       Iout1(x,y)=sum(sum(Isub.*mask1));
    end
end
figure;imshow(Iout1,[]);
title(' Remove of Salt & Pepper by Simple Average');

%% Removal of Gaussion Noise by Median Filter
W=3; % w = size of matrix
R1=W; C1=W;
M = (R1*C1 + 1)/2; % median

Xpad = (R1-1)/2;
Ypad = (C1-1)/2;
%Pad image by pixel replication
Ipad=padarray(I1,[Xpad,Ypad],'replicate');
%2D convolution
Iout1 = zeros(R,C);
for x=1:R
    for y=1:C
      Isub = Ipad(x:x+R1-1,y:y+C1-1);
      Ivector = reshape(Isub,1,R1*C1); %convert 2D into 1D
      Isort = sort(Ivector);
      Iout1(x,y)=Isort(M);
    end
end
figure;imshow(Iout1,[]);
title(' Remove of Gaussian by Median Filter');

%% Removal of Salt & Pepper Noise by Median Filter
W=3; % w = size of matrix
R1=W; C1=W;
M = (R1*C1 + 1)/2; % median
Xpad = (R1-1)/2;
Ypad = (C1-1)/2;
%Pad image by pixel replication
Ipad=padarray(I2,[Xpad,Ypad],'replicate');
%2D convolution
Iout1 = zeros(R,C);
for x=1:R
   for y=1:C
     Isub = Ipad(x:x+R1-1,y:y+C1-1);
     Ivector = reshape(Isub,1,R1*C1); %convert 2D into 1D
     Isort = sort(Ivector);
     Iout1(x,y)=Isort(M);
   end
end
figure;imshow(Iout1,[]);
title(' Remove of Salt & Pepper by Median Filter');
```