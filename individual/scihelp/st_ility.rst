


st_ility
========

stabilizability test



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [ns, [nc, [,U [,Slo] ]]]=st_ility(Sl [,tol])




Arguments
~~~~~~~~~

:Sl `syslin` list (linear system)
: :ns integer (dimension of stabilizable subspace)
: :nc integer (dimension of controllable subspace `nc <= ns`)
: :U basis such that its `ns` (resp. `nc`) first components span the
  stabilizable (resp. controllable) subspace
: :Slo a linear system ( `syslin` list)
: :tol threshold for controllability detection (see contr)
:



Description
~~~~~~~~~~~

`Slo=( U'*A*U, U'*B, C*U, D, U'*x0 )` ( `syslin` list) displays the
stabilizable form of `Sl`. Stabilizability means `ns=nx` (dim. of `A`
matrix).


::

    [*,*,*]            [*]
    U'*A*U = [0,*,*]     U'*B = [0]
    [0,0,*]            [0]


where `(A11,B1)` (dim(A11)= `nc`) is controllable and `A22` (dim(A22)=
`ns-nc`) is stable. "Stable" means real part of eigenvalues negative
for a continuous linear system, and magnitude of eigenvalues lower
than one for a discrete-time system (as defined by `syslin`).



Examples
~~~~~~~~


::

    A=`diag`_([0.9,-2,3]);B=[0;0;1];Sl=`syslin`_('c',A,B,[]);
    [ns,nc,U]=st_ility(Sl);
    U'*A*U
    U'*B
    [ns,nc,U]=st_ility(`syslin`_('d',A,B,[]));
    U'*A*U
    U'*B




See Also
~~~~~~~~


+ `dt_ility`_ detectability test
+ `contr`_ controllability, controllable subspace, staircase
+ `stabil`_ stabilization
+ `ssrand`_ random system generator


.. _dt_ility: dt_ility.html
.. _stabil: stabil.html
.. _ssrand: ssrand.html
.. _contr: contr.html


