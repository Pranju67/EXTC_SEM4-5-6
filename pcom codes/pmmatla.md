```
clc;
vm=5;
vc=2;
K=1;
pi=3.14;
fm=100;
fc=1000;
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
vfmt=vc*cos(2*pi*fc*t+K*vm*cos(2*pi*fm*t));
subplot(4,1,3);
plot(vfmt(1:300));
title('Phase modulated signal')
```
