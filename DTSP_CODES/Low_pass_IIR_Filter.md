```
clc
clear all;
close all;
fp=4000;
fs=8000;
fsamp=24000;
rs=0.108;
rp=0.01;
wp=2*pi*(fp/fsamp);
ws=2*pi*(fs/fsamp);
T=1/fsamp;
Op=2/T*(tan(wp/2));
Os=2/T*(tan(ws/2));
Ap =-20*log(1 - rp);
As=-20*log(rs);
[N,Oc]=buttord(Op,Os,Ap,As,'s')
[ns,ds]=butter(N,Os,'s');
hs=tf(ns,ds)
[nz,dz]=bilinear(ns,ds,fsamp);
Hz=tf(nz,dz,fsamp,'variable','z^-1')
%POLE ZERO PLOT
[z,p,k]=tf2zp(ns,ds);
subplot(3,1,1);
zplane(z,p);
title('Poles and Zeros');
%Frequency Response
w = -pi:0.01:pi;
Hw=freqz(nz,dz,w);
m=abs(Hw);
subplot(3,1,2);
plot(w,m);
title('Magnitude Plot');
xlabel('w');
ylabel('magnitude');
ph=angle(Hw);
subplot(3,1,3);
plot(w,ph);
title('Phase Plot');
xlabel('w');
ylabel('phase');

```