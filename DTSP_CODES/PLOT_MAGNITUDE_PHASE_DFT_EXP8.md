```
clc
clear all;
close all;
xn = input('Enter input x(n) : ');
N = length(xn);
for k = 0:N-1
for n = 0:N-1
w(n+1,k+1) = exp((-1j*2*pi*n*k)/N);
end
end
Tf=w;
xk = xn*w;
magnitude = abs(xk);
phase = angle(xk);
n = 0:1:N-1;
subplot(2,1,1);
stem(n,magnitude)
title('Magnitude Plot of x(k).');
xlabel('n');
ylabel('phase')
subplot(2,1,2);
stem(n,phase)
title('Phase Plot of x(k).');
xlabel('n');
ylabel('Phase')
x1k=fft(xn)

```