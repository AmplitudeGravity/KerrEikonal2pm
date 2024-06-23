# KerrEikonal2pm
this is the public data for the paper "Systematic integral evaluation in spin-resummed binary dynamics" The mathematica program is dependent on [KiHA](https://github.com/AmplitudeGravity/kinematicHopfAlgebra) 

## Closed form of eikonal
The closed form of the eikonal in stored in "EikonalClosedformList". Sum over it will generate the complete eikonal phase at 2PM of aligned spin with $a\cdot b\neq 0$. The output structure is like `T[f,rep]`. The "f" denotes the function in terms of $a$ and $b$. The "rep" denotes the value of $a$ and $b$ in terms of spin "a[1]" and "b[0]". They are donote the spin vector and impact parameter respectively. The `T` means the contributions to eikonal should be evaluated under the $\sigma$-integral as $$\int_0^1 d\sigma_1d\sigma_2d\sigma_3d\sigma_4 (f|_{rep}) $$ 

## Spin expansion of the eikonal

## Numerical check of the master integral $\widehat{\mathcal{I}}_3$

## Numerical evaluation of the eikonal at finte spin


