```
//Contrast_Stretching.m 
 
 clc;
 clear all;
 close all;
 Image = imread('CST.bmp');
 % convert to double class with range 0-255
 I = double(Image);
 [R,C] = size(I);
 figure;imshow(I,[]);title('Input Image');
 % Input Parameters
 r1 = input('Enter r1:');
 r2 = input('Enter r2:');
 s1 = input('Enter s1:');
 s2 = input('Enter s2:');
 if r1 > r2 || s1 > s2
    disp('Invalid parameters.');
 elseif r1 == r2 && s1 == s2
    disp('Identity Transformation');
    Iout = I;  % Identity transformation
    figure;imshow(Iout,[]);title('Identity Transformation');
 elseif r1 == r2 && s1 == 0 && s2 == 255
    disp('Thresholding');
    Iout = I;  % Initialize Iout
    for x = 1:R
        for y = 1:C
            if I(x,y) < r1
                Iout(x,y) = 0;
            else
                Iout(x,y) = 255;
            end
        end
    end
    figure;imshow(Iout,[]);title('Thresholding');
 elseif r1 ~= r2 && s1 == 0 && s2 == 255
    disp('Clipping');
    m2 = 255 / (r2 - r1);
    Iout = I;  % Initialize Iout
    for x = 1:R
        for y = 1:C
            if I(x,y) < r1
                Iout(x,y) = 0;
            elseif r1 <= I(x,y) && I(x,y) < r2
                Iout(x,y) = m2 * (I(x,y) - r1);
            else
                Iout(x,y) = 255;
            end
        end
    end
    figure;imshow(Iout,[]);title('Clipping');
 else
    disp('General Contrast Stretching');
    m1 = s1 / r1;
    m2 = (s2 - s1) / (r2 - r1);
    Iout = I;  % Initialize Iout
    for x = 1:R
        for y = 1:C
            if I(x,y) < r1
                Iout(x,y) = m1 * I(x,y);
            elseif r1 <= I(x,y) && I(x,y) < r2
                Iout(x,y) = m2 * (I(x,y) - r1) + s1;
            else
                Iout(x,y) = m2 * (I(x,y) - r2) + s2;
            end
        end
    end
    figure;imshow(Iout,[]);title('General Contrast Stretching');
 end
 
```