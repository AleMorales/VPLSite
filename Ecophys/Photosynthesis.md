
<a id='Module-Photosynthesis'></a>

<a id='Module-Photosynthesis-1'></a>

# Module Photosynthesis




<a id='CO2-assimilation-and-stomatal-conductance'></a>

<a id='CO2-assimilation-and-stomatal-conductance-1'></a>

## CO2 assimilation and stomatal conductance

<a id='Ecophys.Photosynthesis.C3' href='#Ecophys.Photosynthesis.C3'>#</a>
**`Ecophys.Photosynthesis.C3`** &mdash; *Type*.



```julia
C3(Sco25 = 2800.0, E_Sco = -24.46e3, Kmc25 = 270.0, E_Kmc = 80.99e3, 
    Kmo25 = 165.0e3, E_Kmo = 23.72e3, Vcmax25 = 120.0, E_Vcmax = 65.33e3, 
    theta = 0.7, Phi2 = 0.82, sigma2 = 0.5, beta = 0.85, fcyc = 0.1, 
    fpseudo = 0.05, Jmax25 = 230.0, E_Jmax = 30.0e3, D_Jmax = 200.0e3, 
    Topt_Jmax = 300.5, TPU25 = 12.0, E_TPU = 53.1e3, D_TPU = 20.18e3)
```

Data structure to store all the parameters for the C3 photosynthesis model.

**Arguments**

  * `Sco25`: Sc/o parameter at 25 C
  * `E_Sco`: Apparent activation energy of Sc/o (J/mol)
  * `Kmc25`: Km for CO2 at 25 C (μmol/mol)
  * `E_Kmc`: Activation energy of Kmc (J/mol)
  * `Kmo25`: Km for O2 at 25 C (umol/mol)
  * `E_Kmo`: Activation energy of Kmo (J/mol)
  * `Vcmax25`: Maximum rate of carboxylation at 25 C (μmol/m2/s)
  * `E_Vcmax`: Activation energy of Vcmax (J/mol)
  * `theta`: Curvature parameter
  * `Phi2`: Low-light PSII quantum yield
  * `sigma2`: Partitioning of excitation between PSII and PSI
  * `beta`: Leaf absorptance of PAR
  * `fcyc`:  Fraction of electrons at PSI that follow cyclic transport around PSI
  * `fpseudo`: Fraction of electrons at PSI that are used by alternative electron sinks
  * `Jmax25`: Maximum rate of electron transport (μmol/m2/s)
  * `E_Jmax`: Activation energy Jmax (J/mol)
  * `D_Jmax`: Deactivation energy of Jmax (J/mol)
  * `Topt_Jmax`: Optimal temperature for Jmax (K)
  * `TPU25`: Maximum rate of triose phosphate utilisation (μmol/m2/s)
  * `E_TPU`: Activation energy TPU (J/mol)
  * `D_TPU`: Deactivation energy of TPU (J/mol)


<a target='_blank' href='https://github.com/JuliaLang/julia/blob/17cfb8e65ead377bf1b4598d8a9869144142c84e/base/docs/Docs.jl#L473-L504' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.C3Q' href='#Ecophys.Photosynthesis.C3Q'>#</a>
**`Ecophys.Photosynthesis.C3Q`** &mdash; *Type*.



```julia
C3Q(Sco25 = 2800.0, E_Sco = -24.46e3J/mol, Kmc25 = 270.0μmol/mol, E_Kmc = 80.99e3J/mol,
     Kmo25 = 165.0e3μmol/mol, E_Kmo = 23.72e3J/mol, Vcmax25 = 120.0μmol/m^2/s, E_Vcmax = 65.33e3J/mol,
     theta = 0.7, Phi2 = 0.82, sigma2 = 0.5, beta = 0.85, fcyc = 0.1, fpseudo = 0.05, 
     Jmax25 = 230.0μmol/m^2/s, E_Jmax = 30.0e3J/mol, D_Jmax = 200.0e3J/mol, Topt_Jmax = 300.5K, 
     TPU25 = 12.0μmol/m^2/s, E_TPU = 53.1e3J/mol, D_TPU = 201.8e3J/mol, Topt_TPU = 306.5K, 
     Rd25 = 1.2μmol/m^2/s, E_Rd = 46.39e3J/mol, gm25 = 0.4mol/m^2/s, E_gm = 49.6e3J/mol, 
     D_gm = 437.4e3J/mol, Topt_gm = 308.6K, gso = 0.01mol/m^2/s, a1 = 0.85, b1 = 0.14e-3/Pa)
```

Data structure to store all the parameters for the C3 photosynthesis model using `Quantity` objects from Unitful.jl.

**Arguments**

  * `Sco25`: Sc/o parameter at 25 C
  * `E_Sco`: Apparent activation energy of Sc/o (J/mol)
  * `Kmc25`: Km for CO2 at 25 C (μmol/mol)
  * `E_Kmc`: Activation energy of Kmc (J/mol)
  * `Kmo25`: Km for O2 at 25 C (umol/mol)
  * `E_Kmo`: Activation energy of Kmo (J/mol)
  * `Vcmax25`: Maximum rate of carboxylation at 25 C (μmol/m2/s)
  * `E_Vcmax`: Activation energy of Vcmax (J/mol)
  * `theta`: Curvature parameter
  * `Phi2`: Low-light PSII quantum yield
  * `sigma2`: Partitioning of excitation between PSII and PSI
  * `beta`: Leaf absorptance of PAR
  * `fcyc`:  Fraction of electrons at PSI that follow cyclic transport around PSI
  * `fpseudo`: Fraction of electrons at PSI that are used by alternative electron sinks
  * `Jmax25`: Maximum rate of electron transport (μmol/m2/s)
  * `E_Jmax`: Activation energy Jmax (J/mol)
  * `D_Jmax`: Deactivation energy of Jmax (J/mol)
  * `Topt_Jmax`: Optimal temperature for Jmax (K)
  * `TPU25`: Maximum rate of triose phosphate utilisation (μmol/m2/s)
  * `E_TPU`: Activation energy TPU (J/mol)
  * `D_TPU`: Deactivation energy of TPU (J/mol)


<a target='_blank' href='https://github.com/JuliaLang/julia/blob/17cfb8e65ead377bf1b4598d8a9869144142c84e/base/docs/Docs.jl#L473-L507' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.C4' href='#Ecophys.Photosynthesis.C4'>#</a>
**`Ecophys.Photosynthesis.C4`** &mdash; *Type*.



```julia
C4(Sco25 = 2590.0, E_Sco = -24.46e3, Kmc25 = 650.0, E_Kmc = 79.43e3, Kmo25 = 450e3, 
   E_Kmo = 36380.0, Vcmax25 = 120.0, E_Vcmax = 65.33, theta = 0.7, Phi2 = 0.83, sigma2 = 0.5, 
   beta = 0.85, fQ = 1.0, fpseudo = 0.1, h = 4.0, Jmax25 = 230.0, E_Jmax = 48e3, D_Jmax = 200e3, 
   Topt_Jmax = 300.5, x = 0.4, alpha = 0.1, kp25 = 0.7, E_kp = 46.39e3, gbs = 0.003, Rd25 = 1.2, 
   E_Rd = 46.39e3, gso = 0.01, a1 = 0.9, b1 = 0.15e-3)
```

Data structure to store all the parameters for the C3 photosynthesis model.

**Arguments**

  * `Sco25`: Sc/o parameter at 25 C
  * `E_Sco`: Apparent activation energy of Sc/o (J/mol)
  * `Kmc25`: Km for CO2 at 25 C (μmol/mol)
  * `E_Kmc3`: Activation energy of Kmc (J/mol)
  * `Kmo25`: Km for O2 at 25 C (umol/mol)
  * `E_Kmo`: Activation energy of Kmo (J/mol)
  * `Vcmax25`: Maximum rate of carboxylation at 25 C (μmol/m2/s)
  * `E_Vcmax`: Activation energy of Vcmax (J/mol)
  * `theta`: Curvature parameter
  * `Phi2`: Low-light PSII quantum yield
  * `sigma2`: Partitioning of excitation between PSII and PSI
  * `beta`: Leaf absorptance of PAR
  * `fQ`: Fraction of electrons at reduced plastoquinone that follow the Q-cycle
  * `fpseudo`: Fraction of electrons at PSI that follow cyclic transport around PSI
  * `h`: Number of protons required to produce one ATP
  * `Jmax25`: Maximum rate of electron transport (μmol/m2/s)
  * `E_Jmax`: Activation energy Jmax (J/mol)
  * `D_Jmax`: Deactivation energy of Jmax (J/mol)
  * `Topt_Jmax`: Entropy coefficient of Jmax (J/mol/K)
  * `x`: Fraction of electron transport partitioned to mesophyll cells
  * `alpha`: Fraction of O2 evolution occuring in the bundle sheath
  * `kp25`: Initial carboxylation efficiency of the PEP carboxylase (mol/m2/s)
  * `E_kp`: Activation energy of kp (J/mol)
  * `gbs`: Bundle sheath conductance (mol/m^2/s)
  * `Rd25:`: Respiration rate at 25 C (μmol/m2/s)
  * `E_Rd`: Activation energy of Rd (J/mol)
  * `gso`: Minimum stomatal conductance to fluxes of CO2 in darkness (mol/m2/s)
  * `a1`: Empirical parameter in gs formula
  * `b1`: Empirical parameter in gs formula (1/kPa)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/FvCB/C4.jl#LL9-L48' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.C4Q' href='#Ecophys.Photosynthesis.C4Q'>#</a>
**`Ecophys.Photosynthesis.C4Q`** &mdash; *Type*.



```julia
C4(Sco25 = 2590.0, E_Sco = -24.46e3J/mol, Kmc25 = 650.0μmol/mol, E_Kmc = 79.43e3J/mol,
   Kmo25 = 450e3μmol/mol, E_Kmo = 36380.0J/mol, Vcmax25 = 120.0μmol/m^2/s, E_Vcmax = 65.33J/mol,
   theta = 0.7, Phi2 = 0.83, sigma2 = 0.5, beta = 0.85, fQ = 1.0, fpseudo = 0.1, h = 4.0, 
   Jmax25 = 230.0μmol/m^2/s, E_Jmax = 48e3J/mol, D_Jmax = 200e3J/mol, Topt_Jmax = 300.5K, 
   x = 0.4, alpha = 0.1, kp25 = 0.7mol/m^2/s, E_kp = 46.39e3J/mol, gbs = 0.003mol/m^2/s, 
   Rd25 = 1.2μmol/m^2/s, E_Rd = 46.39e3J/mol, gso = 0.01mol/m^2/s, a1 = 0.9, b1 = 0.15e-3/Pa)
```

Data structure to store all the parameters for the C4 photosynthesis model using `Quantity` objects from Unitful.jl.

**Arguments**

  * `Sco25`: Sc/o parameter at 25 C
  * `E_Sco`: Apparent activation energy of Sc/o (J/mol)
  * `Kmc25`: Km for CO2 at 25 C (μmol/mol)
  * `E_Kmc3`: Activation energy of Kmc (J/mol)
  * `Kmo25`: Km for O2 at 25 C (umol/mol)
  * `E_Kmo`: Activation energy of Kmo (J/mol)
  * `Vcmax25`: Maximum rate of carboxylation at 25 C (μmol/m2/s)
  * `E_Vcmax`: Activation energy of Vcmax (J/mol)
  * `theta`: Curvature parameter
  * `Phi2`: Low-light PSII quantum yield
  * `sigma2`: Partitioning of excitation between PSII and PSI
  * `beta`: Leaf absorptance of PAR
  * `fQ`: Fraction of electrons at reduced plastoquinone that follow the Q-cycle
  * `fpseudo`: Fraction of electrons at PSI that follow cyclic transport around PSI
  * `h`: Number of protons required to produce one ATP
  * `Jmax25`: Maximum rate of electron transport (μmol/m2/s)
  * `E_Jmax`: Activation energy Jmax (J/mol)
  * `D_Jmax`: Deactivation energy of Jmax (J/mol)
  * `Topt_Jmax`: Entropy coefficient of Jmax (J/mol/K)
  * `x`: Fraction of electron transport partitioned to mesophyll cells
  * `alpha`: Fraction of O2 evolution occuring in the bundle sheath
  * `kp25`: Initial carboxylation efficiency of the PEP carboxylase (mol/m2/s)
  * `E_kp`: Activation energy of kp (J/mol)
  * `gbs`: Bundle sheath conductance (mol/m^2/s)
  * `Rd25:`: Respiration rate at 25 C (μmol/m2/s)
  * `E_Rd`: Activation energy of Rd (J/mol)
  * `gso`: Minimum stomatal conductance to fluxes of CO2 in darkness (mol/m2/s)
  * `a1`: Empirical parameter in gs formula
  * `b1`: Empirical parameter in gs formula (1/kPa)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/FvCB/C4.jl#LL87-L128' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.A_gs' href='#Ecophys.Photosynthesis.A_gs'>#</a>
**`Ecophys.Photosynthesis.A_gs`** &mdash; *Function*.



```julia
A_gs(par::FvCB, PAR, RH, Tleaf, Ca, gb)
```

Calculate net CO2 assimilation (umol/m2/s), transpiration (mmol/m2/s) and stomatal condutance to fluxes of CO2 (mol/m2/s) as a function of photosynthetically active radiation (PAR, umol/m2/s), relative humidity (RH, %), leaf temperature (Tleaf, K), air CO2 partial pressure (Ca, μmol/mol), oxygen (O2, μmol/mol) and boundary layer  conductance to CO2 (gb, mol/m2/s). Environmental inputs must be scalar. 


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/FvCB/C3.jl#LL162-L170' class='documenter-source'>source</a><br>


<a id='Boundary-layer-conductance'></a>

<a id='Boundary-layer-conductance-1'></a>

## Boundary layer conductance

<a id='Ecophys.Photosynthesis.gb' href='#Ecophys.Photosynthesis.gb'>#</a>
**`Ecophys.Photosynthesis.gb`** &mdash; *Function*.



```julia
gb(p::gbType, ws, Tl, Ta, P)
```

Compute boundary layer conductance for heat, water vapor and CO2.

**Arguments**

  * `p`: Model of boundary layer conductance
  * `ws`: Wind speed (m/s)
  * `Tl`: Leaf temperature (K)
  * `Ta`: Air temperature (K)
  * `P`: Air pressure (Pa)

**Returns**

  * `gbh`: Boundary layer conductance for heat (W/m²/K)
  * `gbw`: Boundary layer conductance for water vapor (mol/m²/s)
  * `gbc`: Boundary layer conductance for CO2 (mol/m²/s)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/BoundaryLayer.jl#LL12-L28' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.simplegb' href='#Ecophys.Photosynthesis.simplegb'>#</a>
**`Ecophys.Photosynthesis.simplegb`** &mdash; *Type*.



```julia
simplegb(; d = 0.01)
```

Simple model of boundary layer conductance.

**Arguments**

  * `d`: Characteristic leaf length (m)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/BoundaryLayer.jl#LL78-L85' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.simplegbQ' href='#Ecophys.Photosynthesis.simplegbQ'>#</a>
**`Ecophys.Photosynthesis.simplegbQ`** &mdash; *Type*.



```julia
simplegbQ(; d = 0.01m)
```

Simple model of boundary layer conductance using `Quantity` from Unitful.jl.

**Arguments**

  * `d`: Characteristic leaf length (m)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/BoundaryLayer.jl#LL90-L97' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.gbAngle' href='#Ecophys.Photosynthesis.gbAngle'>#</a>
**`Ecophys.Photosynthesis.gbAngle`** &mdash; *Type*.



```julia
gbAngle(; d = 0.01, ang = 0.0, ar = 1.0, fangm = 1.381, fangk = 0.034, 
α = 2.738, b0_0 = 0.455, d_b0 = 2.625, b0_n = 0.373, b0_KAR = 28.125,  db_0 = 0.085, 
d_db = 0.437, db_n = 5.175, db_KAR = 0.884,  β_0 = 3.362, d_β = 17.664, β_n = 4.727, 
β_KAR = 0.677)
```

Model of boundary layer conductance that accounts for inclination angle and leaf aspect ratio (see documentation for details).

**Arguments**

  * `d`: Characteristic leaf length (m)
  * `ang`: Leaf inclination angle (°)
  * `ar`: Leaf aspect ratio (length/width)
  * `fangm`: Maximum enhancement factor due to inclination angle
  * `fangk`: Exponent in response to inclination angle
  * `α`: Effect on back boundary layer conductance due to leaf inclination angle and aspect ratio
  * `b0_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_b0`: Parameter in the effect of aspect ratio (see documentation)
  * `b0_n`: Parameter in the effect of aspect ratio (see documentation)
  * `b0_KAR`: Parameter in the effect of aspect ratio (see documentation)
  * `db_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_db`: Parameter in the effect of aspect ratio (see documentation)
  * `db_n`: Parameter in the effect of aspect ratio (see documentation)
  * `db_KAR`: Parameter in the effect of aspect ratio (see documentation)
  * `β_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_β`: Parameter in the effect of aspect ratio (see documentation)
  * `β_n`: Parameter in the effect of aspect ratio (see documentation)
  * `β_KAR`: Parameter in the effect of aspect ratio (see documentation)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/BoundaryLayer.jl#LL110-L138' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.gbAngleQ' href='#Ecophys.Photosynthesis.gbAngleQ'>#</a>
**`Ecophys.Photosynthesis.gbAngleQ`** &mdash; *Type*.



```julia
gbAngleQ(; d = 0.01m, ang = 0.0, ar = 1.0, fangm = 1.381, fangk = 0.034, 
α = 2.738, b0_0 = 0.455, d_b0 = 2.625, b0_n = 0.373, b0_KAR = 28.125,  db_0 = 0.085, 
d_db = 0.437, db_n = 5.175, db_KAR = 0.884,  β_0 = 3.362, d_β = 17.664, β_n = 4.727, 
β_KAR = 0.677)
```

Model of boundary layer conductance that accounts for inclination angle and leaf aspect ratio (see documentation for details) using `Quantity` for Unitful.jl.

**Arguments**

  * `d`: Characteristic leaf length (m)
  * `ang`: Leaf inclination angle (°)
  * `ar`: Leaf aspect ratio (length/width)
  * `fangm`: Maximum enhancement factor due to inclination angle
  * `fangk`: Exponent in response to inclination angle
  * `α`: Effect on back boundary layer conductance due to leaf inclination angle and aspect ratio
  * `b0_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_b0`: Parameter in the effect of aspect ratio (see documentation)
  * `b0_n`: Parameter in the effect of aspect ratio (see documentation)
  * `b0_KAR`: Parameter in the effect of aspect ratio (see documentation)
  * `db_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_db`: Parameter in the effect of aspect ratio (see documentation)
  * `db_n`: Parameter in the effect of aspect ratio (see documentation)
  * `db_KAR`: Parameter in the effect of aspect ratio (see documentation)
  * `β_0`: Parameter in the effect of aspect ratio (see documentation)
  * `d_β`: Parameter in the effect of aspect ratio (see documentation)
  * `β_n`: Parameter in the effect of aspect ratio (see documentation)
  * `β_KAR`: Parameter in the effect of aspect ratio (see documentation)


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/BoundaryLayer.jl#LL165-L193' class='documenter-source'>source</a><br>


<a id='Energy-balance'></a>

<a id='Energy-balance-1'></a>

## Energy balance

<a id='Ecophys.Photosynthesis.SimpleOptical' href='#Ecophys.Photosynthesis.SimpleOptical'>#</a>
**`Ecophys.Photosynthesis.SimpleOptical`** &mdash; *Type*.



```julia
SimpleOptical(; αPAR = 0.85, αNIR = 0.20, ϵ = 0.95)
```

Simple optical properties of a leaf.

**Arguments**

  * `αPAR`: Absorption coefficient of PAR
  * `αNIR`: Absorption coefficient of NIR
  * `ϵ`: Emissivity for thermal radiation


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/EnergyBalance.jl#LL10-L20' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.energybalance' href='#Ecophys.Photosynthesis.energybalance'>#</a>
**`Ecophys.Photosynthesis.energybalance`** &mdash; *Function*.



```julia
energybalance(pgb, pAgs, pEb, PAR, NIR, ws, RH, Ta, Ca, P, O2)
```

Calculate the energy balance of a leaf.

**Arguments**

  * `pgb`: Boundary layer conductance model
  * `pAgs`: Photosynthesis and stomatal conductance model
  * `pEb`: Optical properties of the leaf
  * `PAR`: Photosynthetically active radiation (umol/m2/s)
  * `NIR`: Near-infrared radiation (W/m2)
  * `ws`: Wind speed (m/s)
  * `RH`: Relative humidity
  * `Ta`: Air temperature (K)
  * `Ca`: Atmospheric CO2 concentration (ppm)
  * `P`: Air pressure (kPa)
  * `O2`: Atmospheric O2 concentration (ppm)

**Details**

Inputs maybe be either `Real` or `Quantity` types (i.e., with physical units).  If `Quantity` types are used, the output will be a `Quantity` type.


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/EnergyBalance.jl#LL27-L50' class='documenter-source'>source</a><br>

<a id='Ecophys.Photosynthesis.solve_energy_balance' href='#Ecophys.Photosynthesis.solve_energy_balance'>#</a>
**`Ecophys.Photosynthesis.solve_energy_balance`** &mdash; *Function*.



```julia
solve_energy_balance(pgb, pAgs, pEb, PAR, NIR, ws, RH, Ta, Ca, P, O2)
```

Solve the energy balance of a leaf coupled to photosynthesis and transpiration.

**Arguments**

  * `pgb`: Boundary layer conductance model
  * `pAgs`: Photosynthesis and stomatal conductance model
  * `pEb`: Optical properties of the leaf
  * `PAR`: Photosynthetically active radiation (umol/m2/s)
  * `NIR`: Near-infrared radiation (W/m2)
  * `ws`: Wind speed (m/s)
  * `RH`: Relative humidity
  * `Ta`: Air temperature (K)
  * `Ca`: Atmospheric CO2 concentration (ppm)
  * `P`: Air pressure (kPa)
  * `O2`: Atmospheric O2 concentration (ppm)

**Details**

Inputs maybe be either `Real` or `Quantity` types from Unitful.jl (i.e., with  physical units). If `Quantity` types are used, the output will be a `Quantity`  type.


<a target='_blank' href='https://github.com/AleMorales/Ecophys.jl/blob/55df7383847197fc17020ade993be9a25c0177dc/src/Photosynthesis/EnergyBalance/EnergyBalance.jl#LL86-L110' class='documenter-source'>source</a><br>

