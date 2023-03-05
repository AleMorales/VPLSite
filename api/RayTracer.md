
<a id='Module-RayTracing'></a>

<a id='Module-RayTracing-1'></a>

# Module RayTracing




<a id='Meshes'></a>

<a id='Meshes-1'></a>

# Meshes

<a id='VPL.RayTracing.Triangle-Tuple{SVector{3}, SVector{3}, SVector{3}}' href='#VPL.RayTracing.Triangle-Tuple{SVector{3}, SVector{3}, SVector{3}}'>#</a>
**`VPL.RayTracing.Triangle`** &mdash; *Method*.



```julia
Triangle(p1, p2, p3)
```

Create a ray tracing `Triangle` object given the three vertices `p1`, `p2` and `p3`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Geometry/Triangle.jl#LL19-L23' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Triangle-Tuple{VPL.Geom.Mesh}' href='#VPL.RayTracing.Triangle-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.RayTracing.Triangle`** &mdash; *Method*.



```julia
Triangle(mesh)
```

Create a vector of ray tracing `Triangle` objects from a `Mesh` object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Geometry/Triangle.jl#LL30-L34' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Triangle-Tuple{VPL.Geom.Scene}' href='#VPL.RayTracing.Triangle-Tuple{VPL.Geom.Scene}'>#</a>
**`VPL.RayTracing.Triangle`** &mdash; *Method*.



```julia
Triangle(mesh)
```

Create a vector of ray tracing `Triangle` objects from a `Scene` object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Geometry/Triangle.jl#LL39-L43' class='documenter-source'>source</a><br>


<a id='RayTracer'></a>

<a id='RayTracer-1'></a>

# RayTracer

<a id='VPL.RayTracing.get_nw' href='#VPL.RayTracing.get_nw'>#</a>
**`VPL.RayTracing.get_nw`** &mdash; *Function*.



```julia
get_nw(s::Source)
```

Retrieve the number of wavelengths that rays from a source will contain.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/Source.jl#LL46-L50' class='documenter-source'>source</a><br>


```
get_nw(rt::RayTracer)
```

Retrieve the number of wavelengths being simulated by the ray tracer. See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/RayTracer/RayTracer.jl#LL145-L150' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.RTSettings' href='#VPL.RayTracing.RTSettings'>#</a>
**`VPL.RayTracing.RTSettings`** &mdash; *Type*.



```julia
RTSettings(;parallel = false, pkill = 0.2, maxiter = 2, sampler = Random.Xoshiro(123456789),
            nx = 3, ny = 3, nz = 0, dx = 0.0, dy = 0.0, dz = 0.0)
```

Settings for the ray tracer: `parallel` indicates if the raytracer will run on a single core or make use of multiple cores in the machine based on Julia's multithreading support. `pkill` is the probably that a ray is terminated by the Russian roulette after it has been scattered a `maxiter` number of times. `sampler` is the pseudo-random number generator to be used by the ray tracer. `nx` and `ny` are the number of times the scene will be clone by the grid cloner in each direction along the x and y axis (e.g., setting `nx = 1` and `ny = 1`  will generate a grid of 3 x 3 clones of the original scene), whereas `dx` and `dy` will be distance at which each new clone will be generated (along the axis). `nz` is the number of times the scene will be cloned in the vertical direction. Unlike horizontal cloning, the vertical cloning is always done in the positive direction of `z` axis and the number of clones will be exactly `nz`. See VPL documentation for more details on the ray  tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/RayTracer/RayTracer.jl#LL9-L22' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.accelerate' href='#VPL.RayTracing.accelerate'>#</a>
**`VPL.RayTracing.accelerate`** &mdash; *Function*.



```julia
accelerate(scene::Scene; settings = RTSettings(), acceleration = Naive, rule = nothing)
```

Create an `AccScene` object from a scene, settings and acceleration function  (choose from `Naive` or  `BVH`). The argument `rule` is only required for the  accelerator `BVH` and it must be an object of type `SAH` or `AvgSplit`  (it is ignored for the `Naive` accelerator). The `AccScene` object contains the acceleration structure and the grid cloner structure built on top of the  original 3D meshes in `scene`. See VPL documentation for details.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/RayTracer/RayTracer.jl#LL42-L51' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.RayTracer' href='#VPL.RayTracing.RayTracer'>#</a>
**`VPL.RayTracing.RayTracer`** &mdash; *Type*.



```julia
RayTracer(scene, materials, sources, settings)
```

Create a ray tracer object from an acceleration structure built around a 3D mesh, a grid cloner structure around the acceleration structure (`scene`), a vector of materials associated to the mesh (`materials`), a vector of sources of irradiance  (`sources`) and settings. (as generated by `RTSettings()`). See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/RayTracer/RayTracer.jl#LL61-L67' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.trace!' href='#VPL.RayTracing.trace!'>#</a>
**`VPL.RayTracing.trace!`** &mdash; *Function*.



```julia
trace!(rt)
```

Run the ray tracing simulations. This function will overwrite the `power` component of any material object that is included in the scene. It returns the total number of rays being traced (primary and secondary). See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/RayTracer/RayTracer.jl#LL174-L180' class='documenter-source'>source</a><br>


<a id='Acceleration-structures'></a>

<a id='Acceleration-structures-1'></a>

# Acceleration structures

<a id='VPL.RayTracing.Naive' href='#VPL.RayTracing.Naive'>#</a>
**`VPL.RayTracing.Naive`** &mdash; *Type*.



```julia
Naive
```

Allow to run the ray tracer without an acceleration structure. This should be  assigned to the argument `acceleration` in the `RayTracer` function.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Acceleration/Naive.jl#LL4-L9' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.BVH' href='#VPL.RayTracing.BVH'>#</a>
**`VPL.RayTracing.BVH`** &mdash; *Type*.



```julia
BVH
```

Construct a Bounding Volume Hierarchy around the triangular meshes to  accelerate the ray tracer. This should be assigned to the argument `acceleration` in the `RayTracer` function, in combination with a corresponding `rule`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Acceleration/BVH.jl#LL59-L65' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.SAH' href='#VPL.RayTracing.SAH'>#</a>
**`VPL.RayTracing.SAH`** &mdash; *Type*.



```julia
SAH{K}(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node at the axis and location using the Surface Area Heuristics. To speed up the construction, only `K` cuts will be tested per axis. These cuts will correspond to the quantiles along each axis. The rule is parameterized by the minimum  number of triangles in a leaf node (`minN`) and the maximum depth of the tree  (`maxL`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Acceleration/BVH.jl#LL202-L211' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.AvgSplit' href='#VPL.RayTracing.AvgSplit'>#</a>
**`VPL.RayTracing.AvgSplit`** &mdash; *Type*.



```julia
AvgSplit(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node along the longest axis through the mean coordinate value. The rule is  parameterized by the minimum number of triangles in a leaf node (`minN`) and the maximum depth of the tree (`maxL`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Acceleration/BVH.jl#LL164-L171' class='documenter-source'>source</a><br>


<a id='Sources'></a>

<a id='Sources-1'></a>

# Sources

<a id='VPL.RayTracing.Source' href='#VPL.RayTracing.Source'>#</a>
**`VPL.RayTracing.Source`** &mdash; *Type*.



```julia
Source(geom, angle, power::Number, nrays)
Source(geom, angle, power::Tuple, nrays)
```

Createn irradiance source given a source geometry, a source angle, the power per ray and the total number of rays to be generated from this source. When simulating more than one wavelength simultaneously, a tuple of power values should be given, of the same length as in the materials used in the scene. See VPL documentation for details on source geometries  and source angles.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/Source.jl#LL33-L42' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.DirectionalSource' href='#VPL.RayTracing.DirectionalSource'>#</a>
**`VPL.RayTracing.DirectionalSource`** &mdash; *Function*.



```julia
DirectionalSource(box::AABB, θ, Φ, radiosity, nrays)
DirectionalSource(scene::Scene, θ, Φ, radiosity, nrays)
```

Create a Directional source (including geometry and angle components) by providing an axis-aligned bounding box (`box`) or an `Scene` object (`scene`) as well as the zenith (`θ`) and azimuth (`Φ`) angles, the radiosity of the source and the number of rays to be generated.  Directional sources may generate incorrect results in the absence of a grid cloner that extendes the scenes. This is because the rays are generated from the upper face of the scene's bounding box. See VPL documentation for details on light sources.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/Directional.jl#LL4-L14' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.PointSource' href='#VPL.RayTracing.PointSource'>#</a>
**`VPL.RayTracing.PointSource`** &mdash; *Type*.



```julia
PointSource(vec)
```

Create a point irradiance source geometry at given 3D location `vec`, defined as vector of Cartesian coordinates (`Vec(x, y, z)`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/SourceGeometry.jl#LL10-L15' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.LineSource' href='#VPL.RayTracing.LineSource'>#</a>
**`VPL.RayTracing.LineSource`** &mdash; *Type*.



```julia
LineSource(p, line)
```

Create a line irradiance source geometry given an origin (`p`) and a segment (`line`) both specified as vector of Cartesian coordinates (`Vec(x, y, z)`). This will create a line source between the points `p` and `p .+ line`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/SourceGeometry.jl#LL23-L29' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.AreaSource' href='#VPL.RayTracing.AreaSource'>#</a>
**`VPL.RayTracing.AreaSource`** &mdash; *Type*.



```julia
AreaSource(mesh)
```

Create an area irradiance source geometry given a triangular mesh.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/SourceGeometry.jl#LL45-L49' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.LambertianSource' href='#VPL.RayTracing.LambertianSource'>#</a>
**`VPL.RayTracing.LambertianSource`** &mdash; *Type*.



```julia
LambertianSource(x, y, z)
LambertianSource(axes)
```

Create a Lambertian irradiance source angle by given a local coordinate system as three separate `Vec` objects representing the axes (x, y, z) or as tuple containing the three axes. Rays will be generated towards the hemisphere defined by the `z` direction. See VPL documentation for details on irradiance sources.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/SourceAngle.jl#LL21-L29' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.FixedSource' href='#VPL.RayTracing.FixedSource'>#</a>
**`VPL.RayTracing.FixedSource`** &mdash; *Type*.



```julia
FixedSource(dir)
FixedSource(θ, Φ)
```

Create a fixed irradiance source by given a vector with the direction of the rays (dir) or zenith (θ) and azimuth (Φ) angles.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Sources/SourceAngle.jl#LL5-L11' class='documenter-source'>source</a><br>


<a id='Materials'></a>

<a id='Materials-1'></a>

# Materials

<a id='VPL.RayTracing.Sensor' href='#VPL.RayTracing.Sensor'>#</a>
**`VPL.RayTracing.Sensor`** &mdash; *Type*.



```julia
Sensor(nw::Int)
```

Create a sensor material object to store power for `nw` wavelengths. A sensor material will let rays pass through without altering the direction or irradiance. They will also not count for the total number of ray iterations.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Sensor.jl#LL12-L18' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Black' href='#VPL.RayTracing.Black'>#</a>
**`VPL.RayTracing.Black`** &mdash; *Type*.



```julia
Black(nw::Int)
```

Create a black material object to store power for `nw` wavelengths. See VPL documentation for details.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Black.jl#LL12-L17' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Lambertian' href='#VPL.RayTracing.Lambertian'>#</a>
**`VPL.RayTracing.Lambertian`** &mdash; *Type*.



```julia
Lambertian(;τ = 0.0, ρ = 0.0)
```

Create a `Lambertian` material object from the values of transmittance (`τ`)  and reflectance (`ρ`). When more than one wavelength is being simulated, a tuple  of values should be passed for each optical property (as in `τ = (0.1,0.2)`). 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Lambertian.jl#LL14-L20' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Phong' href='#VPL.RayTracing.Phong'>#</a>
**`VPL.RayTracing.Phong`** &mdash; *Type*.



```julia
Phong(;τ = 0.0, ρd = 0.0, ρsmax = 0.0, n = 2)
```

Create a `Phong` material object from the values of transmittance (`τ`) diffuse  reflectance (`ρd`), maximum Phong specular reflectance (`ρsmax`) and `n` is the  specular exponent that controls the "Phong reflectance lobe". When more than one  wavelength is being simulated, a tuple of values should be passed for each  optical property (as in `τ = (0.1, 0.3)`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Phong.jl#LL15-L23' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.power' href='#VPL.RayTracing.power'>#</a>
**`VPL.RayTracing.power`** &mdash; *Function*.



```julia
power(material::Material)
```

Extract the power stored inside a material.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Material.jl#LL38-L42' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.reset!-Tuple{VPL.Material}' href='#VPL.RayTracing.reset!-Tuple{VPL.Material}'>#</a>
**`VPL.RayTracing.reset!`** &mdash; *Method*.



```julia
reset!(material::Material)
```

Reset the power stored inside a material back to zero


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/Materials/Material.jl#LL20-L24' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.tau' href='#VPL.RayTracing.tau'>#</a>
**`VPL.RayTracing.tau`** &mdash; *Function*.



```julia
tau(vals...)
```

Generate values of transmisivity to be used in material object. `vals...` is a list of one or more comma separted values, corresponding to the different  wavelengths/wavebands to be simulated in a ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/utils.jl#LL6-L12' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.rho' href='#VPL.RayTracing.rho'>#</a>
**`VPL.RayTracing.rho`** &mdash; *Function*.



```julia
rho(vals...)
```

Generate values of reflectivity to be used in material object. `vals...` is a list of one or more comma separted values, corresponding to the different  wavelengths/wavebands to be simulated in a ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Raytracer/utils.jl#LL15-L21' class='documenter-source'>source</a><br>

