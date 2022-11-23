
<a id='Module-Core'></a>

<a id='Module-Core-1'></a>

# Module Core




<a id='Types'></a>

<a id='Types-1'></a>

## Types

<a id='VPL.Core.Graph' href='#VPL.Core.Graph'>#</a>
**`VPL.Core.Graph`** &mdash; *Type*.



```julia
Graph(;axiom, rules = nothing, vars = nothing)
```

Create a dynamic graph from an axiom, one or more rules and, optionally,  graph-level variables.

**Arguments**

  * `axiom`: A single object inheriting from `Node` or a subgraph generated  with

the graph construction DSL. It should represent the initial state of the dynamic graph. 

  * `rules`:  A single `Rule` object or a tuple of `Rule` objects (optional). It

should include all graph-rewriting rules of the graph. 

  * `vars`: A single object of any user-defined type (optional). This will be the

graph-level variable accessible from any rule or query applied to the graph.

  * `FT`: Floating-point precision to be used when generating the 3D geometry

associated to a graph. 

**Details**

All arguments are assigned by keyword. The axiom and rules are deep-copied when  creating the graph but the graph-level variables (if a copy is needed due to mutability, the user needs to care of that).

**Return**

An object of type `Graph` representing a dynamic graph. Printing this object results in a human-readable description of the type of data stored in the graph.

**Examples**

```julia
let
    struct A0 <: Node end
    struct B0 <: Node end
    axiom = A0() + B0()
    no_rules_graph = Graph(axiom = axiom)
    rule = Rule(A, rhs = x -> A0() + B0())
    rules_graph = Graph(axiom = axiom, rules = rule)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Graph.jl#LL7-L44' class='documenter-source'>source</a><br>

<a id='VPL.Core.Rule' href='#VPL.Core.Rule'>#</a>
**`VPL.Core.Rule`** &mdash; *Type*.



```julia
Rule(nodetype; lhs = x -> true, rhs = x -> nothing, captures = false)
```

Create a replacement rule for nodes of type `nodetype`.

**Arguments**

  * `nodetype`: Type of node to be matched.
  * `lhs`: Function or function-like object that takes a `Context` object and

returns whether the node should be replaced or not (with `true` or `false`).

  * `rhs`: Function or function-like object that takes one or more `Context`

objects and returns a replacement graph or `nothing`. If it takes several  inputs, the first one will correspond to the node being replaced.  

  * `captures`: Either `false` or `true` to indicate whether the left-hand side

of the rule is capturing nodes in the context of the replacement node to be used for the construction of the replace graph.

**Details**

See VPL documentation for details on rule-based graph rewriting.

**Return**

An object of type `Rule`.

**Examples**

```julia
let
    struct A <: Node end
    struct B <: Node end
    axiom = A() + B()
    rule = Rule(A, rhs = x -> A() + B())
    rules_graph = Graph(axiom = axiom, rules = rule)
    rewrite!(rules_graph)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Rule.jl#LL7-L40' class='documenter-source'>source</a><br>

<a id='VPL.Core.Query' href='#VPL.Core.Query'>#</a>
**`VPL.Core.Query`** &mdash; *Type*.



```julia
Query(nodetype::DataType; condition = x -> true)
```

Create a query that matches nodes of type `nodetype` and a `condition`.

**Arguments**

  * `nodetype::DataType`: Type of node to be matched.
  * `condition`: Function or function-like object that checks if a node should be

selected. It is assigned as a keyword argument.

**Details**

If the `nodetype` should refer to a concrete type and match one of the types stored inside the graph. Abstract types or types that are not contained in the graph are allowed but the query will never return anything.

The `condition` must be a function or function-like object that takes a  `Context` as input and returns `true` or `false`. The default `condition` always return `true` such that the query will

**Return**

It returns an object of type `Query`. Use `apply()` to execute the query on a  dynamic graph.

**Example**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
graph = Graph(axiom)
query = Query(A)
apply(graph, query)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Query.jl#LL7-L39' class='documenter-source'>source</a><br>

<a id='VPL.Core.Node' href='#VPL.Core.Node'>#</a>
**`VPL.Core.Node`** &mdash; *Type*.



```julia
Node
```

Abstract type from which every node in a graph should inherit. This allows using the graph construction DSL.

**Example**

```julia
let
  struct bar <: Node
    x::Int
  end
  b1 = bar(1)
  b2 = bar(2)
  b1 + b2
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Types.jl#LL3-L20' class='documenter-source'>source</a><br>

<a id='VPL.Core.Context' href='#VPL.Core.Context'>#</a>
**`VPL.Core.Context`** &mdash; *Type*.



```julia
Context
```

Data structure than links a node to the rest of the graph.

**Fields**

  * `graph`: Dynamic graph that contains the node.
  * `node`: Node inside the graph.

**Details**

A `Context` object wraps references to a node and its associated graph. The purpose of this structure is to be able to test relationships among nodes within a graph (from with a query or rule), as well as access the data stored in a node (with `data()`) or the graph (with `vars()`).

Users do not build `Context` objects directly but they are provided by VPL as  inputs to the user-defined functions inside rules and queries. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Types.jl#LL41-L58' class='documenter-source'>source</a><br>


<a id='Graph-DSL'></a>

<a id='Graph-DSL-1'></a>

## Graph DSL

<a id='Base.:+-Tuple{VPL.Core.Node, VPL.Core.Node}' href='#Base.:+-Tuple{VPL.Core.Node, VPL.Core.Node}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(n1::Node, n2::Node)
```

Creates a graph with two nodes where `n1` is the root and `n2` is the insertion point.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + B1(1)
    draw(axiom)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/GraphConstruction.jl#LL52-L66' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.Node}' href='#Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.Node}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g::StaticGraph, n::Node)
```

Creates a graph as the result of appending the node `n` to the insertion point of graph `g`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + B1(1)
    axiom = axiom + A1(2)
    draw(axiom)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/GraphConstruction.jl#LL76-L91' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.Node, VPL.Core.StaticGraph}' href='#Base.:+-Tuple{VPL.Core.Node, VPL.Core.StaticGraph}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(n::Node, g::StaticGraph)
```

Creates a graph as the result of appending the static graph `g` to the node `n`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + B1(1)
    axiom = A1(2) + axiom
    draw(axiom)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/GraphConstruction.jl#LL94-L109' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.StaticGraph}' href='#Base.:+-Tuple{VPL.Core.StaticGraph, VPL.Core.StaticGraph}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g1::StaticGraph, g2::StaticGraph)
```

Creates a graph as the result of appending `g2` to the insertion point of `g1`.  The insertion point of the final graph corresponds to the insertion point of `g2`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom1 = A1(1) + B1(1)
    axiom2 = A1(2) + B1(2)
    axiom = axiom1 + axiom2
    draw(axiom)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/GraphConstruction.jl#LL113-L130' class='documenter-source'>source</a><br>

<a id='Base.:+-Tuple{VPL.Core.Node, Tuple}' href='#Base.:+-Tuple{VPL.Core.Node, Tuple}'>#</a>
**`Base.:+`** &mdash; *Method*.



```julia
+(g::StaticGraph, T::Tuple)
+(n::Node, T::Tuple)
```

Creates a graph as the result of appending a tuple of graphs/nodes `T` to the insertion point of the graph `g` or node `n`. Each graph/node in `L` becomes a  branch.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + (B1(1) + A1(3), B1(4))
    draw(axiom)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/GraphConstruction.jl#LL149-L166' class='documenter-source'>source</a><br>


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


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Query.jl#LL61-L76' class='documenter-source'>source</a><br>

<a id='VPL.Core.rewrite!-Tuple{VPL.Core.Graph}' href='#VPL.Core.rewrite!-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.rewrite!`** &mdash; *Method*.



```julia
rewrite!(g::Graph)
```

Apply the graph-rewriting rules stored in the graph.

**Arguments**

  * `g::Graph`: The graph to be rewritten. It will be modified in-place.

**Details**

This function will match the left-hand sides of all the rules in a graph. If any node is matched by more than one rule this will result in an error. The rules are then applied in order to replaced the matched nodes with the result of executing the right hand side of the rules. The rules are applied in the order in which they are stored in the graph but the order in which the nodes are  processed is not defined. Since graph rewriting is semantically a parallel process, the rules should not be rely on any particular order for their  functioning.

**Returns**

This function returns `nothing`, but the graph passed as input will be modified by the execution of the rules.

**Example**

```julia
let
    struct A <: Node end
    struct B <: Node end
    axiom = A() + B()
    rule = Rule(A, rhs = x -> A() + B())
    g = Graph(axiom = axiom, rules = rule)
    rewrite!(g)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Rule.jl#LL158-L191' class='documenter-source'>source</a><br>


<a id='Extracting-information'></a>

<a id='Extracting-information-1'></a>

## Extracting information

<a id='VPL.Core.vars-Tuple{VPL.Core.Graph}' href='#VPL.Core.vars-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.vars`** &mdash; *Method*.



vars(g::Graph)

Returns the graph-level variables.

**Example**

```julia
struct A <: Node end
axiom = A()
graph = Graph(axiom, vars = 2)
vars(graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Graph.jl#LL76-L88' class='documenter-source'>source</a><br>

<a id='VPL.Core.rules-Tuple{VPL.Core.Graph}' href='#VPL.Core.rules-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.rules`** &mdash; *Method*.



```julia
rules(g::Graph)
```

Returns a tuple with all the graph-rewriting rules stored in a dynamic graph

**Examples**

```julia
struct A <: Node end
struct B <: Node end
axiom = A() + B()
rule = Rule(A, rhs = x -> A() + B())
rules_graph = Graph(axiom, rules = rule)
rules(rules_graph)
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Graph.jl#LL59-L73' class='documenter-source'>source</a><br>

<a id='VPL.Core.vars-Tuple{VPL.Core.Context}' href='#VPL.Core.vars-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.vars`** &mdash; *Method*.



```julia
vars(c::Context)
```

Returns the graph-level variables. Intended to be used within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL22-L26' class='documenter-source'>source</a><br>

<a id='VPL.Core.data-Tuple{VPL.Core.Context}' href='#VPL.Core.data-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.data`** &mdash; *Method*.



```julia
data(c::Context)
```

Returns the data stored in a node. Intended to be used within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL11-L15' class='documenter-source'>source</a><br>


<a id='Node-relations'></a>

<a id='Node-relations-1'></a>

## Node relations

<a id='VPL.Core.hasParent-Tuple{VPL.Core.Context}' href='#VPL.Core.hasParent-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasParent`** &mdash; *Method*.



```julia
hasParent(c::Context)
```

Check if a node has a parent and return `true` or `false`. Intended to be used  within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL36-L41' class='documenter-source'>source</a><br>

<a id='VPL.Core.isRoot-Tuple{VPL.Core.Context}' href='#VPL.Core.isRoot-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.isRoot`** &mdash; *Method*.



```julia
isRoot(c::Context)
```

Check if a node is the root of the graph (i.e., has no parent) and return `true` or  `false`. Intended to be used within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL44-L49' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasAncestor-Tuple{VPL.Core.Context}' href='#VPL.Core.hasAncestor-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasAncestor`** &mdash; *Method*.



```julia
hasAncestor(c::Context; condition = x -> true, maxlevel::Int = typemax(Int))
```

Check if a node has an ancestor that matches the condition. Intended to be used within  a rule or query. 

**Arguments**

  * `c::Context`: Context associated to a node in a dynamic graph.
  * `condition`: An user-defined function that takes a `Context` object as input

and returns `true` or `false`. It is assigned by the user by keyword.

  * `maxlevel::Int`: Maximum number of steps that the algorithm may take when

traversing the graph.

**Details**

This function traverses the graph from the node associated to `c` towards the  root of the graph until a node is found for which `condition` returns `true`. If no node meets the condition, then it will return `false`. The defaults values  for this function are such that the algorithm always returns `true`  after one step (unless it is applied to the root node) in which case it is  equivalent to calling `hasParent` on the node.

The number of levels that the algorithm is allowed to traverse is capped by `maxlevel` (mostly to avoid excessive computation, though the user may want to specify a meaningful limit based on the topology of the graphs being used).

The function `condition` should take an object of type `Context` as input and return `true` or `false`.

**Return**

Return a tuple with two values a `Bool` and an `Int`, the boolean indicating  whether the node has an ancestor meeting the condition, the integer indicating  the number of levels in the graph separating the node an its ancestor.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    function qfun(n)
        hasAncestor(n, condition = x -> data(x).val == 1)[1]
    end
    Q1 = Query(A1, query = qfun)
    R1 = apply(g, Q1)
    Q2 = Query(B1, query = qfun)
    R2 = apply(g, Q2)
    (R1,R2)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL52-L102' class='documenter-source'>source</a><br>

<a id='Base.parent-Tuple{VPL.Core.Context}' href='#Base.parent-Tuple{VPL.Core.Context}'>#</a>
**`Base.parent`** &mdash; *Method*.



```julia
parent(c::Context; nsteps::Int)
```

Returns the parent of a node that is `nsteps` away towards the root of the graph. Intended to be used within a rule or query. 

**Details**

If `hasParent()` returns `false` for the same node or the algorithm has reached the root node but `nsteps` have not been reached, then `parent()` will return  `missing`, otherwise it returns the `Context` associated to the matching node.

**Return**

Return a `Context` object or `missing`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    function qfun(n)
        np = parent(n, nsteps = 2)
        !ismissing(np) && data(np).val == 2
    end
    Q1 = Query(A1, query = qfun)
    R1 = apply(g, Q1)
    Q2 = Query(B1, query = qfun)
    R2 = apply(g, Q2)
    (R1,R2)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL183-L215' class='documenter-source'>source</a><br>

<a id='VPL.Core.ancestor-Tuple{VPL.Core.Context}' href='#VPL.Core.ancestor-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.ancestor`** &mdash; *Method*.



```julia
ancestor(c::Context; condition = x -> true, maxlevel::Int = typemax(Int))
```

Returns the first ancestor of a node that matches the `condition`. Intended to be  used within a rule or query. 

**Details**

If `hasAncestor()` returns `false` for the same node and `condition`, `ancestor()` will return `missing`, otherwise it returns the `Context` associated to the  matching node

**Return**

Return a `Context` object or `missing`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    function qfun(n)
        na = ancestor(n, condition = x -> (data(x).val == 1))
        if !ismissing(na)
            data(na) isa B1
        else
            false
        end
    end
    Q1 = Query(A1, query = qfun)
    R1 = apply(g, Q1)
    Q2 = Query(B1, query = qfun)
    R2 = apply(g, Q2)
    (R1,R2)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL220-L256' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasChildren-Tuple{VPL.Core.Context}' href='#VPL.Core.hasChildren-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasChildren`** &mdash; *Method*.



```julia
hasChildren(c::Context)
```

Check if a node has at least one child and return `true` or `false`. Intended to be used within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL108-L113' class='documenter-source'>source</a><br>

<a id='VPL.Core.isLeaf-Tuple{VPL.Core.Context}' href='#VPL.Core.isLeaf-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.isLeaf`** &mdash; *Method*.



```julia
isLeaf(c::Context)
```

Check if a node is a leaf in the graph (i.e., has no children) and return `true` or  `false`. Intended to be used within a rule or query. 


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL116-L121' class='documenter-source'>source</a><br>

<a id='VPL.Core.hasDescendent-Tuple{VPL.Core.Context}' href='#VPL.Core.hasDescendent-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.hasDescendent`** &mdash; *Method*.



```julia
hasDescendent(c::Context; condition = x -> true, maxlevel::Int = typemax(Int))
```

Check if a node has a descendent that matches the optional condition. Intended to be used  within a rule or query. 

**Arguments**

  * `c::Context`: Context associated to a node in a dynamic graph.
  * `condition`: An user-defined function that takes a `Context` object as input

and returns `true` or `false`. It is assigned by the user by keyword.

  * `maxlevel::Int`: Maximum number of steps that the algorithm may take when

traversing the graph.

**Details**

This function traverses the graph from the node associated to `c` towards the  leaves of the graph until a node is found for which `condition` returns `true`.  If no node meets the condition, then it will return `false`. The defaults values  for this function are such that the algorithm always returns `true`  after one step (unless it is applied to a leaf node) in which case it is  equivalent to calling `hasChildren` on the node.

The number of levels that the algorithm is allowed to traverse is capped by `maxlevel` (mostly to avoid excessive computation, though the user may want to specify a meaningful limit based on the topology of the graphs being used).

The function `condition` should take an object of type `Context` as input and return `true` or `false`.

**Return**

Return a tuple with two values a `Bool` and an `Int`, the boolean indicating  whether the node has an ancestor meeting the condition, the integer indicating  the number of levels in the graph separating the node an its ancestor.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    function qfun(n)
        hasDescendent(n, condition = x -> data(x).val == 1)[1]
    end
    Q1 = Query(A1, query = qfun)
    R1 = apply(g, Q1)
    Q2 = Query(B1, query = qfun)
    R2 = apply(g, Q2)
    (R1,R2)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL124-L174' class='documenter-source'>source</a><br>

<a id='VPL.Core.children-Tuple{VPL.Core.Context}' href='#VPL.Core.children-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.children`** &mdash; *Method*.



```julia
children(c::Context)
```

Returns all the children of a node as `Context` objects.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL262-L266' class='documenter-source'>source</a><br>

<a id='VPL.Core.descendent-Tuple{VPL.Core.Context}' href='#VPL.Core.descendent-Tuple{VPL.Core.Context}'>#</a>
**`VPL.Core.descendent`** &mdash; *Method*.



```julia
descendent(c::Context; condition = x -> true, maxlevel::Int = typemax(Int))
```

Returns the first descendent of a node that matches the `condition`. Intended to  be used within a rule or query. 

**Details**

If `hasDescendent()` returns `false` for the same node and `condition`,  `descendent()` will return `missing`, otherwise it returns the `Context`  associated to the matching node.

**Return**

Return a `Context` object or `missing`.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    function qfun(n)
        na = descendent(n, condition = x -> (data(x).val == 1))
        if !ismissing(na)
            data(na) isa B1
        else
            false
        end
    end
    Q1 = Query(A1, query = qfun)
    R1 = apply(g, Q1)
    Q2 = Query(B1, query = qfun)
    R2 = apply(g, Q2)
    (R1,R2)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Context.jl#LL271-L308' class='documenter-source'>source</a><br>


<a id='Traversal-algorithms'></a>

<a id='Traversal-algorithms-1'></a>

# Traversal algorithms

<a id='VPL.Core.traverse-Tuple{VPL.Core.Graph}' href='#VPL.Core.traverse-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.traverse`** &mdash; *Method*.



```julia
traverse(g::Graph; fun = () -> nothing)
```

Iterates over all the nodes in the graph and execute for the function `fun` on each node

**Arguments**

  * `g::Graph`: The graph object that will be traversed.
  * `fun`: A function or function-like object defined by the user that will be

applied to each node. This argument is assigned by keyword.

**Details**

This traveral happens in the order in which the nodes are stored in the graph. This order is arbitrary and may vary across executions of the code (it does not correspond to the order in which nodes are created). For algorithms that require a particular traveral order of the graph, see `traverseDFS` and `traverseBFS`.

This function does not store any results generated by `fun`. Hence, if the user wants to keep track of such results, they should be stored indirectly (e.g., via a global variable or internally by creating a functor).

The function or function-like object provided by the user should take only one argument that corresponds to applying `data()` to each node in the graph. Several methods of such function may be defined for different types of nodes in the graph. Since the function will use the data stored in the nodes, relations among nodes may not be used as input. For algorithms where relations among nodes are important, the user should be using queries instead (see `Query` and general VPL documentation).

**Return**

This function returns nothing but `fun` may have side-effects.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    struct Foo
        vals::Vector{Int}
    end
    function (f::Foo)(x)
        push!(f.vals, x.val)
    end
    f = Foo(Int[])
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    traverse(g, fun = f)
    f.vals
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Algorithms.jl#LL7-L57' class='documenter-source'>source</a><br>

<a id='VPL.Core.traverseDFS-Tuple{VPL.Core.Graph}' href='#VPL.Core.traverseDFS-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.traverseDFS`** &mdash; *Method*.



```julia
traverseDFS(g::Graph; fun = () -> nothing, ID = root(g))
```

Iterates over all the nodes in the graph (depth-first order, starting at a any node) and execute for the function `fun` on each node

**Arguments**

  * `g::Graph`: The graph object that will be traversed.
  * `fun`: A function or function-like object defined by the user that will be

applied to each node. This argument is assigned by keyword.

  * `ID`: The ID of the node where the traveral should start. This argument is

assigned by keyword and is, by default, the root of the graph.

**Details**

This traveral happens in a depth-first order. That is, all nodes in a branch of the graph are visited until reach a leaf node, then moving to the next branch. Hence, this algorithm should always generate the same result when applied to the same graph (assuming the user-defined function is not stochastic). For a version of this function that us breadth-first order see `traverseBFS`.

This function does not store any results generated by `fun`. Hence, if the user wants to keep track of such results, they should be stored indirectly (e.g., via a global variable or internally by creating a functor).

The function or function-like object provided by the user should take only one argument that corresponds to applying `data()` to each node in the graph. Several methods of such function may be defined for different types of nodes in the graph. Since the function will use the data stored in the nodes, relations among nodes may not be used as input. For algorithms where relations among nodes are important, the user should be using queries instead (see `Query` and general VPL documentation).

**Return**

This function returns nothing but `fun` may have side-effects.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    struct Foo
        vals::Vector{Int}
    end
    function (f::Foo)(x)
        push!(f.vals, x.val)
    end
    f = Foo(Int[])
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    traverseDFS(g, fun = f)
    f.vals
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Algorithms.jl#LL66-L119' class='documenter-source'>source</a><br>

<a id='VPL.Core.traverseBFS-Tuple{VPL.Core.Graph}' href='#VPL.Core.traverseBFS-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.traverseBFS`** &mdash; *Method*.



```julia
traverseBFS(g::Graph; fun = () -> nothing, ID = root(g))
```

Iterates over all the nodes in the graph (breadth-first order, starting at a any node) and execute for the function `fun` on each node

**Arguments**

  * `g::Graph`: The graph object that will be traversed.
  * `fun`: A function or function-like object defined by the user that will be

applied to each node. This argument is assigned by keyword.

  * `ID`: The ID of the node where the traveral should start. This argument is

assigned by keyword and is, by default, the root of the graph.

**Details**

This traveral happens in a breadth-first order. That is, all nodes at a given depth of the the graph are visited first, then moving on to the next level. Hence, this algorithm should always generate the same result when applied to the same graph (assuming the user-defined function is not stochastic). For a version of this function that us depth-first order see `traverseDFS`.

This function does not store any results generated by `fun`. Hence, if the user wants to keep track of such results, they should be stored indirectly (e.g., via a global variable or internally by creating a functor).

The function or function-like object provided by the user should take only one argument that corresponds to applying `data()` to each node in the graph. Several methods of such function may be defined for different types of nodes in the graph. Since the function will use the data stored in the nodes, relations among nodes may not be used as input. For algorithms where relations among nodes are important, the user should be using queries instead (see `Query` and general VPL documentation).

**Return**

This function returns nothing but `fun` may have side-effects.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    struct Foo
        vals::Vector{Int}
    end
    function (f::Foo)(x)
        push!(f.vals, x.val)
    end
    f = Foo(Int[])
    axiom = A1(2) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    traverseBFS(g, fun = f)
    f.vals
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Algorithms.jl#LL140-L193' class='documenter-source'>source</a><br>


<a id='Graph-visualization'></a>

<a id='Graph-visualization-1'></a>

## Graph visualization

<a id='VPL.Core.draw-Tuple{VPL.Core.Graph}' href='#VPL.Core.draw-Tuple{VPL.Core.Graph}'>#</a>
**`VPL.Core.draw`** &mdash; *Method*.



```julia
draw(g::Graph; force = false, backend = "native", inline = false, 
     resolution = (1920, 1080), nlabels_textsize = 15, arrow_size = 15, 
     node_size = 5)
```

Visualize a graph as network diagram.

**Arguments**

All arguments are assigned by keywords except the graph `g`.  

  * `g::Graph`: The graph to be visualized.
  * `force = false`: Force the creation of a new window to store the network

diagram.  

  * `backend = "native"`: The graphics backend to render the network diagram. It

can have the values `"native"`, `"web"` and `"vector"`. See VPL documentation for details.  

  * `inline = false`: Currently this argument does not do anything (will change in

future versions of VPL).  

  * `resolution = (1920, 1080)`: The resolution of the image to be rendered, in

pixels (online relevant for native and web backends). Default resolution is HD. 

  * `nlabels_textsize = 15`: Customize the size of the labels in the diagram.
  * `arrow_size = 15`: Customize the size of the arrows representing edges in the

diagram.  

  * `node_size = 5`: Customize the size of the nodes in the diagram.

**Details**

By default, nodes are labelled with the type of data stored and their unique ID. See function `node_label()` to customize the label for different types of data.

See `export_graph()` to export the network diagram as a raster or vector image (depending on the backend). The function `calculate_resolution()` can be useful to ensure a particular dpi of the exported image (assuming some physical size).

The graphics backend will interact with the environment where the Julia code is being executed (i.e., terminal, IDE such as VS Code, interactive notebook such as Jupyter or Pluto). These interactions are all controlled by the graphics  package Makie that VPL relies on. Some details on the expected behavior specific to `draw()` can be found in the general VPL documentation as www.virtualplantlab.com

**Return**

This function returns a Makie `Figure` object, while producing the visualization as a side effect.

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    draw(g)
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Draw.jl#LL115-L169' class='documenter-source'>source</a><br>

<a id='VPL.Core.draw-Tuple{VPL.Core.StaticGraph}' href='#VPL.Core.draw-Tuple{VPL.Core.StaticGraph}'>#</a>
**`VPL.Core.draw`** &mdash; *Method*.



```julia
draw(g::StaticGraph; force = false, backend = "native", inline = false, 
     resolution = (1920, 1080), nlabels_textsize = 15, arrow_size = 15, 
     node_size = 5)
```

Equivalent to the method `draw(g::Graph; kwargs...)` but  to visualize static  graphs (e.g., the axiom of a graph).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Draw.jl#LL67-L74' class='documenter-source'>source</a><br>

<a id='VPL.Core.node_label-Tuple{VPL.Core.Node, Any}' href='#VPL.Core.node_label-Tuple{VPL.Core.Node, Any}'>#</a>
**`VPL.Core.node_label`** &mdash; *Method*.



```julia
node_label(n::Node, id)
```

Function to construct a label for a node to be used by `draw()` when visualizing. The user can specialize this method for user-defined data types to customize the  labels. By default, the type of data stored in the node and the unique ID of the node are used as labels.


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Draw.jl#LL3-L10' class='documenter-source'>source</a><br>

<a id='VPL.Core.export_graph-Tuple{Any}' href='#VPL.Core.export_graph-Tuple{Any}'>#</a>
**`VPL.Core.export_graph`** &mdash; *Method*.



```julia
export_graph(f; filename, kwargs...)
```

Save a network diagram generated by `draw()` to an external file.

**Arguments**

  * `f`: Object of type `Figure` return by `draw()`.
  * `filename`: Name of the file where the diagram will be stored. The extension

will be used to determined the format of the image (see example below).

**Details**

Internally, `export_graph()` calls the `save()` method from the ImageIO package and its dependencies. Any keyword argument supported by the relevant save method  will be passed along by `export_graph()`. For example, exporting diagrams as PNG  allows defining the compression level as `compression_level` (see PNGFiles  package for details).

**Return**

The function returns nothing but, if successful, it will generate a new file containing the network diagram in the appropiate format.

**Examples**

**Examples**

```julia
let
    struct A1 <: Node val::Int end
    struct B1 <: Node val::Int end
    axiom = A1(1) + (B1(1) + A1(3), B1(4))
    g = Graph(axiom = axiom)
    f = draw(g);
    export_graph(f, filename = "test.png")
end
```


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Draw.jl#LL176-L209' class='documenter-source'>source</a><br>

<a id='VPL.Core.calculate_resolution-Tuple{}' href='#VPL.Core.calculate_resolution-Tuple{}'>#</a>
**`VPL.Core.calculate_resolution`** &mdash; *Method*.



```julia
calculate_resolution(;width = 1024/300*2.54, height = 768/300*2.54, 
                      format = "raster", dpi = 300)
```

Calculate the resolution required to achieve a specific `width` and `height`  (in cm) of the exported image, with a particular `dpi` (for raster formats).


<a target='_blank' href='https://github.com/AleMorales/VPL.jl/blob/e4e3aa68ed1f0a6fa3a421ecbb7e759fb85eaebd/src/Core/Draw.jl#LL214-L220' class='documenter-source'>source</a><br>

