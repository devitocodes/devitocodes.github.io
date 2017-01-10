---
layout: default
permalink: /devito

#title: "Devito: Fast Symbolic Finite Difference Computation"

---

<div class="col-sm-12 pull-left" markdown="1">
### Symbolic Finite Difference Computation

<div class="col-sm-7 pull-left" markdown="1">

</div>

<div class="col-sm-5 pull-right" markdown="1">
```
from devito import TimeData, Operator
from sympy.abc import s, h

u = TimeData(name=’u’, shape=(nx, ny),
             time_order=1, space_order=2)
u.data[0, :] = ui[:]

eqn = Eq(u.dt, a * (u.dx2 + u.dy2))
stencil = solve(eqn, u.forward)[0]
op = Operator(stencils=Eq(u.forward, stencil),
              subs={h: dx, s: dt}, nt=timesteps)
op.apply()
```

Example code for a 2D diffusion operator from a symbolic
definition. The full tutorial can be found
[here](http://www.opesci.org/devito-docs/heat.html).
</div>
</div>

<div class="col-sm-12 pull-left" markdown="1">
### Seismic Inversion using Devito

</div>

<div class="col-sm-12 pull-left" markdown="1">
### Optimisation and Performance

</div>

