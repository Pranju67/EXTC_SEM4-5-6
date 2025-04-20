```
%Program 7 : Energy Compaction
clc;
close all;
clear all;
Image = imread('Cameraman.bmp');
%Convert to double with range 0 to 1
I = im2double(Image);
figure;imshow(I,[]);
title('Input image');
N = input('No. of Rows and Columns to be Truncated : ');
%% DFT
I_DFT = fft2(I);
% Use Log transform to Display spectrum
figure;
imshow(log(abs(I_DFT)+1),[]);
title('DFT');
%Truncate DFT
I_DFT_T = I_DFT ;
I_DFT_T(end - N : end , :) = 0 ;
I_DFT_T(: , end - N : end) = 0 ;
figure ;
imshow(log(abs(I_DFT_T)+1),[]);
title('Truncated DFT');
% Take Inverse
Iout = ifft2(I_DFT_T);
figure;
imshow(Iout,[]);
title('DFT Output');
%% DCT
I_DCT = dct2(I);


% Use Log transform to Display spectrum
figure;
imshow(log(abs(I_DCT)+1),[]);
title('DCT');
%Truncate DFT
I_DCT_T = I_DCT ;
I_DCT_T(end - N : end , :) = 0 ;
I_DCT_T(: , end - N : end) = 0 ;
figure ;
imshow(log(abs(I_DCT_T)+1),[]);
title('Truncated DCT');
% Take Inverse
Iout2 = idct2(I_DCT_T);
figure;
imshow(Iout2,[]);
title('DCT Output');
```