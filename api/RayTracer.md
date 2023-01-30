
<a id='Module-RayTracing'></a>

<a id='Module-RayTracing-1'></a>

# Module RayTracing




<a id='Turtle'></a>

<a id='Turtle-1'></a>

# Turtle

<a id='VPL.RayTracing.RTTurtle' href='#VPL.RayTracing.RTTurtle'>#</a>
**`VPL.RayTracing.RTTurtle`** &mdash; *Type*.



```julia
RTTurtle()
```

Create a `RTTurtle()` object that will parse a `Graph` object and store the materials associated to the different primitives. This type of turtle is automatically created by calls to `RTScene()` but the user may want to separately construct the geometry and  materials and manually combine them into a `RTScene` object for performance reasons.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL7-L14' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.materials' href='#VPL.RayTracing.materials'>#</a>
**`VPL.RayTracing.materials`** &mdash; *Function*.



```julia
materials(turtle)
```

Extract the array of materials stored inside a `RTTurtle` object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL20-L24' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.feedmaterial!' href='#VPL.RayTracing.feedmaterial!'>#</a>
**`VPL.RayTracing.feedmaterial!`** &mdash; *Function*.



```julia
feedmaterial!(turtle::RTTurtle, material::Material)
```

General purpose method to feed a material to a RT turtle. This should be used inside user's defined methods to add the material object with optical properties associated to the primitive.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL27-L33' class='documenter-source'>source</a><br>


```
feedmaterial!(turtle::RTTurtle, node::Node)
```

Default method for `feedmaterial!()` that does not do anything. Hence, the user can include nodes in a graph withour associated colors (the nodes should not generate geometry either).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL36-L41' class='documenter-source'>source</a><br>


```
feedmaterial!(turtle::RTTurtle, g::Graph)
```

Process a `Graph` object with a RT turtle and collect the materials defined in the graph, in  the same order in which the 3D mesh is created by the corresponding `feedgeom!()` method.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL44-L49' class='documenter-source'>source</a><br>


```
feedmaterial!(turtle::RTTurtle, collection::AbstractArray)
feedmaterial!(turtle::RTTurtle, collection::Tuple)
```

Feed a RT turtle an array or tuple of objects (`collection`) with existing `feedmaterial!()` methods.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/Turtle.jl#LL75-L80' class='documenter-source'>source</a><br>


<a id='RTScene'></a>

<a id='RTScene-1'></a>

# RTScene

<a id='VPL.RayTracing.Triangle-Tuple{StaticArraysCore.SVector{3}, StaticArraysCore.SVector{3}, StaticArraysCore.SVector{3}}' href='#VPL.RayTracing.Triangle-Tuple{StaticArraysCore.SVector{3}, StaticArraysCore.SVector{3}, StaticArraysCore.SVector{3}}'>#</a>
**`VPL.RayTracing.Triangle`** &mdash; *Method*.



```julia
Triangle(p1, p2, p3)
```

Create a ray tracing `Triangle` object given the three vertices `p1`, `p2` and `p3`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Geometry/Triangle.jl#LL18-L22' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Triangle-Tuple{VPL.Geom.Mesh}' href='#VPL.RayTracing.Triangle-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.RayTracing.Triangle`** &mdash; *Method*.



```julia
Triangle(mesh)
```

Create a vector of ray tracing `Triangle` objects from a `Mesh` object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Geometry/Triangle.jl#LL29-L33' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.RTScene' href='#VPL.RayTracing.RTScene'>#</a>
**`VPL.RayTracing.RTScene`** &mdash; *Type*.



```julia
RTScene(triangles, material_ids, materials)
```

Create a ray tracing scene for rendering from a vector of triangles (`triangles`), a vector of ids that  match each triangle to a material (`ids`) and the vector of material objects (`materials`).  This method will generally not be used by the author unless  the components of an `RTScene` were generated manually.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RTScene.jl#LL5-L12' class='documenter-source'>source</a><br>

<a id='VPL.add!' href='#VPL.add!'>#</a>
**`VPL.add!`** &mdash; *Function*.



```julia
add!(scene; mesh, material)
```

Add a 3D mesh with a corresponding material (`mesh` and `material`) to an existing `RTScene` object (`scene`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RTScene.jl#LL104-L108' class='documenter-source'>source</a><br>


```julia
add!(scene; mesh, color)
```

Manually add a 3D mesh with corresponding colors (`mesh` and `color`) to an  existing `GLScene` object (`scene`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Scene.jl#LL72-L77' class='documenter-source'>source</a><br>


<a id='RayTracer'></a>

<a id='RayTracer-1'></a>

# RayTracer

<a id='VPL.RayTracing.get_nw' href='#VPL.RayTracing.get_nw'>#</a>
**`VPL.RayTracing.get_nw`** &mdash; *Function*.



```julia
get_nw(s::Source)
```

Retrieve the number of wavelengths that rays from a source will contain.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/Source.jl#LL46-L50' class='documenter-source'>source</a><br>


```
get_nw(rt::RayTracer)
```

Retrieve the number of wavelengths being simulated by the ray tracer. See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RayTracer.jl#LL119-L124' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.RTSettings' href='#VPL.RayTracing.RTSettings'>#</a>
**`VPL.RayTracing.RTSettings`** &mdash; *Type*.



```julia
RTSettings(;parallel = false, pkill = 0.2, maxiter = 2, sampler = Random.Xoshiro(123456789),
            nx = 0, ny = 0, nz = 0, dx = 0.0, dy = 0.0, dz = 0.0)
```

Settings for the ray tracer: `parallel` indicates if the raytracer will run on a single core or make use of multiple cores in the machine based on Julia's multithreading support. `pkill` is the probably that a ray is terminated by the Russian roulette after it has been scattered a `maxiter` number of times. `sampler` is the pseudo-random number generator to be used by the ray tracer. `nx` and `ny` are the number of times the scene will be clone by the grid cloner in each direction along the x and y axis (e.g., setting `nx = 1` and `ny = 1`  will generate a grid of 3 x 3 clones of the original scene), whereas `dx` and `dy` will be distance at which each new clone will be generated (along the axis). `nz` is the number of times the scene will be cloned in the vertical direction. Unlike horizontal cloning, the vertical cloning is always done in the positive direction of `z` axis and the number of clones will be exactly `nz`. See VPL documentation for more details on the ray  tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RayTracer.jl#LL8-L21' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.RayTracer' href='#VPL.RayTracing.RayTracer'>#</a>
**`VPL.RayTracing.RayTracer`** &mdash; *Type*.



```julia
RayTracer(acceleration, grid, materials, sources, settings)
```

Create a ray tracer object from an acceleration structure built around a 3D mesh (`acceleration`), a grid cloner structure around the acceleration structure (`grid`), a vector of materials associated to the mesh (`materials`), a vector of sources of irradiance  (`sources`) and settings. (as generated by `RTSettings()`). See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RayTracer.jl#LL37-L43' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.trace!' href='#VPL.RayTracing.trace!'>#</a>
**`VPL.RayTracing.trace!`** &mdash; *Function*.



```julia
trace!(rt)
```

Run the ray tracing simulations. This function will overwrite the `power` component of any material object that is included in the scene. It returns the total number of rays being traced (primary and secondary). See VPL documentation for more details on the ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/RayTracer/RayTracer.jl#LL148-L154' class='documenter-source'>source</a><br>


<a id='Acceleration-structures'></a>

<a id='Acceleration-structures-1'></a>

# Acceleration structures

<a id='VPL.RayTracing.Naive' href='#VPL.RayTracing.Naive'>#</a>
**`VPL.RayTracing.Naive`** &mdash; *Type*.



```julia
Naive
```

Allow to run the ray tracer without an acceleration structure. This should be  assigned to the argument `acceleration` in the `RayTracer` function.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Acceleration/Naive.jl#LL4-L9' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.BVH' href='#VPL.RayTracing.BVH'>#</a>
**`VPL.RayTracing.BVH`** &mdash; *Type*.



```julia
BVH
```

Construct a Bounding Volume Hierarchy around the triangular meshes to  accelerate the ray tracer. This should be assigned to the argument `acceleration` in the `RayTracer` function, in combination with a corresponding `rule`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Acceleration/BVH.jl#LL64-L70' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.SAH' href='#VPL.RayTracing.SAH'>#</a>
**`VPL.RayTracing.SAH`** &mdash; *Type*.



```julia
SAH{K}(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node at the axis and location using the Surface Area Heuristics. To speed up the construction, only `K` cuts will be tested per axis. These cuts will correspond to the quantiles along each axis. The rule is parameterized by the minimum  number of triangles in a leaf node (`minN`) and the maximum depth of the tree  (`maxL`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Acceleration/BVH.jl#LL207-L216' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.AvgSplit' href='#VPL.RayTracing.AvgSplit'>#</a>
**`VPL.RayTracing.AvgSplit`** &mdash; *Type*.



```julia
AvgSplit(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node along the longest axis through the mean coordinate value. The rule is  parameterized by the minimum number of triangles in a leaf node (`minN`) and the maximum depth of the tree (`maxL`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Acceleration/BVH.jl#LL169-L176' class='documenter-source'>source</a><br>


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


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/Source.jl#LL33-L42' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.DirectionalSource' href='#VPL.RayTracing.DirectionalSource'>#</a>
**`VPL.RayTracing.DirectionalSource`** &mdash; *Function*.



```julia
DirectionalSource(box::AABB, θ, Φ, power, nrays)
DirectionalSource(scene::RTScene, θ, Φ, power, nrays)
```

Create a Directional source (including geometry and angle components) by providing an axis-aligned bounding box (`box`) or an `RTScene` object (`scene`) as well as the zenith (`θ`) and azimuth (`Φ`) angles, the power per ray (as in `Source`) and the number of rays to be generated. See VPL documentation for details on irradiance sources.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/Directional.jl#LL4-L12' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.PointSource' href='#VPL.RayTracing.PointSource'>#</a>
**`VPL.RayTracing.PointSource`** &mdash; *Type*.



```julia
PointSource(vec)
```

Create a point irradiance source geometry at given 3D location `vec`, defined as vector of Cartesian coordinates (`Vec(x, y, z)`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/SourceGeometry.jl#LL10-L15' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.LineSource' href='#VPL.RayTracing.LineSource'>#</a>
**`VPL.RayTracing.LineSource`** &mdash; *Type*.



```julia
LineSource(p, line)
```

Create a line irradiance source geometry given an origin (`p`) and a segment (`line`) both specified as vector of Cartesian coordinates (`Vec(x, y, z)`). This will create a line source between the points `p` and `p .+ line`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/SourceGeometry.jl#LL23-L29' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.AreaSource' href='#VPL.RayTracing.AreaSource'>#</a>
**`VPL.RayTracing.AreaSource`** &mdash; *Type*.



```julia
AreaSource(mesh)
```

Create an area irradiance source geometry given a triangular mesh.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/SourceGeometry.jl#LL45-L49' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.LambertianSource' href='#VPL.RayTracing.LambertianSource'>#</a>
**`VPL.RayTracing.LambertianSource`** &mdash; *Type*.



```julia
LambertianSource(x, y, z)
LambertianSource(axes)
```

Create a Lambertian irradiance source angle by given a local coordinate system as three separate `Vec` objects representing the axes (x, y, z) or as tuple containing the three axes. Rays will be generated towards the hemisphere defined by the `z` direction. See VPL documentation for details on irradiance sources.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/SourceAngle.jl#LL21-L29' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.FixedSource' href='#VPL.RayTracing.FixedSource'>#</a>
**`VPL.RayTracing.FixedSource`** &mdash; *Type*.



```julia
FixedSource(dir)
FixedSource(θ, Φ)
```

Create a fixed irradiance source by given a vector with the direction of the rays (dir) or zenith (θ) and azimuth (Φ) angles.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Sources/SourceAngle.jl#LL5-L11' class='documenter-source'>source</a><br>


<a id='Materials'></a>

<a id='Materials-1'></a>

# Materials

<a id='VPL.RayTracing.Sensor' href='#VPL.RayTracing.Sensor'>#</a>
**`VPL.RayTracing.Sensor`** &mdash; *Type*.



```julia
Sensor(nw::Int)
```

Create a sensor material object to store power for `nw` wavelengths. A sensor material will let rays pass through without altering the direction or irradiance. They will also not count for the total number of ray iterations.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Sensor.jl#LL12-L18' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Black' href='#VPL.RayTracing.Black'>#</a>
**`VPL.RayTracing.Black`** &mdash; *Type*.



```julia
Black(nw::Int)
```

Create a black material object to store power for `nw` wavelengths. See VPL documentation for details.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Black.jl#LL12-L17' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Lambertian' href='#VPL.RayTracing.Lambertian'>#</a>
**`VPL.RayTracing.Lambertian`** &mdash; *Type*.



```julia
Lambertian(;τ = 0.0, ρ = 0.0)
```

Create a `Lambertian` material object from the values of transmittance (`τ`)  and reflectance (`ρ`). When more than one wavelength is being simulated, a tuple  of values should be passed for each optical property (as in `τ = (0.1,0.2)`). 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Lambertian.jl#LL14-L20' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.Phong' href='#VPL.RayTracing.Phong'>#</a>
**`VPL.RayTracing.Phong`** &mdash; *Type*.



```julia
Phong(;τ = 0.0, ρd = 0.0, ρsmax = 0.0, n = 2)
```

Create a `Phong` material object from the values of transmittance (`τ`) diffuse  reflectance (`ρd`), maximum Phong specular reflectance (`ρsmax`) and `n` is the  specular exponent that controls the "Phong reflectance lobe". When more than one  wavelength is being simulated, a tuple of values should be passed for each  optical property (as in `τ = (0.1, 0.3)`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Phong.jl#LL15-L23' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.power' href='#VPL.RayTracing.power'>#</a>
**`VPL.RayTracing.power`** &mdash; *Function*.



```julia
power(material::Material)
```

Extract the power stored inside a material.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Material.jl#LL39-L43' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.reset!-Tuple{VPL.RayTracing.Material}' href='#VPL.RayTracing.reset!-Tuple{VPL.RayTracing.Material}'>#</a>
**`VPL.RayTracing.reset!`** &mdash; *Method*.



```julia
reset!(material::Material)
```

Reset the power stored inside a material back to zero


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Materials/Material.jl#LL21-L25' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.tau' href='#VPL.RayTracing.tau'>#</a>
**`VPL.RayTracing.tau`** &mdash; *Function*.



```julia
tau(vals...)
```

Generate values of transmisivity to be used in material object. `vals...` is a list of one or more comma separted values, corresponding to the different  wavelengths/wavebands to be simulated in a ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/utils.jl#LL6-L12' class='documenter-source'>source</a><br>

<a id='VPL.RayTracing.rho' href='#VPL.RayTracing.rho'>#</a>
**`VPL.RayTracing.rho`** &mdash; *Function*.



```julia
rho(vals...)
```

Generate values of reflectivity to be used in material object. `vals...` is a list of one or more comma separted values, corresponding to the different  wavelengths/wavebands to be simulated in a ray tracer.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/utils.jl#LL15-L21' class='documenter-source'>source</a><br>

