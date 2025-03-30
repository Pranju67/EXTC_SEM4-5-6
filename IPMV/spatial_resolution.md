```
// change_spatial_resolution.m 
 clc;
 clear all;
 Image = imread('Lena_small.bmp');
 
% convert to double class with range 0 to 255
 I = double (Image);
 [R,C] = size (I);
 disp('Original size: ');
 disp ([R,C]);
 
 Z = input('Enter zoom factor: ');
 disp ('New size will be: ');
 disp([R*Z,C*Z]); 
 imshow(I,[]); title ('Output');
 
% pixel replication 
 I1 = [];
 for x = 1:R
    L = [];
    for y =1:C
        pixel = I(x,y);
        Block = repmat(pixel,Z,Z);
        L = [L,Block];
    end
    I1 = [I1;L];
 end
 figure;imshow(I1,[]);title ('Pixel Rep');
 
 % Bilinear Interpolation
 % Interpolation along row
 [R,C] = size(I);
 Irow = [ ];
 for x = 1:R
    L = [];
    for y=1:C-1 % Bilinear interpolate except boundary pixel
        %Bilinear interpolation 
        P1 = I(x,y);
        P2 = I(x,y+1);  % pixel calculatiuon for x and y axis
        L = [L,P1];
        for n = 1: Z-1
            Pn = (P2-P1)/Z*n +P1;
            L = [L,Pn];
        end
    end
    
    % Pixel rep for boundary pixel 
    Pb = I(x,C);
    Block = repmat (Pb,1,Z);
    L = [L,Block];
    % append it below previous row
    Irow = [Irow;L];
 end
    figure;imshow(Irow,[]);title('Irow');
   
% Interpolation along column
 IrowT = Irow';
 [R1,C1]= size (IrowT);
 Icol = [ ];
 for x = 1:R1
    L = [];
    for y=1:C1-1 % Bilinear interpolate except boundary pixel
        %Bilinear interpolation 
        P1 = IrowT(x,y);
        P2 = IrowT(x,y+1);
        L = [L,P1];
        for n = 1: Z-1
            Pn = (P2-P1)/Z*n +P1;
            L = [L,Pn];
        end
    end
    
    % Pixel rep for boundary pixel 
    Pb = IrowT(x,C1);
    Block = repmat (Pb,1,Z);
    L = [L,Block];
    % append it below previous row
    Icol = [Icol;L];
    
end
 
    figure;imshow(Icol,[]);title('Icol');
    I2 = Icol.';
    figure;imshow(I2,[]);title('Bilinear Interpolation');
```  
 
 
    
    
 
 