
An algorithm that says that you can multiply two matrices with 7 multiplications of the sub-matrices, instead of the typical 8. It was fun to re-derive how it would work, but I don't think I really got any insight into anything.

![[Screenshot 2025-05-25 at 11.22.10 PM.png]]




M1 = (A + D)(E + H) = AE + DE + AH + DH 

M2 = (B - D)(G + H) = BG - DG + BH - DH

M3 = (-A + C)(E + F) = -AE + CE - AF + CF

M4 = (A + B)H = AH + BH

M5 = (C + D)E = CE + DE

M6 = D(-E + G) = -DE + DG

M7 = A(F - H) = AF - AH

Q1 = M1 + M2 - M4 + M6 = (AE + DE + AH + DH) + (BG - DG + BH - DH) - (AH + BH) + (-DE + DG) +  = AE + BG

Q2 = M5 + M6

Q3 = M4 + M7 = AF + BH

Q4 = M1 + M3 + M7 - M5 = CF + DH



