


eigenmarkov
===========

normalized left and right Markov eigenvectors



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [M,Q]=eigenmarkov(P)




Arguments
~~~~~~~~~

:P real N x N Markov matrix. Sum of entries in each row should add to
  one.
: :M real matrix with N columns.
: :Q real matrix with N rows.
:



Description
~~~~~~~~~~~

Returns normalized left and right eigenvectors associated with the
eigenvalue 1 of the Markov transition matrix P. If the multiplicity of
this eigenvalue is m and P is N x N, M is a m x N matrix and Q a N x m
matrix. M(k,:) is the probability distribution vector associated with
the kth ergodic set (recurrent class). M(k,x) is zero if x is not in
the k-th recurrent class. Q(x,k) is the probability to end in the k-th
recurrent class starting from x. If `P^k` converges for large `k` (no
eigenvalues on the unit circle except 1), then the limit is `Q*M`
(eigenprojection).



Examples
~~~~~~~~


::

    //P has two recurrent classes (with 2 and 1 states) 2 transient states
    P=`genmarkov`_([2,1],2) 
    [M,Q]=eigenmarkov(P);
    P*Q-Q
    Q*M-P^20




See Also
~~~~~~~~


+ `genmarkov`_ generates random markov matrix with recurrent and
  transient classes
+ `classmarkov`_ recurrent and transient classes of Markov matrix


.. _genmarkov: genmarkov.html
.. _classmarkov: classmarkov.html


