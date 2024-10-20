```
clc;
clear all;
*Encoder
disp('Parity Matrix')
P =[0 1 1; 1 1 0; 1 0 1; 1 1 1]
disp('Generator Matrix')
G=[eye (4), P]
disp('Data');
D= [1 1 0 1]
disp('Transmitted Code')
C= D*G
C= mod (D*G, 2)
*Channel
disp('Error Pattern')
E=[0 0 0 0 0 0 0]
disp('Received Code')
R=mod (C+E, 2)
*Decoder
disp('H Transpose')
HT =[P; eye (3)]
disp('Error Syndrome')
S=mod (R*HT, 2) 
if S==0
else
end
disp('No Error in recieve signal')
disp('Decoded data')
D_RX = R (1:4)
disp('Error in recieved signal')
[tf, index]=ismember (S, HT, 'rows') 
disp('Location of error bit');
index;
disp('Error in recieved signal');
error zeros (1,7);
error (index)=1
disp('Corrected R');
Rx  = mod (R+error, 2)
disp('Decoded data');
D_Rx = Rx (1:4)
```