```
clc;
vm=2;
vc=2;
fm=500;
fc=5000;
t=0:0.00001:1;
vmt= vm*cos(2*pi*fm*t);
subplot(4,1,1);
plot(vmt(1:400));
title('modulating signal');
vct= 2*cos(2*pi*fc*t);
subplot(4,1,2);
plot(vct(1:400));
title('carrier signal');
vamt= vm/2*cos(2*pi*(fc-fm)*t);
subplot(4,1,3);
plot(vamt(1:400));
title('Amplitude modulated signal for m<1 (SSBSC)')
```