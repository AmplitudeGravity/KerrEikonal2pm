# KerrEikonal2pm
This is the public data for the paper "Systematic integral evaluation in spin-resummed binary dynamics". The `Mathematica` notebooks provided in this repository are dependent on the package [KiHA](https://github.com/AmplitudeGravity/kinematicHopfAlgebra) 

## Closed form of eikonal
The closed form of the eikonal is stored in "EikonalClosedformList". Summing it up will generate the complete eikonal phase at 2PM in the aligned-spin configuration with $a\cdot b\neq 0$. The output contains structures of the form `T[f,rep]`, where `f` denotes the function in terms of $a$ and $b$, and `rep` denotes the replacement rules that define the values of $a$ and $b$ in terms of the spin vector `a[1]` and the impact parameter `b[0]`. (For more detail, see the discussions on "sectors" around Eq.(14) in the manuscript.) The placeholder function head `T` indicates that there are remaining $\sigma_i$-integrations to be performed, in order to obtain each term's final contribution to the eikonal phase. Namely, such terms are to be evaluated as $$T[f,rep]\equiv\int_0^1 d\sigma_1d\sigma_2d\sigma_3d\sigma_4 (f|_{rep}) $$ 

## Spin expansion of the eikonal
To obtain the *analytical* expression for the aligned-spin eikonal to a given order in spin, the following steps are to be taken:
1. Compute the series expansion of the incomplete elliptic integral `integrate[f,{K[1],0,y4}]` using the function `intSeries[_,{y4,order}]`.
2. Substitute the definitions of `y2` and `y4` in each sector (namely, each `T[f, rep]`) using the functions `Y2[rep]` and `Y4[rep]`.
3. Substitute the values of `a` and `b` in each sector as given in `rep`.
4. Compute the series expansion in powers of `a[1]`.
5. Integrate over all the $\sigma$ variables in each sector from 0 to 1. 



## Numerical evaluation of the eikonal at finite spin
To obtain the numerical value of the *aligned-spin* eikonal at finite spin, the following steps are to be taken:
1. Replace the two incomplete elliptic integrals `integrate[f1,{K[1],0,y4}]` and `integrate[f2,{K[1],0,y4}]` with the built-in definitions of the elliptic integrals `EllipticF[_,_]` and `EllipticE[_,_]` in `Mathematica` using the replacement `repEKback`.
2. Substitute the definitions of `y2` and `y4` in each sector (namely, each `T[f, rep]`) using the functions `Y2[rep]` and `Y4[rep]`.
3. Substitute the values of `a` and `b` in each sector as given in `rep`.
4. Replace all the dynamic parameters, such as `dot[a[1],b[0]]`, with numerical values
5. Integrate out all the $sigma_i$ variables from 0 to 1 numerically using `NIntegrate`

   We add an example to illustrate this procedure and show that the spin expansion converges and agrees with the resummed result for $|a|/|b|<0.5$. For $|a|/|b|>0.5$, the expansion in spin does not hold.
    
   <img width="450" alt="image" src="https://github.com/AmplitudeGravity/KerrEikonal2pm/assets/48633803/b6ac8d6b-86d1-4581-a81e-2bb2651a9d98">
   
   We also note that, in this example, as $|a|/|b|\rightarrow 1$, the branch cut of the square root needs to be chosen explicitly in order to obtain the correct numerical result.  

   
## Spin expansion up to $\mathcal{O} (a^8)$

The spin expanded result is stored in the variable `EikonalExpandList2`

## Numerical values of the eikonal for a test Kerr black hole scattering from a background Schwarzschild black hole
The full data of the eikonal is stored in the variable `intScalarSpin`

In this limit, the Y-diagram contribution is greatly simplified. There are only two integrations, over $\sigma_1$ and  $\sigma_2$, to be carried out. The incomplete elliptic integrals are absent. The eikonal at finite spin is obtained in the same way as above, while the procedure is simplified.
