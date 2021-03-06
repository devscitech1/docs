


hermit
======

Hermite form



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [Ar,U]=hermit(A)




Arguments
~~~~~~~~~

:A polynomial matrix
: :Ar triangular polynomial matrix
: :U unimodolar polynomial matrix
:



Description
~~~~~~~~~~~

Hermite form: `U` is an unimodular matrix such that `A*U` is in
Hermite triangular form:

The output variable is `Ar=A*U`.

Warning: Experimental version



Examples
~~~~~~~~


::

    s=`poly`_(0,'s');
    p=[s, s*(s+1)^2, 2*s^2+s^3];
    [Ar,U]=hermit(p'*p);
    `clean`_(p'*p*U), `det`_(U)




See Also
~~~~~~~~


+ `hrmt`_ gcd of polynomials
+ `htrianr`_ triangularization of polynomial matrix


.. _hrmt: hrmt.html
.. _htrianr: htrianr.html


