


fstair
======

computes pencil column echelon form by qz transformations



Calling Sequence
~~~~~~~~~~~~~~~~


::

    [AE,EE,QE,ZE,blcks,muk,nuk,muk0,nuk0,mnei]=fstair(A,E,Q,Z,stair,rk,tol)




Arguments
~~~~~~~~~

:A m x n matrix with real entries.
: :tol real positive scalar.
: :E column echelon form matrix
: :Q m x m unitary matrix
: :Z n x n unitary matrix
: :stair vector of indexes (see ereduc)
: :rk integer, estimated rank of the matrix
: :AE m x n matrix with real entries.
: :EE column echelon form matrix
: :QE m x m unitary matrix
: :ZE n x n unitary matrix
: :nblcks is the number of submatrices having full row rank >= 0
  detected in matrix `A`.
: :muk: integer array of dimension (n). Contains the column dimensions
  mu(k) (k=1,...,nblcks) of the submatrices having full column rank in
  the pencil sE(eps)-A(eps)
: :nuk: integer array of dimension (m+1). Contains the row dimensions
  nu(k) (k=1,...,nblcks) of the submatrices having full row rank in the
  pencil sE(eps)-A(eps)
: :muk0: integer array of dimension (n). Contains the column
  dimensions mu(k) (k=1,...,nblcks) of the submatrices having full
  column rank in the pencil sE(eps,inf)-A(eps,inf)
: :nuk: integer array of dimension (m+1). Contains the row dimensions
  nu(k) (k=1,...,nblcks) of the submatrices having full row rank in the
  pencil sE(eps,inf)-A(eps,inf)
: :mnei: integer array of dimension (4). mnei(1) = row dimension of
  sE(eps)-A(eps)
:



Description
~~~~~~~~~~~

Given a pencil `sE-A` where matrix `E` is in column echelon form the
function `fstair` computes according to the wishes of the user a
unitary transformed pencil `QE(sEE-AE)ZE` which is more or less
similar to the generalized Schur form of the pencil `sE-A`. The
function yields also part of the Kronecker structure of the given
pencil.

`Q,Z` are the unitary matrices used to compute the pencil where E is
in column echelon form (see ereduc)



See Also
~~~~~~~~


+ `quaskro`_ quasi-Kronecker form
+ `ereduc`_ computes matrix column echelon form by qz transformations


.. _quaskro: quaskro.html
.. _ereduc: ereduc.html


