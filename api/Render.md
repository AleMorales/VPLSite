
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


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Scene.jl#LL1-L7' class='documenter-source'>source</a><br>

<a id='VPL.Render.add!-Tuple{}' href='#VPL.Render.add!-Tuple{}'>#</a>
**`VPL.Render.add!`** &mdash; *Method*.



```julia
add!(; scene, mesh, color)
```

Manually add a 3D mesh with corresponding colors (`mesh` and `color`) to an existing `GLScene` object (`scene`).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Scene.jl#LL65-L69' class='documenter-source'>source</a><br>


<a id='Rendering-methods'></a>

<a id='Rendering-methods-1'></a>

## Rendering methods

<a id='VPL.Render.GLTurtle' href='#VPL.Render.GLTurtle'>#</a>
**`VPL.Render.GLTurtle`** &mdash; *Type*.



```julia
GLTurtle()
```

Create a `GLTurtle()` object that will parse a `Graph` object and store the colors associated to the different primitives. This type of turtle is automatically created by calls to `GLScene()` and `render()` but the user may want to separately construct the geometry and colors and manually combined them into a `GLScene` object for performance reasons.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL2-L9' class='documenter-source'>source</a><br>

<a id='VPL.Render.colors-Tuple{VPL.Render.GLTurtle}' href='#VPL.Render.colors-Tuple{VPL.Render.GLTurtle}'>#</a>
**`VPL.Render.colors`** &mdash; *Method*.



```julia
colors(turtle)
```

Extract the array of colors stored inside an `GLTurtle` object


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL14-L18' class='documenter-source'>source</a><br>

<a id='VPL.Render.feedcolor!' href='#VPL.Render.feedcolor!'>#</a>
**`VPL.Render.feedcolor!`** &mdash; *Function*.



```julia
feedcolor!(turtle::GLTurtle, color::Colorant)
```

General purpose method to feed a color to a GL turtle. This should be used inside user's defined methods to add any color object that inherits from `Colorant` from the package *Color*, for example, by using `RGB()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL21-L27' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, node::Node)
```

Default method for `feedcolor!()` that does not do anything. Hence, the user can include nodes in a graph withour associated colors (the nodes should not generate geometry either).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL30-L35' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, g::Graph)
```

Process a `Graph` object with a GL turtle and collect the colors defined in the graph, in the same order in which the 3D mesh is created by the corresponding `feedgeom!()` method.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL38-L43' class='documenter-source'>source</a><br>


```
feedcolor!(turtle::GLTurtle, collection::AbstractArray)
feedcolor!(turtle::GLTurtle, collection::Tuple)
```

Feed a GL turtle an array or tuple of objects (`collection`) with existing `feedcolor!()` methods.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Turtle.jl#LL68-L73' class='documenter-source'>source</a><br>

<a id='VPL.Render.render' href='#VPL.Render.render'>#</a>
**`VPL.Render.render`** &mdash; *Function*.



```julia
render(m::Mesh, color; kwargs...)
```

Render a mesh with a given color. This will create a new visualization (see Documentation for details). Keyword arguments are passed to the `render(scene::GLScene)` method and any   unmatched keywords will be passed along to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL6-L12' class='documenter-source'>source</a><br>


```
render(scene::GLScene; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render a `GLScene` object. This will create a new visualization (see Documentation for details). `normals = true` will draw arrows in the direction of the normal vector for each triangle in the mesh, `wireframe = true` will draw the edges of each triangle with  black lines. Keyword arguments are passed to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL59-L66' class='documenter-source'>source</a><br>


```
render(graph::Graph; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render the 3D mesh associated to a `Graph` object. This will create a new visualization (see Documentation for details). `normals = true` will draw arrows in the direction of the normal vector for each triangle in the mesh, `wireframe = true` will draw the edges of each triangle with  black lines. Keyword arguments are passed to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL71-L78' class='documenter-source'>source</a><br>


```
render(graphs::Vector{<:Graph}; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render the 3D mesh associated to an array of `Graph` objects. This will create a new visualization (see Documentation for details). `normals = true` will draw arrows in the direction of the normal vector for each triangle in the mesh, `wireframe = true` will draw the edges of each triangle with  black lines. Keyword arguments are passed to `Makie.mesh()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL83-L90' class='documenter-source'>source</a><br>

<a id='VPL.Render.render!' href='#VPL.Render.render!'>#</a>
**`VPL.Render.render!`** &mdash; *Function*.



```julia
render!(m::Mesh, color; kwargs...)
```

Add a mesh with a given color the visualization currently active. This will create a new  visualization (see Documentation for details). Keyword arguments are passed to the  `render!(scene::GLScene)` method and any unmatched keywords will be passed along to `Makie.mesh!()`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL17-L23' class='documenter-source'>source</a><br>

<a id='VPL.Render.export_scene-Tuple{Any, Any}' href='#VPL.Render.export_scene-Tuple{Any, Any}'>#</a>
**`VPL.Render.export_scene`** &mdash; *Method*.



```julia
export_scene(scene, filename; kwargs...)
```

Export a screenshot of the current visualization (stored as `scene` as output of a call to `render`) as a PNG  file store in the path given by `filename` (including `.png` extension). Keyword arguments will be passed along to the corresponding `save` method from Makie (see VPL documentation for details).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Render/Render.jl#LL99-L105' class='documenter-source'>source</a><br>

