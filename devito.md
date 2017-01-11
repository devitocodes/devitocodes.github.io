---
layout: default
permalink: /devito

#title: "Devito: Fast Symbolic Finite Difference Computation"

---

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### **Devito**: Symbolic Finite Difference Computation
</div>

<div class="col-sm-6 pull-left" markdown="1">
Devito is a prototype Domain-specific Language (DSL) and code
generation framework for the design of highly optimised finite
difference kernels for use in inversion methods. Devito utilises
[SymPy](www.sympy.org) to allow the definition of operators from
high-level symbolic equations and generates optimised and
automatically tuned code specific to a given target architecture.

Symbolic computation is a powerful tool that allows users to:

* Build complex solvers from only a few lines of high-level code
* Use automated performance optimisation for generated code
* Adjust stencil discretisation at runtime as required
* (Re-)development of solver code in hours rather than months

#### **Documentation**

Documentation for Devito is available
[here](http://www.opesci.org/devito-docs/index.html), including
[installation
instructions](http://www.opesci.org/devito-docs/download.html), a set
of [tutorials](http://www.opesci.org/devito-docs/tutorials.html) and
[API documentation](http://www.opesci.org/devito-docs/devito.html).
In addition, a paper outlining the use of symbolic Python to define
finite difference operators in Devito can be found
[here](https://arxiv.org/abs/1609.03361).

</div>

<div class="col-sm-1 pull-left" markdown="1"></div>
<div class="col-sm-4 pull-left" markdown="1">
```
from devito import TimeData, Operator
from sympy.abc import s, h

u = TimeData(name=’u’, shape=(nx, ny),
             time_order=1, space_order=2)
u.data[0, :] = initial_data[:]

eqn = Eq(u.dt, a * (u.dx2 + u.dy2))
stencil = solve(eqn, u.forward)[0]
op = Operator(
   stencils=Eq(u.forward, stencil),
   subs={h: dx, s: dt}, nt=timesteps
)
op.apply()
```

Example code for a 2D diffusion operator from a symbolic
definition. The full tutorial can be found
[here](http://www.opesci.org/devito-docs/heat.html).
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
[here](http://www.opesci.org/devito-docs/wave.html) and a paper
outlining the verification procedures of the acoustic operator can be
found [here](https://arxiv.org/abs/1608.08658).
<br/>

<img src="images/ModelPerturbation.png" alt="ModelPerturbation" style="width:100%;"/>

<img src="images/RTM.png" alt="RTM" style="width:100%;"/>
</div>

<div class="col-sm-6 pull-left" markdown="1">
<img src="images/DualShot-eps-converted-to.png" alt="DualShot" style="width:90%;"/>
</div>
</div>  <!--End row-->

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">
### Optimisation and Performance
</div>

<div class="col-sm-6 pull-left" markdown="1">
Devito provides a set of automated performance optimiza-
tions during code generation that allow user applications to
fully utilise the target hardware without changing the model
specification:

* Vectoriastion and shared-memory parallelism
* Loop blocking and auto-tuning
* Symbolic optimisations:
    * Common sub-expression elimination (CSE)
    * Loop re-writing and expression hoisting
</div>

<div class="col-sm-1 pull-right" markdown="1"></div>
<div class="col-sm-4 pull-right" markdown="1">
<img src="images/acoustic_at_broadwell.png" alt="AcousticBroadwellAT" style="width:100%;"/>

Performance of acoustic wave modelling operator with different stencil
sizes and auto-tuning on single-socket E5-2697 v4 CPU (Broadwell, 16
cores @ 2.3GHz).
</div>
<div class="col-sm-1 pull-right" markdown="1"></div>
</div>  <!--End row-->
