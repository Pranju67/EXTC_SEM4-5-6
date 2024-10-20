```
n = 7;
K = 4;
m = n - K;
fprintf('n = %d',n);
fprintf('k = %d',K);
fprintf('m = %d\n',m);
fprintf('The Generator Polynomial is x^3 + x^2 + 1\n');
g0=1;
g1=0;
g2=1;
g3=1;
fprintf('Hence g0= %d; g1= %d; g2= %d; g3= %d; \n',g0,g1,g2,g3); 
%taking Data
D = input('Enter the Data : ');
%Padding the Data with m=n-k zeros
D_pad = [D, zeros(1,m)];
disp('Padded data = ');
disp(D_pad );
%Generate the Table
S0 = 0;
S1 = 0;
S2 = 0;
fprintf('--------------------\n');
fprintf('d S2 S1 S0 \n');
fprintf(' %d %d %d \n', S2, S1,S0);
fprintf('--------------------\n');
%For loop 
for i = 1:n
 S0_old = S0;
 S1_old = S1;
 S2_old = S2;
 S0 = xor(D_pad(i), S2_old);
 S1 = xor(g1*S2_old, S0_old);
 S2 = xor(g2*S2_old, S1_old);
 fprintf(' %d %d %d %d \n',D_pad(i),S0, S1, S2);
end
%End of the Table
fprintf('--------------------\n\n');
%Parity Bit
p = [S0,S1,S2];
disp('Parity Bits = ');
disp(p);

%Data 
code = [D,p];
disp('Code Bits = ');
disp(code);

```