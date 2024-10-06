```
clc;
clear all;
close all;
Xn = input ('Enter value of Xn: ')
N = length (Xn)
for K = 0:N-1
    for n = 0:N-1
       w (n+1, K+1)= exp ((-j*2*pi*n*K)/N)
    end
end
Tf = W
xk = Xn*w
magnitude = abs (xk)
phase = angle (xk)
n = 0:1:N-1
subplot (2,1,1)
stem (n, magnitude)
title ('Magnitude plot xk')
xlabel('n')
ylabel('phase')
subplot (2,1,2)
stem (n, phase)
title('phase plot xk')
xlabel('n')
ylabel('phase')
xlk = fft (Xn)
```