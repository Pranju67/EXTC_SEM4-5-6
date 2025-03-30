```
% pract 4: Histogram eqalization
 
 clc;
 clear all;
 close all;
 Image = imread('CST.bmp');
 % convert to double class with range 0-255
 I = double(Image);
 figure;imshow(I,[]);title('Input image');
 [R,C] = size(I);
 N=R*C;
 %INPUT HISTOGRAM
 H1 =zeros(1,256);
 for r = 0:255
     temp=zeros(R,C); % It will make empty matrix where it was filled with all zeros
     temp(I==r)=1; % It will match the orginal matrix with r value i.e from 0:256
     nk = sum(temp(:)); % It will count the no of pixels for r values 
     H1(r+1)= nk % It will update the histogram values (r+1) is used as histogram starts 
     from '1' index
 end
 figure;
 stem([0:255],H1); % plot the histogram
 xlabel('Gray Level');
 ylabel('No of pixels');
 title('Input Histogram');
 
% Histogram equalization 
% The below functions willl perform histogram equalization as per theory 
% PDF 
 Pk = H1/N;
 % CDF
 Sk = cumsum(Pk);
 % Valid S
 S = round (Sk*255);
 
% Transfer function 
 figure;
 plot([0:255],Sk*255);
 xlabel('Input gray level');
 ylabel('Output gray level');
 title('Transfer function');
 xlim([0,255]);
 ylim([0,255]);
 
% Output image
 Iout = zeros(R,C);
 for r = 0:255
    Iout(I==r)=S(r+1);
 end
 figure;
 imshow(Iout,[]);title('Output image');
 

 % Output Histogram
 H2 =zeros(1,256);
 for r = 0:255
 temp=zeros(R,C); % It will make empty matrix where it was filled with all zeros
 temp(Iout==r)=1; % It will match the orginal matrix with r value i.e from 0:256
 nk = sum(temp(:)); % It will count the no of pixels for r values 
 H2(r+1)= nk % It will update the histogram values (r+1) is used as histogram starts 
             from '1' index
 end
 figure;
 stem([0:255],H2); % plot the histogram
 xlabel('Gray Level');
 ylabel('No of pixels');
 title('Output Histogram');
 ```