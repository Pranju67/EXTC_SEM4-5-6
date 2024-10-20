```
clc;
close all;
clear all;
r=0.5;
bo=1;
w=-pi:0.01:pi;
Hw=(bo/(1-r))*(1-r*exp(-j*2*w));
MD=abs(Hw);
PD=angle(Hw);
subplot(4,3,1);
plot(w,MD);
subplot(4,3,2);
plot(w,PD);
a=[1 0];
b=[5 1 5];
[z,p,k]=tf2zp(a,b);
subplot(4,3,3);
zplane(z,p);
Hw1=bo*(1-2*exp(-j*w)*cos(pi/4)+exp(-j*2*w));
MD1=abs(Hw1);
PD1=angle(Hw1);
subplot(4,3,4);
plot(w,MD1);
subplot(4,3,5);
plot(w,PD1);
a1=[1 1 1];
b1=[1 0 0];
[z,p,k]=tf2zp(a1,b1);
subplot(4,3,6);
zplane(z,p);
m=6;
hc=(1/m+1)*(exp(-j*w(m/2)).*(sin((m+1/2)*w)./sin(w/2)))
MD=abs(hc);
PD=angle(hc);
subplot(4,3,7);
plot(w,MD);
subplot(4,3,8);
plot(w,PD);
a=[1 0 0 0 0 0 1];
b=[1 1 0 0 0 0 0];
[z,p,k]=tf2zp(a,b);
subplot(4,3,9);
zplane(z,p);
z1=1/0.8;
z2=1/-0.8;
p1=0.8;

p2=-0.8;
Ha = (((exp(j * w) - z1) .* (exp(j * w) - z2)) ./ ((exp(1j * w) - p1) .* (exp(j * w) - p2)));
MD=abs(Ha);
PD=angle(Ha);
subplot(4,3,10);
plot(w,MD);
subplot(4,3,11);
plot(w,PD);
b=[1 0 0 0 0.25]
%
a=[1 0 0 0 64]
%
[z,p,k]=tf2zp(a,b)
subplot(4,3,12);
zplane(z,p);

```