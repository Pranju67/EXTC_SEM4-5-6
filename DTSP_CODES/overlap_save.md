```
--CODE
clc;
clear all;
close all;
xn=[3,-1,0,1,3,2,0,1,2,1]
hn=[1,1,1]
N=5
L=3
M=3
x1=[zeros(1,M-1),xn(1:L)]
x2=[x1(4:5),xn(L+1:2*L)]
x3=[x2(4:5),xn(2*L+1:3*L)]
x4=[x3(4:5),xn(3*L+1),0,0]
h1=[hn,zeros(1,N-M)]
hm=[h1;circshift(h1,[0 1]);circshift(h1,[0 2]);circshift(h1,[0
3]);circshift(h1,[0 4])]
y1= x1 * hm
y2= x2 * hm
y3= x3 * hm
y4= x4 * hm
yn=[y1(3:5),y2(3:5),y3(3:5),y4(3:5)]
yn=conv(xn,hn)

```