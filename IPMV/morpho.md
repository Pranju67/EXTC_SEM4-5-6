```
%% Erosion function
function Iout=my_erosion(A,B)
%To test function
%A= zeros(7,7);
%A(2:3,1:4) = 1
%A(4:5,3:5) = 1;
%B=[1,1,0;0,1,0;0,0,1]
[R,C]=size(A);
[R1,C1]= size(B);
xpad = (R1-1)/2;
ypad = (C1-1)/2;
% pad zeros at boundary
Apad = padarray(A,[xpad,ypad],0);
%2D convolution
Iout = zeros(R,C);
for x=1:R
 for y=1:C
 Isub = Apad(x:x+R1-1,y:y+C1-1);
 Iprod = Isub.*B;
 if sum(sum(Iprod)) >= sum(sum(B))
 Iout(x,y)=1;
 end
 end
end

%% DILATION FUNCTION
function Iout = my_dilation(A,B)
% To check whether function is working or not
%A= zeros(7,7);
%A(3:4,3:5) = 1;
%B=[1,1,0;0,1,0;0,0,1]
[R,C]=size(A);
[R1,C1]= size(B);
Bcap=flipud(fliplr(B)); % flipud= flip up and down, fliplr= flip left and right
xpad = (R1-1)/2;
ypad = (C1-1)/2;
% pad zeros at boundary
Apad = padarray(A,[xpad,ypad],0);
%2D convolution
Iout = zeros (R,C);
for x=1:R
 for y=1:C
 Isub = Apad(x:x+R1-1,y:y+C1-1);
 Iprod = Isub.*Bcap;
 Iout(x,y)=max(max(Iprod));
 end
end

clc;clear all;close all;
I = im2double(imread('FingurePrint.bmp'));
figure;imshow(I); title('Input Image');
% struturing element
B = ones(3,3);
%% A open B = (A erode B) dilate B
I1 = my_erosion(A,B);
figure; imshow(I1); title ('A erode B');
%I1 dilate B
I2 =my_dilation(I1,B);
figure; imshow(I2); title ('A open B');
%%(A open B)close B= I2 close B = (I2 dilute B)erode B
I3 = my_dilation(I2,B);
figure;imshow(I3);title('I2 dilute B');
I4 = my_erosion(I3,B);
figure; imshow(I4);title('(A open B) close B'))
```