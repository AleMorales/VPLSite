
<a id='Module-Sky'></a>

<a id='Module-Sky-1'></a>

# Module Sky



<a id='Sky.UniformSky' href='#Sky.UniformSky'>#</a>
**`Sky.UniformSky`** &mdash; *Type*.



```julia
UniformSky()
```

Model of uniform sky diffuse radiation. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL263-L267' class='documenter-source'>source</a><br>

<a id='Sky.StandardSky' href='#Sky.StandardSky'>#</a>
**`Sky.StandardSky`** &mdash; *Type*.



```julia
StandardSky()
```

Standard model of overcast sky diffuse radiation Moon & Spencer (1942). See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL291-L296' class='documenter-source'>source</a><br>

<a id='Sky.CIE' href='#Sky.CIE'>#</a>
**`Sky.CIE`** &mdash; *Type*.



```julia
CIE(type::Int; θₛ = 0.0, Φₛ = 0.0, rtol = sqrt(eps(Float64)), atol = 0.0,
```

maxevals = typemax(Int))

Create a standard CIE model of sky diffuse radiance as described by  Darula and Kittler (2002). The argument `type` can have values from 1 to 15 representing the 15 standard CIE models. θₛ and Φₛ are the zenith and azimuth angles of the solar disc. `rtol` and `atol` and `maxevals` are the relative tolerance, absolute tolerance and maximum number of function evaluation of the numerical integration algorithm. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL333-L343' class='documenter-source'>source</a><br>

<a id='Sky.radiance' href='#Sky.radiance'>#</a>
**`Sky.radiance`** &mdash; *Function*.



```julia
radiance(m, θ, Φ)
```

Calculate the radiance per unit of solid angle at zenith (θ) and azimuth (Φ)  angle normalized by diffuse radiance on the horizontal plane for a given model of diffuse radiation `m`. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL119-L125' class='documenter-source'>source</a><br>

<a id='Sky.radiosity' href='#Sky.radiosity'>#</a>
**`Sky.radiosity`** &mdash; *Function*.



```julia
radiosity(m, sky::SkySectors, cosine = true)
```

Calculate the radiosity of each section of `sky`(multiplied by cos(θ) if  `cosine = true`) normalized by diffuse radiance on the horizontal plane  for a given model of radiation `m`. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL142-L148' class='documenter-source'>source</a><br>

<a id='Sky.equal_solid_angles' href='#Sky.equal_solid_angles'>#</a>
**`Sky.equal_solid_angles`** &mdash; *Function*.



```julia
equal_solid_angles (ntheta, nphi)
```

Discretize the sky into `ntheta` zenith rings and a number of sectors per ring that is proportional to `sin(θ)`. The total number of sectors will be `ntheta*nphi`. Returns an object of type `SkySectors`. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL54-L60' class='documenter-source'>source</a><br>

<a id='Sky.equal_angle_intervals' href='#Sky.equal_angle_intervals'>#</a>
**`Sky.equal_angle_intervals`** &mdash; *Function*.



```julia
equal_angle_intervals(ntheta, nphi)
```

Discretize the sky into `ntheta` zenith rings of `nphi` sectors each assuming  the same angle intervals for each sector (Δθ = π/2/ntheta and ΔΦ = 2π/nphi).  Returns an object of type `SkySectors`. See package documentation for details.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL36-L42' class='documenter-source'>source</a><br>

<a id='Sky.sky' href='#Sky.sky'>#</a>
**`Sky.sky`** &mdash; *Function*.



```julia
sky(scene; Idir = 0.77, nrays_dir = 100_000, theta_dir = 0.0, phi_dir = 0.0, 
           Idif = 0.23, nrays_dif = 1_000_000, sky_model = StandardSky,
           dome_method = equal_solid_angles, ntheta = 9, nphi = 12, 
           kwargs...)
```

Create a vector of directional radiation sources representing diffuse and  direct solar radiation for a given scene.

**Arguments**

  * `scene`: A Scene object generated by VPL.
  * `Idir`: The direct solar radiation measured on the horizontal plane.
  * `nrays_dir`: The number of rays to be generated for direct solar radiation.
  * `theta_dir`: The zenith angle of the sun position (radians).
  * `phi_dir`: The azimuthal angle of the sun position (radians).
  * `Idif`: The diffuse solar radiation measured on the horizontal plane.
  * `nrays_dif`: The total number of rays to be generated diffuse solar radiation.
  * `sky_model`: The angular distribution of diffuse irradiance (`StandardSky`, `UniformSky` or `CIE`).
  * `dome_method`: The method to discretize hemisphere into patches for diffuse solar radiation (`equal_solid_angles` or `equal_angle_intervals`).
  * `ntheta`: The number of divisions along the zenith angle for `dome_method`.
  * `nphi`: The number of divisions along the azimuthal angle for `dome_method`.
  * `kwargs...`: Additional arguments to be used when `dome_method = CIE`

**Returns**

A vector of directional sources that can be used for ray tracing calculations in VPL. ```


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SkyDome.jl#LL185-L211' class='documenter-source'>source</a><br>

<a id='Sky.clear_sky' href='#Sky.clear_sky'>#</a>
**`Sky.clear_sky`** &mdash; *Function*.



```julia
clear_sky(;lat, DOY, t, altitude = 0.0, TL = 4.0)
```

Calculate global, direct and diffuse solar radiation on the horizontal plane using the clear sky model by Ineichen and Perez (2002).

**Arguments**

  * `lat`: latitude in radians
  * `DOY`: day of year
  * `f`: fraction of the day (0 = sunrise, 1 = sunset)
  * `altitude`: altitude above sea level in meters (default 0.0)
  * `TL`: Linke turbidity coefficient (default 4.0)

**Returns**

A named tuple with fields:

  * `Ig`: global solar radiation on the horizontal plane in W/m^2
  * `Idir`: direct solar radiation on the horizontal plane in W/m^2
  * `Idif`: diffuse solar radiation on the horizontal plane in W/m^2
  * `theta`: solar zenith angle in radians

**References**

Ineichen P., Perez R., A new airmass independent formulation for  the Linke turbidity coefficient, Solar Energy, Vol 73(3), pp.151–157, 2002.


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SolarIrradiance.jl#LL56-L79' class='documenter-source'>source</a><br>

<a id='Sky.waveband_conversion' href='#Sky.waveband_conversion'>#</a>
**`Sky.waveband_conversion`** &mdash; *Function*.



```julia
waveband_conversion(;Itype = :direct, waveband = :PAR, mode = :power)
```

Returns the conversion coefficient from solar radiation (W/m2) to a give  waveband in either power (W/m2) or photon flux (umol/m2/s). The coefficients are based on the Bird spectral model for a clear sky using June 21th in The  Netherlands (latitude 52° N).

**Arguments**

  * `Itype`: The type of solar radiation, either `:direct` or `:diffuse`.
  * `waveband`: The waveband of interest, one of `:PAR`, `:UV`, `:blue`, `:red`, `:green`, or `:NIR`.
  * `mode`: The physical units of the target, either `:power` (W/m^2) or `:flux` (mol/m^2/s).

**Examples**

```julia
waveband_conversion(Itype = :diffuse, waveband = :UV, mode = :flux)
waveband_conversion(waveband = :NIR)
```


<a target='_blank' href='https://github.com/AleMorales/Sky.jl/blob/47e5a2c5631880c7cc24f74c9d59b030ddbb5829/src/SolarIrradiance.jl#LL144-L162' class='documenter-source'>source</a><br>

