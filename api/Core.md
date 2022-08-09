
<a id='Module-Core'></a>

<a id='Module-Core-1'></a>

# Module Core




<a id='Types'></a>

<a id='Types-1'></a>

## Types

<a id='VPL.Core.Graph' href='#VPL.Core.Graph'>#</a>
**`VPL.Core.Graph`** &mdash; *Type*.



```julia
Graph(axiom; rules = nothing, vars = nothing)
```

Creates a dynamic graph defined by the initial node or nodes (`axiom`), one or more rules  (`rules`), and an object with graph-level variables (`vars`). Rules and graph-level variables are optional and must be assigned by keyword (see example below).  Rules must be a `Rule` or tuple of `Rule` objects.  The `axiom` may be a single object inheriting from `Node` or a subgraph generated  with the graph construction DSL.  A copy of the axiom and rules is always made when constructing the graph, but if object containing graph-level variables is not `mutable`, the user must manually copy it (with `copy` or `deepcopy`) or else changes within the graph will affect the original object (and other graphs created from the same object).

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
no_rules_graph = Graph(axiom)
rule = Rule(A, rhs = x -> A() + B())
rules_graph = Graph(axiom, rules = rule)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Graph.jl#LL7-L30' class='documenter-source'>source</a><br>

<a id='VPL.Core.Rule' href='#VPL.Core.Rule'>#</a>
**`VPL.Core.Rule`** &mdash; *Type*.



```julia
Rule(nodetype; lhs = x -> true, rhs = x -> nothing, captures = false)
```

Create a replacement rule for nodes of type `nodetype` with function-like objects for the left-hand side (`lhs`) and right-hand side (`rhs`). If the rule captures nodes in the context of the replacement node this must be indicated by the argument `captures`.

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
rule = Rule(A, rhs = x -> A() + B())
rules_graph = Graph(axiom, rules = rule)
rewrite!(rules_graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Rule.jl#LL7-L24' class='documenter-source'>source</a><br>

<a id='VPL.Core.Query' href='#VPL.Core.Query'>#</a>
**`VPL.Core.Query`** &mdash; *Type*.



```julia
Query(nodetype::DataType, query = x -> true)
```

Create a query that matches nodes of type `nodetype` and the conditions specified in the argument `query` (must be a function that returns `true`). It returns an object of type `Query` that can be applied to a graph with the function `apply`.

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
graph = Graph(axiom)
query = Query(A)
apply(graph, query)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Query.jl#LL7-L23' class='documenter-source'>source</a><br>

<a id='VPL.Core.Node' href='#VPL.Core.Node'>#</a>
**`VPL.Core.Node`** &mdash; *Type*.



```julia
Node
```

Abstract type from which every node in a graph should inherit. This allows using the graph construction DSL.

**Example**

```julia
struct bar <: Node
  x::Int
end
b1 = bar(1)
b2 = bar(2)
b1 + b2
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Types.jl#LL2-L17' class='documenter-source'>source</a><br>

<a id='VPL.Core.Context' href='#VPL.Core.Context'>#</a>
**`VPL.Core.Context`** &mdash; *Type*.



```julia
Context
```

Data structure than links a `GraphNode` to a `Graph`. Functions `data()` and `vars()`  give access to the data stored in the node and graph, respectively. Several  methods are also available to test relationships among nodes in the graph and to  extract these related nodes (see User Manual for details).

Users do not build `Context` objects directly but they are provided by VPL as  inputs to the user-defined functions inside rules and queries. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Types.jl#LL38-L48' class='documenter-source'>source</a><br>


<a id='Graph-DSL'></a>

<a id='Graph-DSL-1'></a>

## Graph DSL

<a id='Base.:+-Tuple{VPL.Core.Node, VPL.Core.Node}' href='#Base.:+-Tuple{VPL.Core.Node, VPL.Core.Node}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(n1::Node, n2::Node)
```

Creates a graph with two nodes where `n1` is the root and `n2` is the insertion point.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/GraphConstruction.jl#LL52-L55' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.Node}' href='#Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.Node}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g::StaticGraph, n::Node)
```

Creates a graph as the result of appending the node `n` to the insertion point of graph `g`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/GraphConstruction.jl#LL65-L68' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.Node, VPL.Core.StaticGraph}' href='#Base.:+-Tuple{VPL.Core.Node, VPL.Core.StaticGraph}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(n::Node, g::StaticGraph)
```

Creates a graph as the result of appending the static graph `g` to the node `n`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/GraphConstruction.jl#LL71-L74' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.StaticGraph}' href='#Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.StaticGraph}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g1::StaticGraph, g2::StaticGraph)
```

Creates a graph as the result of appending `g2` to the insertion point of `g1`. The insertion point of the final graph corresponds to the insertion point of `g2`


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/GraphConstruction.jl#LL78-L82' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.Node, Tuple}' href='#Base.:+-Tuple{VPL.Core.Node, Tuple}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g::StaticGraph, T::Tuple)
+(n::Node, T::Tuple)
```

Creates a graph as the result of appending a tuple of graphs/nodes `T` to the insertion point of the graph `g` or node `n`. Each graph/node in `L` becomes a branch.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/GraphConstruction.jl#LL100-L105' class='documenter-source'>source</a><br>


<a id='Applying-rules-and-queries'></a>

<a id='Applying-rules-and-queries-1'></a>

## Applying rules and queries

<a id='VPL.Core.apply-Tuple{VPL.Core.Graph, VPL.Core.Query}' href='#VPL.Core.apply-Tuple{VPL.Core.Graph, VPL.Core.Query}'>#</a>
**`VPL.Core.apply`** &mdash; *Method*.



```julia
apply(g::Graph, query::Query)
```

Return an array with all the nodes in the graph that match the query supplied by  the user.

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
graph = Graph(axiom)
query = Query(A)
apply(graph, query)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Query.jl#LL45-L60' class='documenter-source'>source</a><br>

<a id='VPL.Core.rewrite!-Tuple{VPL.Core.Graph}' href='#VPL.Core.rewrite!-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.rewrite!`** &mdash; *Method*.



```julia
rewrite!(g::Graph)
```

Apply the graph-rewriting rules stored in the graph. This function will match the left-hand sides of the rules against the graph and then replace and/or prune the graph at every location where the left-hand sides matched by the result of executing the right hand side of each rule. The modification is performed in-place, so this function returns `nothing`.

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
rule = Rule(A, rhs = x -> A() + B())
rules_graph = Graph(axiom, rules = rule)
rewrite!(rules_graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Rule.jl#LL142-L160' class='documenter-source'>source</a><br>


<a id='Extracting-information'></a>

<a id='Extracting-information-1'></a>

## Extracting information

<a id='VPL.Core.vars-Tuple{VPL.Core.Graph}' href='#VPL.Core.vars-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.vars`** &mdash; *Method*.



vars(g::Graph)

Returns the object storing the graph-level variables

**Example**

```julia
struct A <: Node end
axiom = A()
graph = Graph(axiom, vars = 2)
vars(graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Graph.jl#LL62-L74' class='documenter-source'>source</a><br>

<a id='VPL.Core.rules-Tuple{VPL.Core.Graph}' href='#VPL.Core.rules-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.rules`** &mdash; *Method*.



```julia
rules(g::Graph)
```

Returns a tuple with all the graph-rewriting rules stored in the graph

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
rule = Rule(A, rhs = x -> A() + B())
rules_graph = Graph(axiom, rules = rule)
rules(rules_graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Graph.jl#LL45-L59' class='documenter-source'>source</a><br>

<a id='VPL.Core.vars-Tuple{VPL.Core.Context}' href='#VPL.Core.vars-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.vars`** &mdash; *Method*.



```julia
vars(c::Context)
```

Returns the object storing the graph-level variables in the graph associated to  a `Context` object. This needs to be used inside rules and queries.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL23-L28' class='documenter-source'>source</a><br>

<a id='VPL.Core.data-Tuple{VPL.Core.Context}' href='#VPL.Core.data-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.data`** &mdash; *Method*.



```julia
data(c::Context)
```

Returns the data stored in the node associated to a `Context` object. This needs to be used inside rules and queries.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL11-L16' class='documenter-source'>source</a><br>


<a id='Graph-traversal'></a>

<a id='Graph-traversal-1'></a>

## Graph traversal

<a id='VPL.Core.hasParent-Tuple{VPL.Core.Context}' href='#VPL.Core.hasParent-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasParent`** &mdash; *Method*.



```julia
hasParent(c::Context)
```

Check if the node passed as argument has a parent and return `true` or `false`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL38-L42' class='documenter-source'>source</a><br>

<a id='VPL.Core.isRoot-Tuple{VPL.Core.Context}' href='#VPL.Core.isRoot-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.isRoot`** &mdash; *Method*.



```julia
isRoot(c::Context)
```

Check if the node passed as argument is the root of the graph (i.e. has no parent)  and return `true` or `false`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL45-L50' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasAncestor' href='#VPL.Core.hasAncestor'>#</a>
**`VPL.Core.hasAncestor`** &mdash; *Function*.



```julia
hasAncestor(c::Context, condition, maxlevel)
```

Check if the node passed as argument has an ancestor that matches the optional  condition and and return `true` or `false` and the number of steps taken.  The `argument` maxlevel is optional and limits the number of steps that the  algorithm will move through the graph (by default there is no limitation). The default condition returns `true` for any ancestor  and it takes an object of type `Context`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL53-L62' class='documenter-source'>source</a><br>

<a id='Base.parent-Tuple{VPL.Core.Context}' href='#Base.parent-Tuple{VPL.Core.Context}'>#</a>
**`Base.parent`** &mdash; *Method*.



```julia
parent(c::Context, nsteps::Int)
```

Returns a `Context` object associated to the parent of the node passed as first argument (`nsteps = 1`, the default) or an ancestor that is `nsteps` away from the node passed as first argument.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL100-L106' class='documenter-source'>source</a><br>

<a id='VPL.Core.ancestor' href='#VPL.Core.ancestor'>#</a>
**`VPL.Core.ancestor`** &mdash; *Function*.



```julia
ancestor(c::Context, condition, maxlevel)
```

Returns a `Context` object associated to the first ancestor of the node given as  argument that matches the optional condition. The `argument` maxlevel is optional and limits the number of steps that the algorithm will move through the graph (by default there is no limitation). The matched node is returned as a `Context` object. The default condition returns `true` for any ancestor and it takes an object of type `Context`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL111-L120' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasChildren-Tuple{VPL.Core.Context}' href='#VPL.Core.hasChildren-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasChildren`** &mdash; *Method*.



```julia
hasChildren(c::Context)
```

Check if the node passed as argument has at least one child and return `true` or `false`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL68-L72' class='documenter-source'>source</a><br>

<a id='VPL.Core.isLeaf-Tuple{VPL.Core.Context}' href='#VPL.Core.isLeaf-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.isLeaf`** &mdash; *Method*.



```julia
isLeaf(c::Context)
```

Check if the node passed as argument is a leaf in the graph (i.e. has no children)  and return `true` or `false`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL75-L80' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasDescendent' href='#VPL.Core.hasDescendent'>#</a>
**`VPL.Core.hasDescendent`** &mdash; *Function*.



```julia
hasDescendent(c::Context, condition, maxlevel)
```

Check if the node passed as argument has a descendent that matches the optional condition  and return `true` or `false`. The argument `maxlevel` is optional and limits the number of steps that the algorithm will move through the graph (by default there is no limitation). The default condition returns `true` for any descendent  and it takes an object of type `Context`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL83-L91' class='documenter-source'>source</a><br>

<a id='VPL.Core.children-Tuple{VPL.Core.Context}' href='#VPL.Core.children-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.children`** &mdash; *Method*.



```julia
children(c::Context)
```

Returns a tuple of `Context` objects with all the children of the node given as  argument.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL126-L131' class='documenter-source'>source</a><br>

<a id='VPL.Core.descendent' href='#VPL.Core.descendent'>#</a>
**`VPL.Core.descendent`** &mdash; *Function*.



```julia
descendent(c::Context, condition, maxlevel)
```

Returns a `Context` object associated to the first descendent of the node given as  argument that matches the optional condition. The argument `maxlevel` is optional and limits the number of steps that the algorithm will move through the graph (by default there is no limitation). The matched node is returned as a `Context` object. The default condition returns `true` for any descendent and it takes an object of type `Context`.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Context.jl#LL136-L145' class='documenter-source'>source</a><br>

<a id='VPL.Core.traverse-Tuple{VPL.Core.Graph, Any}' href='#VPL.Core.traverse-Tuple{VPL.Core.Graph, Any}'>#</a>
**`VPL.Core.traverse`** &mdash; *Method*.



```julia
traverse(g::Graph, f)
```

Iterates over all the nodes in the graph (in no particular order) and execute for each node the function `f` taking as input the data stored in the node.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Algorithms.jl#LL5-L10' class='documenter-source'>source</a><br>

<a id='VPL.Core.traverseDFS-Tuple{VPL.Core.Graph, Any}' href='#VPL.Core.traverseDFS-Tuple{VPL.Core.Graph, Any}'>#</a>
**`VPL.Core.traverseDFS`** &mdash; *Method*.



```julia
traverseDFS(g::Graph, f)
```

Iterates over all the nodes in the graph (depth-first order, starting at the  root of the graph) and execute for each node the function `f` taking as input the  data stored in the node.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Algorithms.jl#LL18-L24' class='documenter-source'>source</a><br>

<a id='VPL.Core.traverseBFS-Tuple{VPL.Core.Graph, Any}' href='#VPL.Core.traverseBFS-Tuple{VPL.Core.Graph, Any}'>#</a>
**`VPL.Core.traverseBFS`** &mdash; *Method*.



```julia
traverseBFS(g::Graph, f)
```

Iterates over all the nodes in the graph (breadth-first order, starting at the  root of the graph) and execute for each node the function `f` taking as input the  data stored in the node.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Algorithms.jl#LL43-L49' class='documenter-source'>source</a><br>


<a id='Graph-visualization'></a>

<a id='Graph-visualization-1'></a>

## Graph visualization

<a id='VPL.Core.draw-Tuple{VPL.Core.Graph}' href='#VPL.Core.draw-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.draw`** &mdash; *Method*.



```julia
draw(g::Graph; force = false, backend = "native", inline = false, resolution = (1920, 1080),
```

nlabels*textsize = 15, arrow*size = 15, node_size = 5)

Visualize a graph as a network using different backends (`native` for OpenGL, `web` for WebGL and `vector` for Cairo vector graphics, see VPL documentation for details). To force an external window when using the native backend set `force = true` whereas to force to be inlined use `inline = true`. Details on the behaviour of each backend on different contexts of code execution can be found in the VPL documentation. For backend `native` or `web`, the user may specify the  resolution in pixels (by default HD is used). Additional customization is possible via `nlabels_textsize` (useful if the labels of the nodes are too large or small), `arrow_size` (this adjust the size of arrow heads) and `node_size` (for the size of the nodes).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Draw.jl#LL104-L115' class='documenter-source'>source</a><br>

<a id='VPL.Core.draw-Tuple{VPL.Core.StaticGraph}' href='#VPL.Core.draw-Tuple{VPL.Core.StaticGraph}'>#</a>
**`VPL.Core.draw`** &mdash; *Method*.



```julia
draw(g::StaticGraph; force = false, backend = "native", inline = false, resolution = (1920, 1080),
```

nlabels*textsize = 15, arrow*size = 15, node_size = 5)

Equivalent to the method `draw(g::Graph)` but useful to visualize static graphs (e.g., usually this would be  the axiom of a graph).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Draw.jl#LL57-L63' class='documenter-source'>source</a><br>

<a id='VPL.Core.node_label-Tuple{VPL.Core.Node, Any}' href='#VPL.Core.node_label-Tuple{VPL.Core.Node, Any}'>#</a>
**`VPL.Core.node_label`** &mdash; *Method*.



```julia
node_label(n::Node, id)
```

Function that constructs a label for a node to be used by `draw()` when visualizing the graph  as a network. The default method will create a label from the type of node its unique id. The user can specialize this method for user-defined data types to customize the label.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Draw.jl#LL2-L8' class='documenter-source'>source</a><br>

<a id='VPL.Core.export_graph-Tuple{Any, Any}' href='#VPL.Core.export_graph-Tuple{Any, Any}'>#</a>
**`VPL.Core.export_graph`** &mdash; *Method*.



```julia
export_graph(f, filename; kwargs...)
```

Export a graph visualization (created by `draw()`) into an external file. Supported formats are png (if the `native` or `web` backends were used in `draw()`), pdf or svg (if the `vector` backend was used). The file name should include the extension from which the format will be inferred. Additional keyword arguments are passed along to the corresponding `save()` method defined in the *Makie* package (see VPL documentation for details).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Draw.jl#LL122-L130' class='documenter-source'>source</a><br>

<a id='VPL.Core.calculate_resolution-Tuple{Any, Any}' href='#VPL.Core.calculate_resolution-Tuple{Any, Any}'>#</a>
**`VPL.Core.calculate_resolution`** &mdash; *Method*.



```julia
calculate_resolution(width, height; format = "png", dpi = 300)
```

Calculate the resolution required to achieve a specific `width` and `height` (in cm) of the exported image, with a particular `dpi` (for png format).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/ad86afd063ba4a15975584f1b4744fe3ef405caa/src/Core/Draw.jl#LL135-L140' class='documenter-source'>source</a><br>

