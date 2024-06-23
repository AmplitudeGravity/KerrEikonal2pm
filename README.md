# KerrEikonal2pm
this is the public data for the paper "Systematic integral evaluation in spin-resummed binary dynamics" The mathematica program is dependent on [KiHA](https://github.com/AmplitudeGravity/kinematicHopfAlgebra) 

## Closed form of eikonal
The closed form of the eikonal in stored in "EikonalClosedformList". Sum over it will generate the complete eikonal phase at 2PM of aligned spin with $a\cdot b\neq 0$. The output structure is like `T[f,rep]`. The `f` denotes the function in terms of $a$ and $b$. The `rep` doentes the replacement of the value of $a$ and $b$ in terms of spin vector `a[1]` and impact parameter `b[0]`.  The `T` means the contributions to eikonal should be evaluated under the $\sigma$-integral as $$T[f,rep]\equiv\int_0^1 d\sigma_1d\sigma_2d\sigma_3d\sigma_4 (f|_{rep}) $$ 

## Spin expansion of the eikonal
To get spin expansion result, you need to do the following steps
1. expand the incomplete elliptic function `integrate[f1,{K[1],0,y4}]` by `intSeries[_,{y4,10}]`.
2. perfom the spin expansions
3. integrate over all the $\sigma$ variables from 0 to 1. 



## Numerical evaluation of the eikonal at finite spin
To get the numerical value at finite spin, you need to do the following steps 
1. replace the two incomplete elliptic functions `integrate[f1,{K[1],0,y4}]` and `integrate[f2,{K[1],0,y4}]` by the known standard incomplete elliptic functions `EllipticF[_,_]` and `EllipticE[_,_]` in mathematica
2. replace all the dynamic parameters by numerical value
3. perform the numerical integration by `NIntegrate` from 0 to 1.

   We add an example to illustrate them and find the spin expasion result is identical with the resummed result for $|a|/|b|<0.5$. For $|a|/|b|>0.5$, spin expansion is not correct any more.
    
   <img width="450" alt="image" src="https://github.com/AmplitudeGravity/KerrEikonal2pm/assets/48633803/b6ac8d6b-86d1-4581-a81e-2bb2651a9d98">
   
   We also note that, for this example, when $|a|/|b|$ tend to 1, one need to fix the branches properly to get correct numerical result.  

   



