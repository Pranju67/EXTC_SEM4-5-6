```
clc;
clear all;
close all;
xn
[3,-1,0,1,3,2,0,1,2]
hn
[1,1,1]
N=5
L=3
M=2
x1 =[xn (1:L), zeros (1,2)]
x2=[xn (L+1:2*L), zeros (1,2)]
x3=[xn (2*L+1:3*L), zeros (1,2)]
hl
[hn, zeros (1,2)]
hm=[hl; circshift (hl, [0 1]); circshift (hl, [0 2]); circshift (hl, [0 3]); circshift (hl, [0 4])]
yl=x1*hm
y2=x2*hm
y3=x3*hm
yn= [yl (1:3), y1 (4:5)+y2 (1:2), y2 (3), y2 (4:5) +y3 (1:2), y3 (3), y3 (4:5)]
y=conv (xn, hn)
```