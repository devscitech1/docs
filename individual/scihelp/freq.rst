


freq
====

frequency response



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [x]=freq(A,B,C [,D],f)
    [x]=freq(NUM,DEN,f)




Arguments
~~~~~~~~~

:A, B, C, D real matrices of respective dimensions `nxn, nxp, mxn,
  mxp`.
: :NUM,DEN polynomial matrices of dimension `mxp`
: :x real or complex matrix
:



Description
~~~~~~~~~~~

`x=freq(A,B,C [,D],f)` returns a real or complex `mxp*t` matrix such
that:

`x(:,k*p:(k+1)*p)= C*inv(f(k)*eye()-A)*B + D`.

Thus, for `f` taking values along the imaginary axis or on the unit
circle `x` is the continuous or discrete time frequency response of
`(A,B,C,D)`.

`x=freq(NUM,DEN,f)` returns a real or complex matrix `x` such that
columns `k*(p-1)+1` to `k*p` of `x` contain the matrix
`NUM(f(k))./DEN(f(k))`



Examples
~~~~~~~~


::

    s=`poly`_(0,'s');
    sys=(s+1)/(s^3-5*s+4)
    rep=freq(sys("num"),sys("den"),[0,0.9,1.1,2,3,10,20])
    [`horner`_(sys,0),`horner`_(sys,20)]
    //
    Sys=`tf2ss`_(sys);
    [A,B,C,D]=`abcd`_(Sys);
    freq(A,B,C,[0,0.9,1.1,2,3,10,20])




See Also
~~~~~~~~


+ `repfreq`_ frequency response
+ `horner`_ polynomial/rational evaluation


.. _horner: horner.html
.. _repfreq: repfreq.html


