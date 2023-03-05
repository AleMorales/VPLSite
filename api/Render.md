
<a id='Module-Render'></a>

<a id='Module-Render-1'></a>

# Module Render




<a id='Rendering-methods'></a>

<a id='Rendering-methods-1'></a>

## Rendering methods

<a id='VPL.Render.render' href='#VPL.Render.render'>#</a>
**`VPL.Render.render`** &mdash; *Function*.



```julia
render(m::Mesh; kwargs...)
```

Render a mesh. This will create a new visualization (see Documentation for  details). Keyword arguments are passed to the `render(scene::Geom.Scene)` method  and any unmatched keywords will be passed along to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL6-L12' class='documenter-source'>source</a><br>


```
render(scene::Geom.Scene; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render a `Geom.Scene` object. This will create a new visualization (see  Documentation for details). `normals = true` will draw arrows in the direction  of the normal vector for each triangle in the mesh, `wireframe = true` will draw  the edges of each triangle with black lines. Keyword arguments are passed to  `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL63-L71' class='documenter-source'>source</a><br>


```
render(graph::Graph, Float64; normals::Bool = false, message = nothing,
       wireframe::Bool = false, kwargs...)
```

Render the 3D mesh associated to a `Graph` object. This will create a new  visualization (see Documentation for details). `normals = true` will draw arrows  in the direction of the normal vector for each triangle in the mesh,  `wireframe = true` will draw the edges of each triangle with black lines.  Keyword arguments are passed to `Makie.mesh()`. The argument `message` is any user-defined object that will be stored in the turtles and hence available  within the `feedgeom!` and `feedcolor!` methods. By default, double  floating precision will be used (`Float64`) but it is possible to generate a  version with a different precision by specifying the corresponding type as in  `render(graph, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL77-L91' class='documenter-source'>source</a><br>


```
render(graphs::Vector{<:Graph}, Float64; normals::Bool = false, 
       wireframe::Bool = false, messsage = nothing, kwargs...)
```

Render the 3D mesh associated to an array of `Graph` objects. This will create a  new visualization (see Documentation for details). `normals = true` will draw  arrows in the direction of the normal vector for each triangle in the mesh,  `wireframe = true` will draw the edges of each triangle with black lines.  Keyword arguments are passed to `Makie.mesh()`. The argument `message` is any user-defined object that will be stored in the turtles and hence available  within the `feedgeom!` and `feedcolor!` methods. By default, double  floating precision will be used (`Float64`) but it is possible to generate a  version with a different precision by specifying the corresponding type as in  `render(graphs, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL98-L112' class='documenter-source'>source</a><br>

<a id='VPL.Render.render!' href='#VPL.Render.render!'>#</a>
**`VPL.Render.render!`** &mdash; *Function*.



```julia
render!(m::Mesh; kwargs...)
```

Add a mesh to the visualization currently active. This will create a new  visualization (see Documentation for details). Keyword arguments are passed to  the `render!(scene::Geom.Scene)` method and any unmatched keywords will be passed  along to `Makie.mesh!()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL17-L24' class='documenter-source'>source</a><br>


```
render!(source::Source{G, A, nw}; n = 20, alpha = 0.2, point = false,
        scale = 0.2)
```

Add a mesh representing the light source to a 3D scene (if `point = false`) or a series of points representing the center of the light sources (if  `point = true`). When `point = false`, for each type of light source a  triangular mesh will be created, where `n` is the number of triangles (see  documentation of geometric primitives for details) and `alpha` is the  transparency to be used for each triangle. When `point = true`, only the center of the light source is rendered along with the normal vector at that point  (representative of the direction at which rays are generated). In the current version, `point = true` is only possible for directional light sources.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Raytracer/Render.jl#LL4-L17' class='documenter-source'>source</a><br>


```
render!(grid::GridCloner; alpha = 0.2)
```

Add a mesh representing the bounding boxes of the grid cloner to a 3D scene,  where `alpha` represents the transparency of each box.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Raytracer/Render.jl#LL55-L60' class='documenter-source'>source</a><br>

<a id='VPL.Render.export_scene-Tuple{}' href='#VPL.Render.export_scene-Tuple{}'>#</a>
**`VPL.Render.export_scene`** &mdash; *Method*.



```julia
export_scene(;scene, filename, kwargs...)
```

Export a screenshot of the current visualization (stored as `scene` as output of a call to `render`) as a PNG file store in the path given by `filename`  (including `.png` extension). Keyword arguments will be passed along to the  corresponding `save` method from Makie (see VPL documentation for details).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/7a132c2a4dc8604d7234cee76a1586daf23ba23e/src/Render/Render.jl#LL124-L131' class='documenter-source'>source</a><br>

