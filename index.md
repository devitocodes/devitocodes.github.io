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
Devito is a Python package to implement optimized stencil computation (e.g.,
finite differences, image processing, machine learning) from high-level
symbolic problem definitions. Devito builds on [SymPy](https://www.sympy.org)
and employs automated code generation and just-in-time compilation to execute
optimized computational kernels on several computer platforms, including CPUs,
GPUs, and clusters thereof.

Symbolic computation is a powerful tool that allows users to:

* Build complex solvers from only a few lines of high-level code
* Use automated performance optimisation for generated code
* Adjust stencil discretisation at runtime as required
* (Re-)development of solver code in hours/days rather than months
</div>

<div class="col-sm-1 pull-left" markdown="1"></div>
<div class="col-sm-4 pull-left" markdown="1">
<iframe width="100%" src="https://www.youtube.com/embed/druSsV_1O6w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
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
[here](https://nbviewer.jupyter.org/github/devitocodes/devito/blob/master/examples/seismic/tutorials/01_modelling.ipynb) and a paper
outlining the verification procedures of the acoustic operator can be
found [here](https://arxiv.org/abs/1608.08658).
<br/>

<img src="images/TrueFWI.jpg" alt="True velocity model (Marmousi-ii)" style="width:100%;"/>

<img src="images/InitFWI.jpg" alt="Initial velocity model for FWI" style="width:100%;"/>

<img src="images/FWI.jpg" alt="FWI inverted velocity model" style="width:100%;"/>
</div>

<div class="col-sm-6 pull-left" markdown="1">
<img src="images/Dual.jpg" alt="DualShot" style="width:90%;"/>
</div>
</div>  <!--End row-->

<div class="row" markdown="1">
<div class="col-sm-12 pull-left" markdown="1">

<div class="col-sm-1 pull-right" markdown="1"></div>
<div class="col-sm-4 pull-right" markdown="1"></div>
<div class="col-sm-1 pull-right" markdown="1"></div>
</div>  <!--End row-->
