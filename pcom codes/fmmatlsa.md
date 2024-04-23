```
clc;
vm=7;
vc=2;
k=400;
wm=2*3.14*fm;
fm=100;
fc=1000;
mf = k*vm/wm;
t=0:0.0001:1;
vmt=vm*cos(2*pi*fm*t);
subplot(4,1,1);
plot(vmt(1:300));
%xlable('t');
%ylable('vm');
title('modulating signal')
vct=vc*cos(2*pi*fc*t);
subplot(4,1,2);
plot(vct(1:300));
title('Carrier signal');
vfmt=vc*cos(2*pi*fc*t+((k*vm)/wm)*sin(2*pi*fm*t));
subplot(4,1,3);
plot(vfmt(1:300));
title('Frequency modulated signal')
```
