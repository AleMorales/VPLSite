
<a id='Module-Geometry'></a>

<a id='Module-Geometry-1'></a>

# Module Geometry




<a id='Scenes'></a>

<a id='Scenes-1'></a>

## Scenes

<a id='VPL.Geom.Scene' href='#VPL.Geom.Scene'>#</a>
**`VPL.Geom.Scene`** &mdash; *Type*.



```julia
Scene(graph, Float64)
```

Create a 3D scene from a `Graph` object (`g`). By default, double  floating precision will be used (`Float64`) but it is possible to generate a  version with a different precision by specifying the corresponding type as in  `Scene(g, Float32)`. The Scene object contains a mesh of triangles as well as colors and materials associated to each primitive.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL63-L71' class='documenter-source'>source</a><br>


```
Scene(scenes)
```

Merge multiple `Scene` objects into one.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL106-L110' class='documenter-source'>source</a><br>

<a id='VPL.add!' href='#VPL.add!'>#</a>
**`VPL.add!`** &mdash; *Function*.



```julia
add!(scene; mesh, color = nothing, material = nothing)
```

Manually add a 3D mesh to an existing `Scene` object (`scene`) with optional colors and materials


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL120-L125' class='documenter-source'>source</a><br>

<a id='VPL.Geom.colors-Tuple{VPL.Geom.Scene}' href='#VPL.Geom.colors-Tuple{VPL.Geom.Scene}'>#</a>
**`VPL.Geom.colors`** &mdash; *Method*.



```julia
colors(scene::Scene)
```

Extract the vector of `Colorant` objects stored inside a scene (used for rendering)


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL39-L43' class='documenter-source'>source</a><br>

<a id='VPL.Geom.mesh-Tuple{VPL.Geom.Scene}' href='#VPL.Geom.mesh-Tuple{VPL.Geom.Scene}'>#</a>
**`VPL.Geom.mesh`** &mdash; *Method*.



```julia
mesh(scene::Scene)
```

Extract the triangular mesh stored inside a scene (used for ray tracing & rendering)


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL52-L56' class='documenter-source'>source</a><br>

<a id='VPL.Geom.materials-Tuple{VPL.Geom.Scene}' href='#VPL.Geom.materials-Tuple{VPL.Geom.Scene}'>#</a>
**`VPL.Geom.materials`** &mdash; *Method*.



```julia
materials(scene::Scene)
```

Extract the vector of `Material` objects stored inside a scene (used for ray tracing)


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Scene.jl#LL45-L49' class='documenter-source'>source</a><br>


<a id='Turtle-geometry'></a>

<a id='Turtle-geometry-1'></a>

## Turtle geometry

<a id='VPL.Geom.Turtle-Union{Tuple{}, Tuple{Type{T}}, Tuple{T}} where T' href='#VPL.Geom.Turtle-Union{Tuple{}, Tuple{Type{T}}, Tuple{T}} where T'>#</a>
**`VPL.Geom.Turtle`** &mdash; *Method*.



```julia
Turtle(Float64, message)
```

Create a meshing turtle that can convert a `Graph` into a 3D mesh using  turtle operators, geometry primitives and methods of `feed!()`. By default,  the meshing turtle will generate geometry primitives with double floating  precision (`Float64`) but it is possible to generate a version with lower  precision as in `Turtle(Float32)`. The argument `message` is any user-defined object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL30-L39' class='documenter-source'>source</a><br>

<a id='VPL.Geom.head-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.head-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.head`** &mdash; *Method*.



```julia
head(turtle)
```

Extract the direction vector (a `Vec` object) of the head of the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL52-L56' class='documenter-source'>source</a><br>

<a id='VPL.Geom.up-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.up-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.up`** &mdash; *Method*.



```julia
up(turtle)
```

Extract the direction vector (a `Vec` object) of the back of the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL61-L65' class='documenter-source'>source</a><br>

<a id='VPL.Geom.arm-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.arm-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.arm`** &mdash; *Method*.



```julia
arm(turtle)
```

Extract the direction vector (a `Vec` object) of the arm of the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL70-L74' class='documenter-source'>source</a><br>

<a id='VPL.Geom.pos-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.pos-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.pos`** &mdash; *Method*.



```julia
pos(turtle)
```

Extract the current position of the turtle (a `Vec` object).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL79-L83' class='documenter-source'>source</a><br>

<a id='VPL.Geom.geoms-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.geoms-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.geoms`** &mdash; *Method*.



```julia
geoms(turtle)
```

Extract the 3D mesh generated by the turtle (a `Mesh` object).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL88-L92' class='documenter-source'>source</a><br>

<a id='VPL.Geom.colors-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.colors-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.colors`** &mdash; *Method*.



```julia
colors(turtle)
```

Extract the color objects associated to each geometry primitive that was fed to the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL141-L146' class='documenter-source'>source</a><br>

<a id='VPL.Geom.faces-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.faces-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.faces`** &mdash; *Method*.



```julia
geoms(turtle)
```

Extract the faces of the 3D mesh generated by the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL97-L101' class='documenter-source'>source</a><br>

<a id='VPL.Geom.materials-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.materials-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.materials`** &mdash; *Method*.



```julia
materials(turtle)
```

Extract the material objects associated to each geometry primitive that was fed to the turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Turtle.jl#LL126-L131' class='documenter-source'>source</a><br>

<a id='VPL.Geom.feed!' href='#VPL.Geom.feed!'>#</a>
**`VPL.Geom.feed!`** &mdash; *Function*.



```julia
feed!(turtle::Turtle; mesh::Mesh, color::Colorant = nothing, mat::Material = nothing)
```

General purpose method to feed a mesh to a turtle together with color and material. Note that all primitives provided by VPL are implemented as meshes, but this is a generic method for meshes that are constructed directly by the  user or imported from external software.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Graphs.jl#LL3-L10' class='documenter-source'>source</a><br>


```
feed!(turtle::Turtle, node::Node, vars = nothing)
```

Default method for `feed!()` that does not do anything. This allows the user to include nodes in a graph without an associated geometry.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Graphs.jl#LL19-L24' class='documenter-source'>source</a><br>


```
feed!(turtle::Turtle, g::Graph)
```

Process a `Graph` object with a turtle and generate the corresponding 3D mesh  from executing the different `feed!()` methods associated to the nodes in  the graph.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Graphs.jl#LL33-L39' class='documenter-source'>source</a><br>


```
feed!(turtle::Turtle, collection::AbstractArray)
feed!(turtle::Turtle, collection::Tuple)
```

Feed a turtle an array or tuple of objects (`collection`) with existing  `feed!()` methods.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Graphs.jl#LL72-L78' class='documenter-source'>source</a><br>

<a id='VPL.Geom.T' href='#VPL.Geom.T'>#</a>
**`VPL.Geom.T`** &mdash; *Type*.



```julia
T(to::Vec)
```

Node that translates a turtle to the new position `to` (a `Vec` object).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL17-L21' class='documenter-source'>source</a><br>

<a id='VPL.Geom.t!-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.t!-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.t!`** &mdash; *Method*.



```julia
t!(turtle; to = O())
```

Translate a turtle to the new position `to` (a `Vec` object). 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL7-L11' class='documenter-source'>source</a><br>

<a id='VPL.Geom.OR' href='#VPL.Geom.OR'>#</a>
**`VPL.Geom.OR`** &mdash; *Type*.



```julia
OR(head::Vec, up::Vec, arm::Vec)
```

Node that orients a turtle to a new direction by re-defining the local reference  system.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL42-L47' class='documenter-source'>source</a><br>

<a id='VPL.Geom.or!-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.or!-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.or!`** &mdash; *Method*.



```julia
or!(turtle; head = Z(), up = X(), arm = Y())
```

Orient a turtle to a new direction by re-defining the local reference system. The arguments `head`, `up` and `arm` should be of type `Vec`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL28-L33' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SET' href='#VPL.Geom.SET'>#</a>
**`VPL.Geom.SET`** &mdash; *Type*.



```julia
SET(to, head, up, arm)
```

Node that sets the position and orientation of a turtle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL70-L74' class='documenter-source'>source</a><br>

<a id='VPL.Geom.set!-Tuple{VPL.Geom.Turtle}' href='#VPL.Geom.set!-Tuple{VPL.Geom.Turtle}'>#</a>
**`VPL.Geom.set!`** &mdash; *Method*.



```julia
set!(turtle; to = O(), head = Z(), up = X(), arm = Y())
```

Set position and orientation of a turtle. The arguments `to`, `head`, `up` and  `arm` should be of type `Vec` and be passed as keyword arguments.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL56-L61' class='documenter-source'>source</a><br>

<a id='VPL.Geom.RU' href='#VPL.Geom.RU'>#</a>
**`VPL.Geom.RU`** &mdash; *Type*.



```julia
RU(angle)
```

Node that rotates a turtle around up axis. Angle must be in hexadecimal degrees  and the rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL100-L105' class='documenter-source'>source</a><br>

<a id='VPL.Geom.ru!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}' href='#VPL.Geom.ru!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}'>#</a>
**`VPL.Geom.ru!`** &mdash; *Method*.



```julia
ru!(turtle, angle)
```

Rotates a turtle around up axis. Angle must be in hexadecimal degrees and the  rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL85-L90' class='documenter-source'>source</a><br>

<a id='VPL.Geom.RA' href='#VPL.Geom.RA'>#</a>
**`VPL.Geom.RA`** &mdash; *Type*.



```julia
RA(angle)
```

Node that rotates a turtle around arm axis. Angle must be in hexadecimal degrees  and the rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL127-L132' class='documenter-source'>source</a><br>

<a id='VPL.Geom.ra!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}' href='#VPL.Geom.ra!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}'>#</a>
**`VPL.Geom.ra!`** &mdash; *Method*.



```julia
ra!(turtle, angle)
```

Rotates a turtle around arm axis. Angle must be in hexadecimal degrees and the  rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL112-L117' class='documenter-source'>source</a><br>

<a id='VPL.Geom.RH' href='#VPL.Geom.RH'>#</a>
**`VPL.Geom.RH`** &mdash; *Type*.



```julia
RH(angle)
```

Node that rotates a turtle around head axis. Angle must be in hexadecimal  degrees and the rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL154-L159' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rh!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}' href='#VPL.Geom.rh!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}'>#</a>
**`VPL.Geom.rh!`** &mdash; *Method*.



```julia
rh!(turtle, angle)
```

Rotate turtle around head axis. Angle must be in hexadecimal degrees and the  rotation is clockwise.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL139-L144' class='documenter-source'>source</a><br>

<a id='VPL.Geom.F' href='#VPL.Geom.F'>#</a>
**`VPL.Geom.F`** &mdash; *Type*.



```julia
F(dist)
```

Moves a turtle forward a given distance.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL176-L180' class='documenter-source'>source</a><br>

<a id='VPL.Geom.f!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}' href='#VPL.Geom.f!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}'>#</a>
**`VPL.Geom.f!`** &mdash; *Method*.



```julia
f!(turtle, dist)
```

Move turtle forward a given distance.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL166-L170' class='documenter-source'>source</a><br>

<a id='VPL.Geom.RV' href='#VPL.Geom.RV'>#</a>
**`VPL.Geom.RV`** &mdash; *Type*.



```julia
RV(strength)
```

Rotates the turtle towards the Z axis. See documentation for `rv!` for details.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL259-L263' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rv!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}' href='#VPL.Geom.rv!-Union{Tuple{UT}, Tuple{FT}, Tuple{VPL.Geom.Turtle{FT, UT}, FT}} where {FT, UT}'>#</a>
**`VPL.Geom.rv!`** &mdash; *Method*.



```julia
rv!(turtle, strength)
```

Rotates the turtle towards the Z axis. The angle of rotation is proportional to the cosine of the zenith angle of the turtle (i.e., angle between its head  and the vertical axis) with the absolute value of `strength` being the  proportion between the two. `strength` should vary between -1 and 1. If  `strength` is negative, the turtle rotates downwards (i.e., towards negative  values of Z axis), otherwise upwards.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Movements.jl#LL208-L217' class='documenter-source'>source</a><br>


<a id='D-vectors'></a>

<a id='D-vectors-1'></a>

## 3D vectors

<a id='VPL.Geom.Vec' href='#VPL.Geom.Vec'>#</a>
**`VPL.Geom.Vec`** &mdash; *Type*.



```julia
Vec(x, y, z)
```

3D vector or point with coordinates x, y and z.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL15-L19' class='documenter-source'>source</a><br>

<a id='VPL.Geom.O-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.O-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.O`** &mdash; *Method*.



```julia
O()
```

Returns the origin of the 3D coordinate system as a `Vec` object. By default, the coordinates will be in double  floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `O(Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL24-L29' class='documenter-source'>source</a><br>

<a id='VPL.Geom.X-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.X-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.X`** &mdash; *Method*.



```julia
X()
```

Returns an unit vector in the direction of the X axis as a `Vec` object. By default, the coordinates will be in double  floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `X(Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL74-L79' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Y-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Y-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Y`** &mdash; *Method*.



```julia
Y()
```

Returns an unit vector in the direction of the Y axis as a `Vec` object. By default, the coordinates will be in double  floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `Y(Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL54-L59' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Z-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Z-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Z`** &mdash; *Method*.



```julia
Z()
```

Returns an unit vector in the direction of the Z axis as a `Vec` object. By default, the coordinates will be in double  floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `Z(Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL34-L39' class='documenter-source'>source</a><br>

<a id='VPL.Geom.X-Tuple{FT} where FT' href='#VPL.Geom.X-Tuple{FT} where FT'>#</a>
**`VPL.Geom.X`** &mdash; *Method*.



```julia
X(s)
```

Returns scaled vector in the direction of the X axis with length `s` as a `Vec` object using the same floating point precision as `s`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL84-L89' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Y-Tuple{FT} where FT' href='#VPL.Geom.Y-Tuple{FT} where FT'>#</a>
**`VPL.Geom.Y`** &mdash; *Method*.



```julia
Y(s)
```

Returns scaled vector in the direction of the Y axis with length `s` as a `Vec` object using the same floating point precision as `s`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL64-L69' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Z-Tuple{FT} where FT' href='#VPL.Geom.Z-Tuple{FT} where FT'>#</a>
**`VPL.Geom.Z`** &mdash; *Method*.



```julia
Z(s)
```

Returns scaled vector in the direction of the Z axis with length `s` as a `Vec` object using the same floating point precision as `s`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Module_Geom.jl#LL44-L49' class='documenter-source'>source</a><br>


<a id='Geometry-primitives'></a>

<a id='Geometry-primitives-1'></a>

## Geometry primitives


<a id='Triangle'></a>

<a id='Triangle-1'></a>

### Triangle

<a id='VPL.Geom.Triangle-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.Triangle-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Triangle`** &mdash; *Method*.



```julia
Triangle(;length = 1.0, width = 1.0
```

Create a triangle with dimensions given by `length` and `width`, standard  location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/Triangle.jl#LL51-L56' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Triangle!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Triangle!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Triangle!`** &mdash; *Method*.



```julia
Triangle!(turtle; length = 1.0, width = 1.0, move = false,
          material = nothing, color = nothing)
```

Generate a triangle in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the triangle to.
  * `length`: Length of the triangle.
  * `width`: Width of the triangle.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A triangle mesh will be generated representing the triangle. The triangle will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the triangle aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL53-L82' class='documenter-source'>source</a><br>


<a id='Rectangle'></a>

<a id='Rectangle-1'></a>

### Rectangle

<a id='VPL.Geom.Rectangle-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.Rectangle-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Rectangle`** &mdash; *Method*.



```julia
Rectangle(;length = 1.0, width = 1.0)
```

Create a rectangle with dimensions given by `length` and width, standard location  and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/Rectangle.jl#LL51-L56' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Rectangle!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Rectangle!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Rectangle!`** &mdash; *Method*.



```julia
Rectangle!(turtle; length = 1.0, width = 1.0, move = false,
           material = nothing, color = nothing)
```

Generate a rectangle in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the rectangle to.
  * `length`: Length of the rectangle.
  * `width`: Width of the rectangle.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A triangle mesh will be generated representing the rectangle. The rectangle will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the rectangle aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL97-L126' class='documenter-source'>source</a><br>


<a id='Trapezoid'></a>

<a id='Trapezoid-1'></a>

### Trapezoid

<a id='VPL.Geom.Trapezoid-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.Trapezoid-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Trapezoid`** &mdash; *Method*.



```julia
Trapezoid(;length = 1.0, width = 1.0, ratio = 1.0)
```

Create a trapezoid with dimensions given by `length` and the larger `width` and the `ratio` between the smaller and larger widths. The trapezoid is generted at  the standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/Trapezoid.jl#LL50-L56' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Trapezoid!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Trapezoid!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Trapezoid!`** &mdash; *Method*.



```julia
Trapezoid!(turtle; length = 1.0, width = 1.0, ratio = 1.0, move = false,
material = nothing, color = nothing)
```

Generate a trapezoid in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the trapezoid to.
  * `length`: Length of the trapezoid.
  * `width`: Width of the base of the trapezoid.
  * `ratio`: Ratio between the width of the top and base of the trapezoid.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A triangle mesh will be generated representing the trapezoid. The trapezoid will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the trapezoid aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL142-L172' class='documenter-source'>source</a><br>


<a id='Ellipse'></a>

<a id='Ellipse-1'></a>

### Ellipse

<a id='VPL.Geom.Ellipse-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.Ellipse-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Ellipse`** &mdash; *Method*.



```julia
Ellipse(;length = 1.0, width = 1.0, n = 20)
```

Create an  ellipse with dimensions given by `length` and `width`, discretized  into `n` triangles (must be even) and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/Ellipse.jl#LL62-L67' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Ellipse!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.Ellipse!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.Ellipse!`** &mdash; *Method*.



```julia
Ellipse!(turtle; length = 1.0, width = 1.0, n = 20, move = false,
         material = nothing, color = nothing)
```

Generate an ellipse in front of a turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the ellipse to.
  * `length`: Length of the ellipse.
  * `width`: Width of the ellipse.
  * `n`: Number of triangles of the mesh approximating the ellipse (an integer).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A triangle mesh will be generated with `n` triangles that approximates an ellipse. The ellipse will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the ellipse aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL7-L37' class='documenter-source'>source</a><br>


<a id='Hollow-cylinder'></a>

<a id='Hollow-cylinder-1'></a>

### Hollow cylinder

<a id='VPL.Geom.HollowCylinder-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCylinder-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCylinder`** &mdash; *Method*.



```julia
HollowCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

Create a hollow cylinder with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles (must be even) and standard location and orientation.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/HollowCylinder.jl#LL113-L118' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowCylinder!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCylinder!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCylinder!`** &mdash; *Method*.



```julia
HollowCylinder!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false,
material = nothing, color = nothing)
```

Generate a hollow cylinder in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the hollow cylinder to.
  * `length`: Length of the ellipse at the base of the hollow cylinder.
  * `width`: Width of the ellipse at the base of the hollow cylinder.
  * `height`: Height of the hollow cylinder.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the hollow cylinder. The cylinder will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL280-L311' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidCylinder-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCylinder-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCylinder`** &mdash; *Method*.



```julia
SolidCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 80)
```

Create a solid cylinder with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles (must be even) and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/SolidCylinder.jl#LL108-L113' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidCylinder!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCylinder!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCylinder!`** &mdash; *Method*.



```julia
SolidCylinder!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 80, move = false,
material = nothing, color = nothing)
```

Generate a solid cylinder in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the solid cylinder to.
  * `length`: Length of the ellipse at the base of the solid cylinder.
  * `width`: Width of the ellipse at the base of the solid cylinder.
  * `height`: Height of the solid cylinder.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the solid cylinder. The cylinder will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL472-L503' class='documenter-source'>source</a><br>


<a id='Hollow-cone'></a>

<a id='Hollow-cone-1'></a>

### Hollow cone

<a id='VPL.Geom.HollowCone-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCone-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCone`** &mdash; *Method*.



```julia
HollowCone(;length = 1.0, width = 1.0, height = 1.0, n = 20)
```

Create a hollow cone with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles (must be even) and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/HollowCone.jl#LL80-L85' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowCone!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCone!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCone!`** &mdash; *Method*.



```julia
HollowCone!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 20, move = false,
material = nothing, color = nothing)
```

Generate a hollow cone in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the hollow cone to.
  * `length`: Length of the ellipse at the base of the hollow cone.
  * `width`: Width of the ellipse at the base of the hollow cone.
  * `height`: Height of the hollow cone.
  * `n`: Number of triangles in the mesh.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the hollow cone. The cone will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL187-L218' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidCone-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCone-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCone`** &mdash; *Method*.



```julia
SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

Create a solid cone with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles (must be even) and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/SolidCone.jl#LL71-L76' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidCone!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCone!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCone!`** &mdash; *Method*.



```julia
SolidCone!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false,
material = nothing, color = nothing)
```

Generate a solid frustum in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the solid cone to.
  * `length`: Length of the ellipse at the base of the solid cone.
  * `width`: Width of the ellipse at the base of the solid cone.
  * `height`: Height of the solid cone.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the solid cone. The cone will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL378-L409' class='documenter-source'>source</a><br>


<a id='Cube'></a>

<a id='Cube-1'></a>

### Cube

<a id='VPL.Geom.SolidCube-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCube-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCube`** &mdash; *Method*.



```julia
SolidCube(;length = 1.0, width = 1.0, height = 1.0)
```

Create a solid cube with dimensions given by `length`, `width` and `height`,  standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/SolidCube.jl#LL64-L69' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidCube!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.SolidCube!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidCube!`** &mdash; *Method*.



```julia
SolidCube!(turtle; length = 1.0, width = 1.0, height = 1.0, move = false,
material = nothing, color = nothing)
```

Generate a solid cube in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the solid cube to.
  * `length`: Length of the rectangle at the base of the solid cube.
  * `width`: Width of the rectangle at the base of the solid cube.
  * `height`: Height of the solid cube.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated of a solid cube. The cube will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis  and `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL426-L456' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowCube-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCube-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCube`** &mdash; *Method*.



```julia
HollowCube(;length = 1.0, width = 1.0, height = 1.0)
```

Create a hollow cube with dimensions given by `length`, `width` and `height,   standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/HollowCube.jl#LL59-L64' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowCube!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.HollowCube!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowCube!`** &mdash; *Method*.



```julia
HollowCube!(turtle; length = 1.0, width = 1.0, height = 1.0, move = false,
material = nothing, color = nothing)
```

Generate a hollow cube in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the hollow cube to.
  * `length`: Length of the rectangle at the base of the hollow cube.
  * `width`: Width of the rectangle at the base of the hollow cube.
  * `height`: Height of the hollow cube.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated of a hollow cube. The cube will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis  and `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL234-L264' class='documenter-source'>source</a><br>


<a id='Solid-frustum'></a>

<a id='Solid-frustum-1'></a>

### Solid frustum

<a id='VPL.Geom.SolidFrustum-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.SolidFrustum-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidFrustum`** &mdash; *Method*.



```julia
SolidFrustum(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

Create a solid frustum with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/SolidFrustum.jl#LL112-L117' class='documenter-source'>source</a><br>

<a id='VPL.Geom.SolidFrustum!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.SolidFrustum!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.SolidFrustum!`** &mdash; *Method*.



```julia
SolidFrustum!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 80, move = false,
material = nothing, color = nothing)
```

Generate a solid frustum in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the solid frustum to.
  * `length`: Length of the ellipse at the base of the solid frustum.
  * `width`: Width of the ellipse at the base of the solid frustum.
  * `height`: Height of the solid frustum.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the solid frustum. The frustum will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL520-L551' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowFrustum-Union{Tuple{}, Tuple{FT}} where FT' href='#VPL.Geom.HollowFrustum-Union{Tuple{}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowFrustum`** &mdash; *Method*.



```julia
HollowFrustum(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

Create a hollow frustum with dimensions given by `length`, `width` and `height`,  discretized into `n` triangles (must be even) and standard location and orientation. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/HollowFrustum.jl#LL109-L114' class='documenter-source'>source</a><br>

<a id='VPL.Geom.HollowFrustum!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT' href='#VPL.Geom.HollowFrustum!-Union{Tuple{VPL.Geom.Turtle{FT}}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.HollowFrustum!`** &mdash; *Method*.



```julia
HollowFrustum!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false,
material = nothing, color = nothing)
```

Generate a hollow frustum in front of the turtle and feed it to a turtle.

**Arguments**

  * `turtle`: The turtle that we feed the hollow frustum to.
  * `length`: Length of the ellipse at the base of the hollow frustum.
  * `width`: Width of the ellipse at the base of the hollow frustum.
  * `height`: Height of the hollow frustum.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A mesh will be generated with n triangles that approximate the hollow frustum. The frustum will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and  `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL328-L359' class='documenter-source'>source</a><br>


<a id='Bounding-box'></a>

<a id='Bounding-box-1'></a>

### Bounding box

<a id='VPL.Geom.BBox-Union{Tuple{VPL.Geom.Mesh{VT}}, Tuple{VT}, Tuple{FT}} where {FT, VT<:SVector{3, FT}}' href='#VPL.Geom.BBox-Union{Tuple{VPL.Geom.Mesh{VT}}, Tuple{VT}, Tuple{FT}} where {FT, VT<:SVector{3, FT}}'>#</a>
**`VPL.Geom.BBox`** &mdash; *Method*.



```julia
BBox(m::Mesh)
```

Build a tight axis-aligned bounding box around a `Mesh` object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/BBox.jl#LL3-L7' class='documenter-source'>source</a><br>

<a id='VPL.Geom.BBox-Union{Tuple{FT}, Tuple{SVector{3, FT}, SVector{3, FT}}} where FT' href='#VPL.Geom.BBox-Union{Tuple{FT}, Tuple{SVector{3, FT}, SVector{3, FT}}} where FT'>#</a>
**`VPL.Geom.BBox`** &mdash; *Method*.



```julia
BBox(pmin::Vec, pmax::Vec)
```

Build an axis-aligned bounding box given the vector of minimum (`pmin`) and  maximum (`pmax`) coordinates.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Primitives/BBox.jl#LL27-L32' class='documenter-source'>source</a><br>


<a id='Generic-mesh'></a>

<a id='Generic-mesh-1'></a>

### Generic mesh

<a id='VPL.Geom.Mesh!-Union{Tuple{FT}, Tuple{VPL.Geom.Turtle{FT}, VPL.Geom.Mesh}} where FT' href='#VPL.Geom.Mesh!-Union{Tuple{FT}, Tuple{VPL.Geom.Turtle{FT}, VPL.Geom.Mesh}} where FT'>#</a>
**`VPL.Geom.Mesh!`** &mdash; *Method*.



```julia
Mesh!(turtle, m::Mesh; scale = Vec(1.0, 1.0, 1.0), move = false,
material = nothing, color = nothing)
```

Feed a pre-existing mesh to a turtle after scaling.

**Arguments**

  * `turtle`: The turtle that we feed the mesh to.
  * `m`: The pre-existing unscaled mesh in standard position and orientation.
  * `scale`: Vector with scaling factors for the x, y and z axes.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `material`: The material object for the ray tracer (optional).
  * `color`: The color of the ellipse for rendering (optional).

**Details**

A pre-existing mesh will be scaled (acccording to `scale`), rotate so that it is oriented in the same direction as the turtle and translated so that the mesh is generated in front of the turtle. A deep copy of the original mesh is made prior to any transformation.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

The material object must inherit from `Material` (see ray tracing documentation  for detail) and the color can be any type that inherits from `Colorant` (from  ColorTypes.jl).

**Return**

Returns `nothing` but modifies the `turtle` as a side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Turtle/Primitives.jl#LL577-L605' class='documenter-source'>source</a><br>


<a id='Rotations,-scaling-and-translations'></a>

<a id='Rotations,-scaling-and-translations-1'></a>

## Rotations, scaling and translations

<a id='VPL.Geom.scale!-Tuple{VPL.Geom.Mesh, SVector{3}}' href='#VPL.Geom.scale!-Tuple{VPL.Geom.Mesh, SVector{3}}'>#</a>
**`VPL.Geom.scale!`** &mdash; *Method*.



```julia
scale!(m::Mesh, Vec)
```

Scale a mesh `m` along the three axes provided by `vec`


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL16-L20' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rotatex!-Tuple{VPL.Geom.Mesh, Any}' href='#VPL.Geom.rotatex!-Tuple{VPL.Geom.Mesh, Any}'>#</a>
**`VPL.Geom.rotatex!`** &mdash; *Method*.



```julia
rotatex!(m::Mesh, θ)
```

Rotate a mesh `m` around the x axis by `θ` rad.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL26-L30' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rotatey!-Tuple{VPL.Geom.Mesh, Any}' href='#VPL.Geom.rotatey!-Tuple{VPL.Geom.Mesh, Any}'>#</a>
**`VPL.Geom.rotatey!`** &mdash; *Method*.



```julia
rotatey!(m::Mesh, θ)
```

Rotate a mesh `m` around the y axis by `θ` rad.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL36-L40' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rotatez!-Tuple{VPL.Geom.Mesh, Any}' href='#VPL.Geom.rotatez!-Tuple{VPL.Geom.Mesh, Any}'>#</a>
**`VPL.Geom.rotatez!`** &mdash; *Method*.



```julia
rotatez!(m::Mesh, θ)
```

Rotate a mesh `m` around the z axis by `θ` rad.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL46-L50' class='documenter-source'>source</a><br>

<a id='VPL.Geom.rotate!-Union{Tuple{VPL.Geom.Mesh}, Tuple{FT}} where FT' href='#VPL.Geom.rotate!-Union{Tuple{VPL.Geom.Mesh}, Tuple{FT}} where FT'>#</a>
**`VPL.Geom.rotate!`** &mdash; *Method*.



```julia
rotate!(m::Mesh; x::Vec, y::Vec, z::Vec)
```

Rotate a mesh `m` to a new coordinate system given by `x`, `y` and `z`


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL56-L60' class='documenter-source'>source</a><br>

<a id='VPL.Geom.translate!-Tuple{VPL.Geom.Mesh, SVector{3}}' href='#VPL.Geom.translate!-Tuple{VPL.Geom.Mesh, SVector{3}}'>#</a>
**`VPL.Geom.translate!`** &mdash; *Method*.



```julia
translate!(m::Mesh, v::Vec)
```

Translate the mesh `m` by vector `v`


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Transformations.jl#LL69-L73' class='documenter-source'>source</a><br>


<a id='Other-mesh-related-methods'></a>

<a id='Other-mesh-related-methods-1'></a>

## Other mesh-related methods

<a id='VPL.Geom.Mesh-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT<:AbstractFloat' href='#VPL.Geom.Mesh-Union{Tuple{}, Tuple{Type{FT}}, Tuple{FT}} where FT<:AbstractFloat'>#</a>
**`VPL.Geom.Mesh`** &mdash; *Method*.



```julia
Mesh()
```

Generate an empty triangular dense mesh that represents a primitive or 3D scene.  By default a `Mesh` object will only accept coordinates in double floating  precision (`Float64`) but a lower precision can be generated by specifying the  corresponding data type as in `Mesh(Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL30-L37' class='documenter-source'>source</a><br>

<a id='VPL.Geom.Mesh-Union{Tuple{Any}, Tuple{FT}, Tuple{Any, Any}, Tuple{Any, Any, Type{FT}}} where FT<:AbstractFloat' href='#VPL.Geom.Mesh-Union{Tuple{Any}, Tuple{FT}, Tuple{Any, Any}, Tuple{Any, Any, Type{FT}}} where FT<:AbstractFloat'>#</a>
**`VPL.Geom.Mesh`** &mdash; *Method*.



```julia
Mesh(nt, nv = nt*3)
```

Generate a triangular dense mesh with enough memory allocated to store `nt`  triangles and `nv` vertices. The behaviour is equivalent to generating an empty  mesh but may be computationally more efficient when appending a large number of  primitives. If a lower floating precision is required, this may be specified as an optional third argument as in `Mesh(10, 30, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL42-L50' class='documenter-source'>source</a><br>

<a id='VPL.Geom.ntriangles-Tuple{VPL.Geom.Mesh}' href='#VPL.Geom.ntriangles-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.Geom.ntriangles`** &mdash; *Method*.



```julia
ntriangles(mesh)
```

Extract the number of triangles in a mesh.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL11-L15' class='documenter-source'>source</a><br>

<a id='VPL.Geom.nvertices-Tuple{VPL.Geom.Mesh}' href='#VPL.Geom.nvertices-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.Geom.nvertices`** &mdash; *Method*.



```julia
nvertices(mesh)
```

The number of vertices in a mesh.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL18-L22' class='documenter-source'>source</a><br>

<a id='VPL.Geom.area-Tuple{VPL.Geom.Mesh}' href='#VPL.Geom.area-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.Geom.area`** &mdash; *Method*.



```julia
area(m::Mesh)
```

Total surface area of a mesh (as the sum of areas of individual triangles).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL102-L106' class='documenter-source'>source</a><br>

<a id='VPL.Geom.areas-Tuple{VPL.Geom.Mesh}' href='#VPL.Geom.areas-Tuple{VPL.Geom.Mesh}'>#</a>
**`VPL.Geom.areas`** &mdash; *Method*.



```julia
areas(m::Mesh)
```

A vector with the areas of the different triangles that form a mesh.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/Mesh.jl#LL111-L115' class='documenter-source'>source</a><br>

<a id='VPL.Geom.loadmesh-Tuple{Any}' href='#VPL.Geom.loadmesh-Tuple{Any}'>#</a>
**`VPL.Geom.loadmesh`** &mdash; *Method*.



```julia
loadmesh(filename)
```

Import a mesh from a file given by `filename`. Supported formats include stl, ply, obj and msh. By default, this will generate a `Mesh` object that uses double floating-point precision. However, a lower precision can be specified by passing the relevant data type as in `loadmesh(filename, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/MeshIO.jl#LL25-L32' class='documenter-source'>source</a><br>

<a id='VPL.Geom.savemesh-Tuple{Any}' href='#VPL.Geom.savemesh-Tuple{Any}'>#</a>
**`VPL.Geom.savemesh`** &mdash; *Method*.



```julia
savemesh(mesh; fileformat = STL_BINARY, filename)
```

Save a mesh into an external file using a variety of formats.

**Arguments**

  * `mesh`: Object of type `Mesh`.
  * `fileformat`: Format to store the mesh. This is a keyword argument.
  * `filename`: Name of the file in which to store the mesh.

**Details**

The `fileformat` should take one of the following arguments: `STL_BINARY`, `STL_ASCII`, `PLY_BINARY`, `PLY_ASCII` or `OBJ`. Note that these names should not be quoted as strings.

**Return**

This function does not return anything, it is executed for its side effect.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/2c98915077ee2368ff87ffe73fa8a98d21572d25/src/Geom/Mesh/MeshIO.jl#LL43-L60' class='documenter-source'>source</a><br>


```

```

