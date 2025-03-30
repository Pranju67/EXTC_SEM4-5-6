```
// GRAYSCALE_RESOLUTION.m
 
 clc;
 clear all;
 close all;
 I = imread('Peppers.bmp');
 Igray = rgb2gray(I); % Converting from RGB to GRAY 
 I8 = double(Igray);  % Changing class from UINT to DOUBLE
 I7 = floor(I8/2);    % Floor I8 value by 2 to get 7 bits
 I6 = floor(I7/2);    % Floor I8 value by 2 to get 7 bits or we can also do it by dividing I8 by 4 
 I5 = floor(I6/2);
 I4 = floor(I5/2);
 I3 = floor(I4/2);
 I2 = floor(I3/2);
 I1 = floor(I2/2);
 
 % Display output figure; 
 subplot(3,3,1);imshow(I8,[0,255]); title('8 bit image');
 subplot(3,3,2);imshow(I7,[0,127]); title('7 bit image');
 subplot(3,3,3);imshow(I6,[0,63]); title('6 bit image');
 subplot(3,3,4);imshow(I5,[0,31]); title('5 bit image');
 subplot(3,3,5);imshow(I4,[0,15]); title('4 bit image');
 subplot(3,3,6);imshow(I3,[0,7]); title('3 bit image');
 subplot(3,3,7);imshow(I2,[0,3]); title('2 bit image');
 subplot(3,3,8);imshow(I1,[0,1]); title('1 bit image');
 ```