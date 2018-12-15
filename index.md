---
layout: default
permalink: /

#excerpt: "Be patient - the project is just bootstrapping..."
#title: "Devito: Fast Symbolic Finite Difference Computation"

---

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### **Devito**: Symbolic Finite Difference Computation
</div>

<div class="col-sm-6 pull-left" markdown="1">
Devito is a Domain-specific Language (DSL) and code
generation framework for the design of highly optimised finite
difference kernels for use in inversion methods. Devito utilises
[SymPy](http://www.sympy.org) to allow the definition of operators from
high-level symbolic equations and generates optimised and
automatically tuned code specific to a given target architecture.

Symbolic computation is a powerful tool that allows users to:

* Build complex solvers from only a few lines of high-level code
* Use automated performance optimisation for generated code
* Adjust stencil discretisation at runtime as required
* (Re-)development of solver code in hours rather than months

#### **Documentation**

Documentation for Devito is available
[here](https://www.opesci.org/devito/), including [installation
instructions](/devito/download.html), a set of
[tutorials](/devito/tutorials.html) and [API
documentation](/devito/devito.html).  In addition, a paper
outlining the use of symbolic Python to define finite difference operators in
Devito can be found [here](https://arxiv.org/abs/1609.03361).  Devito is a fast
moving project so some of the documentation may lag behind development. Feel
free to talk to us on slack if you have questions - PR's are also welcome.

</div>

<div class="col-sm-1 pull-left" markdown="1"></div>
<div class="col-sm-4 pull-left" markdown="1">
```
from devito import *

grid = Grid(shape=(nx, ny))
u = TimeFunction(name='u', grid=grid,
                 space_order=2)
u.data[0, :] = initial_data[:]

eqn = Eq(u.dt, a * (u.dx2 + u.dy2))
stencil = solve(eqn, u.forward)
op = Operator(Eq(u.forward, stencil))
op(t=timesteps, dt=dt)
```

Example code for a 2D diffusion operator from a symbolic
definition. The full tutorial can be found
[here](/devito/heat.html). In order to get more faimliar with Devito, it is highly recommended
that you run more [tutorials](https://www.devitoproject.org/devito/tutorials.html) .  
</div>
<div class="col-sm-1 pull-left" markdown="1"></div>
</div>  <!--End row-->

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### Seismic Inversion using Devito
</div>

<div class="col-sm-6 pull-left" markdown="1">
Devito is primarily designed to create wave propagation kernels for
use in seismic inversion problems. A tutorial for the generation of a
modelling operator using an acoustic wave equation can be found
[here](/devito/wave.html) and a paper
outlining the verification procedures of the acoustic operator can be
found [here](https://arxiv.org/abs/1608.08658).
<br/>

<img src="images/TrueFWI.png" alt="True velocity model (Marmousi-ii)" style="width:100%;"/>

<img src="images/InitFWI.png" alt="Initial velocity model for FWI" style="width:100%;"/>

<img src="images/FWI.png" alt="FWI inverted velocity model" style="width:100%;"/>
</div>

<div class="col-sm-6 pull-left" markdown="1">
<img src="images/Dual.png" alt="DualShot" style="width:90%;"/>
</div>
</div>  <!--End row-->

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### Optimisation and Performance
</div>

<div class="col-sm-6 pull-left" markdown="1">
Devito provides a set of automated performance optimizations during code generation that allow user applications to
fully utilise the target hardware without changing the model
specification:

* Vectorisation and shared-memory parallelism
* Loop blocking and auto-tuning
* Symbolic optimisations:
    * Common sub-expression elimination (CSE)
    * Loop re-writing and expression hoisting
</div>

<div class="col-sm-1 pull-right" markdown="1"></div>
<div class="col-sm-4 pull-right" markdown="1">
<img src="images/acoustic_skl8180.png" alt="skl8180" style="width:100%;"/>

Performance of acoustic wave modelling operator with different stencil
sizes and auto-tuning on single-socket E5-2697 v4 CPU (Broadwell, 16
cores @ 2.3GHz).
</div>
<div class="col-sm-1 pull-right" markdown="1"></div>
</div>  <!--End row-->


<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### Citing Devito
</div>

<div class="col-sm-12 pull-left" markdown="1">
If you publish results using Devito, we would be grateful if you would cite the
following papers, submitted to ACM Transactions on Mathematical Software (TOMS) and Geoscientific Model Development (GMD):

```
@article{devito-compiler,
  author    = { {Luporini}, F. and {Lange}, M. and {Louboutin}, M. and {Kukreja}, N. and {H{\"u}ckelheim}, J. and {Yount}, C. and {Witte}, P. and {Kelly}, P.~H.~J. and {Gorman}, G.~J. and {Herrmann}, F.~J. },
  title     = { Architecture and performance of Devito, a system for automated stencil computation },
  journal   = { CoRR },
  volume    = { abs/1807.03032 },
  month     = { jul },
  year      = { 2018 },
  url       = { http://arxiv.org/abs/1807.03032 },
  archivePrefix = { arXiv },
  eprint    = { 1807.03032 }
}
@article{devito-api,
  author  = { {Louboutin}, M. and {Lange}, M. and {Luporini}, F. and {Kukreja}, N. and {Witte}, P.~A. and {Herrmann}, F.~J.
  			  and {Velesko}, P. and {Gorman}, G.~J. },
  title   = {Devito: an embedded domain-specific language for finite differences and geophysical exploration},
  journal = { CoRR },
  volume  = { abs/1808.01995 },
  month   = { Aug },
  year    = { 2018 },
  url     = { https://arxiv.org/abs/1808.01995 },
  archivePrefix = { arXiv },
  eprint  = { 1808.01995 }
}
```
</div>
</div>  <!--End row-->
