


ltitr
=====

discrete time response (state space)



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [X]=ltitr(A,B,U,[x0])
    [xf,X]=ltitr(A,B,U,[x0])




Arguments
~~~~~~~~~

:A,B real matrices of appropriate dimensions
: :U,X real matrices
: :x0,xf real vectors (default value=0 for `x0`))
:



Description
~~~~~~~~~~~

calculates the time response of the discrete time system


::

    x[t+1] = Ax[t] + Bu[t].


The inputs `ui`'s are the columns of the `U` matrix


::

    U=[u0,u1,...,un];


`x0` is the vector of initial state (default value : 0) ;

`X` is the matrix of outputs (same number of columns as `U`).


::

    X=[x0,x1,x2,...,xn]


`xf` is the vector of final state `xf=X[n+1]`



Examples
~~~~~~~~


::

    A=`eye`_(2,2);B=[1;1];
    x0=[-1;-2];
    u=[1,2,3,4,5];
    x=ltitr(A,B,u,x0)
    x1=A*x0+B*u(1)
    x2=A*x1+B*u(2)
    x3=A*x2+B*u(3) //....




See Also
~~~~~~~~


+ `rtitr`_ discrete time response (transfer matrix)
+ `flts`_ time response (discrete time, sampled system)


.. _rtitr: rtitr.html
.. _flts: flts.html


