```
clc;
clear all;
close all;
m=input('enter no of message ensembles:');
display('enter the probabilities in descending order');
for i=1:m
 fprintf('ensemble %d:',i); %esemnle %d will display value of prob as 1 to m
 p(i)=input(''); 
end
a(1)=0; %initially set alpha a(1)=0
for j=2:m
 a(j)=a(j-1) + p(j-1); %a(j)=previos value of alpha a + previous value of prob
end
display('alpha matrix')
display(a);
for i=1:m
 n(i)=ceil(log2(1/p(i)));
end
display('length of code')
display(n);
for i=1:m
 z=[]; 
 int=a(i); %let inital is 0.5
 for j=1:n(i) %for above j=1 to 2
 frac = int*2; %f=0.5*2=1
 c=floor(frac); %c=1(round figure)
 frac=frac-c; %f=1-1=0
 z=[z c]; 
 int =frac; %int=f=0(updated value of f)
 end
 fprintf('codeword %d\n',i); %for above values z=[1 0]
 display(z);
end
H=0;
L=0;
for i=1:m
 Hx=p(i)*log2(1/p(i));
 H=H+Hx;
 
 Lx=p(i)*n(i);
 L=L+Lx;
end
display('entropy');
display(H);

display('average code length')
display(L);
E=100*H/L;
display('efficency');
display(E);
R=100-E;
display('Redundancy');
display(R);
```