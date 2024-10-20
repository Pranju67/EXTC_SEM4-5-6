```
clc;
clear all;
close all;
symbol-[1:6];
prob [0.5, 0.25, 0.125, 0.0625, 0.03125, 0.03125];
[Dict, avglen]=huffmandict (symbol, prob, 2, 'min');
Dict(:,2) = cellfun (@num2str, Dict (:,2), 'UniformOutput', false);
display(' symbols their code');
display (Dict);
display(' avg length');
display (avglen);
Entropy
E=0;
for k=symbol
end
E=E+prob (k) *log2 (1/prob (k));
display('Entropy');
display (E);
*Efficency
Eff=E/avglen* 100;
display('Efficency of the code');
display (Eff);
&redundancy
R=100-Eff;
display('% redundancy');
display (R);
```