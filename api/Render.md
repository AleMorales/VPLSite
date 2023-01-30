
<a id='Module-Render'></a>

<a id='Module-Render-1'></a>

# Module Render




<a id='Scenes-for-rendering'></a>

<a id='Scenes-for-rendering-1'></a>

## Scenes for rendering

<a id='VPL.Render.GLScene' href='#VPL.Render.GLScene'>#</a>
**`VPL.Render.GLScene`** &mdash; *Type*.



```julia
GLScene(mesh, colors)
```

Create a 3D scene for rendering from a `Mesh` object (`m`) and colors associated to the different  primitives (`colors`). This method is useful when the user has generated separately the 3D mesh and array with colors, as otherwise other methods of `GLScene()` will be more useful.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Scene.jl#LL1-L7' class='documenter-source'>source</a><br>

<a id='VPL.add!-Tuple{Any}' href='#VPL.add!-Tuple{Any}'>#</a>
**`VPL.add!`** &mdash; *Method*.



```julia
add!(scene; mesh, color)
```

Manually add a 3D mesh with corresponding colors (`mesh` and `color`) to an  existing `GLScene` object (`scene`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Scene.jl#LL72-L77' class='documenter-source'>source</a><br>


<a id='Rendering-methods'></a>

<a id='Rendering-methods-1'></a>

## Rendering methods

<a id='VPL.Render.GLTurtle' href='#VPL.Render.GLTurtle'>#</a>
**`VPL.Render.GLTurtle`** &mdash; *Type*.



```julia
GLTurtle(colors, message)
```

Create a `GLTurtle()` object that will parse a `Graph` object and store the colors associated to the different primitives. This type of turtle is automatically created by calls to `GLScene()` and `render()` but the user may want to separately construct the geometry and colors and manually combine them into a `GLScene` object for  performance reasons. The argument `message` is any user-defined object.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL2-L10' class='documenter-source'>source</a><br>

<a id='VPL.Render.colors-Tuple{VPL.Render.GLTurtle}' href='#VPL.Render.colors-Tuple{VPL.Render.GLTurtle}'>#</a>
**`VPL.Render.colors`** &mdash; *Method*.



```julia
colors(turtle)
```

Extract the array of colors stored inside an `GLTurtle` object


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL16-L20' class='documenter-source'>source</a><br>

<a id='VPL.Render.feedcolor!' href='#VPL.Render.feedcolor!'>#</a>
**`VPL.Render.feedcolor!`** &mdash; *Function*.



```julia
feedcolor!(turtle::GLTurtle, color::Colorant)
```

General purpose method to feed a color to a GL turtle. This should be used inside user's defined methods to add any color object that inherits from `Colorant` from the package *Color*, for example, by using `RGB()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL23-L29' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, node::Node)
```

Default method for `feedcolor!()` that does not do anything. Hence, the user can include nodes in a graph withour associated colors (the nodes should not generate geometry either).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL32-L37' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, g::Graph)
```

Process a `Graph` object with a GL turtle and collect the colors defined in the graph, in the same order in which the 3D mesh is created by the corresponding `feedgeom!()` method.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL40-L45' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, collection::AbstractArray)
feedcolor!(turtle::GLTurtle, collection::Tuple)
```

Feed a GL turtle an array or tuple of objects (`collection`) with existing `feedcolor!()` methods.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Turtle.jl#LL70-L75' class='documenter-source'>source</a><br>

<a id='VPL.Render.render' href='#VPL.Render.render'>#</a>
**`VPL.Render.render`** &mdash; *Function*.



```julia
render(m::Mesh; kwargs...)
```

Render a mesh. This will create a new visualization (see Documentation for  details). Keyword arguments are passed to the `render(scene::GLScene)` method  and any unmatched keywords will be passed along to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL6-L12' class='documenter-source'>source</a><br>


```
render(scene::GLScene; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render a `GLScene` object. This will create a new visualization (see  Documentation for details). `normals = true` will draw arrows in the direction  of the normal vector for each triangle in the mesh, `wireframe = true` will draw  the edges of each triangle with black lines. Keyword arguments are passed to  `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL63-L71' class='documenter-source'>source</a><br>


```
render(graph::Graph, Float64; normals::Bool = false, message = nothing,
       wireframe::Bool = false, kwargs...)
```

Render the 3D mesh associated to a `Graph` object. This will create a new  visualization (see Documentation for details). `normals = true` will draw arrows  in the direction of the normal vector for each triangle in the mesh,  `wireframe = true` will draw the edges of each triangle with black lines.  Keyword arguments are passed to `Makie.mesh()`. The argument `message` is any user-defined object that will be stored in the turtles and hence available  within the `feedgeom!` and `feedcolor!` methods. By default, double  floating precision will be used (`Float64`) but it is possible to generate a  version with a different precision by specifying the corresponding type as in  `render(graph, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL77-L91' class='documenter-source'>source</a><br>


```
render(graphs::Vector{<:Graph}, Float64; normals::Bool = false, 
       wireframe::Bool = false, messsage = nothing, kwargs...)
```

Render the 3D mesh associated to an array of `Graph` objects. This will create a  new visualization (see Documentation for details). `normals = true` will draw  arrows in the direction of the normal vector for each triangle in the mesh,  `wireframe = true` will draw the edges of each triangle with black lines.  Keyword arguments are passed to `Makie.mesh()`. The argument `message` is any user-defined object that will be stored in the turtles and hence available  within the `feedgeom!` and `feedcolor!` methods. By default, double  floating precision will be used (`Float64`) but it is possible to generate a  version with a different precision by specifying the corresponding type as in  `render(graphs, Float32)`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL98-L112' class='documenter-source'>source</a><br>

<a id='VPL.Render.render!' href='#VPL.Render.render!'>#</a>
**`VPL.Render.render!`** &mdash; *Function*.



```julia
render!(source::Source{G, A, nw}; n = 20, alpha = 0.2)
```

Add a mesh representing the light source to a 3D scene. For each type of light source a triangular mesh will be created, where `n` is the number of triangles (see documentation of geometric primitives for details) and `alpha` is the transparency to be used for each triangle.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Render.jl#LL4-L11' class='documenter-source'>source</a><br>


```
render!(grid::GridCloner; alpha = 0.2)
```

Add a mesh representing the bounding boxes of the grid cloner to a 3D scene,  where `alpha` represents the transparency of each box.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Raytracer/Render.jl#LL27-L32' class='documenter-source'>source</a><br>


```
render!(m::Mesh; kwargs...)
```

Add a mesh to the visualization currently active. This will create a new  visualization (see Documentation for details). Keyword arguments are passed to  the `render!(scene::GLScene)` method and any unmatched keywords will be passed  along to `Makie.mesh!()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL17-L24' class='documenter-source'>source</a><br>

<a id='VPL.Render.export_scene-Tuple{}' href='#VPL.Render.export_scene-Tuple{}'>#</a>
**`VPL.Render.export_scene`** &mdash; *Method*.



```julia
export_scene(;scene, filename, kwargs...)
```

Export a screenshot of the current visualization (stored as `scene` as output of a call to `render`) as a PNG file store in the path given by `filename`  (including `.png` extension). Keyword arguments will be passed along to the  corresponding `save` method from Makie (see VPL documentation for details).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/95b9ec3af8f79b223271d3a3a2886919076df5ea/src/Render/Render.jl#LL124-L131' class='documenter-source'>source</a><br>

