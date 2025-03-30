``` 
 % spatial filtering
 
 clc;clear all; close all;
 Image = imread('Lena.bmp');
 % convert to double format in the image 0 to 1
 I= im2double(Image);
 figure; imshow(I,[]); title('Input image');
 [R,C]=size(I);
 
%% Simple averaging
 mask1 = [1,1,1;1,1,1;1,1,1]/9; % define mask
 [R1,C1]=size(mask1);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Iout1 = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* mask1; % multiply subimages and mask point-to-point
        Iout1(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y) =sum(Iprod(:))
    end
 end
 figure;
 imshow(Iout1,[]);title('Simple Average');
 
%% Weighted averaging
 mask2 = [1,2,1;2,4,2;1,2,1]/16; % define mask
 [R1,C1]=size(mask2);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Iout2 = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* mask2; % multiply subimages and mask point-to-point
        Iout2(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y)=sum(Iprod(:))
    end
 end
 figure;
 imshow(Iout2,[]);title('Weighted Average');
 
%% Laplacian negative center
 mask3 = [0,1,0;1,-4,1;0,1,0]; % define mask
 [R1,C1]=size(mask3);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Iout3 = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* mask3; % multiply subimages and mask point-to-point
        Iout3(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y) =sum(Iprod(:))
    end
 end
 figure;
 imshow(Iout3,[]);title('Laplacian negative center');
 
%% Laplacian positive center
 mask4 = [0,-1,0;-1,4,-1;0,-1,0]; % define mask
 [R1,C1]=size(mask4);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Iout4 = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* mask4; % multiply subimages and mask point-to-point
        Iout4(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y) =sum(Iprod(:))
    end
 end
 figure;
 imshow(Iout4,[]);title('Laplacian positive center');
 
                     % GRADIENT
 
%% x GRADIENT
 maskx = [0,0,0;0,1,0;0,-1,0]; % define mask
 [R1,C1]=size(maskx);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Gx = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* maskx; % multiply subimages and mask point-to-point
        Gx(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y)=sum
 (Iprod(:))
    end
 end
 figure;
 imshow(Gx,[]);title('x GRADIENT');
 
%% y GRADIENT
 masky = [0,0,0;0,1,-1;0,0,0]; % define mask
 [R1,C1]=size(masky);
 xpad = (R1-1)/2; % formula for padding
 ypad = (C1-1)/2; % same as x
 
% Pad image with pixel replication
 Ipad = padarray(I,[xpad,ypad],'replicate');
 
% 2D convolution
 Gy = zeros(R,C);
 for x = 1:R
    for y = 1:C
        Isub = Ipad(x:x+R1-1,y:y+C1-1); % to form subimages 
        Iprod = Isub .* masky; % multiply subimages and mask point-to-point
        Gy(x,y)=sum(sum(Iprod)); % sum(sum(Iprod))- For 2D image or use- Iout1(x,y)=sum(Iprod(:))
    end
 end
 figure;
 imshow(Gy,[]);title('y GRADIENT');
 
% Find final output
 G = abs(Gx)+abs (Gy);
 figure;
 imshow(G,[]); title('Gradient');