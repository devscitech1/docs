


insertion
=========

partial variable assignation or modification



assignation
===========

partial variable assignation



Calling Sequence
~~~~~~~~~~~~~~~~


::

    x(i,j)=a
    x(i)=a
    l(i)=a
    l(k1)...(kn)(i)=a or l(list(k1,...,kn,i))=a
    l(k1)...(kn)(i,j)=a or l(list(k1,...,kn,list(i,j))=a




Arguments
~~~~~~~~~

:x matrix of any kind (constant, sparse, polynomial,...)
: :l list
: :i,j indices
: :k1,...kn indices with integer value
: :a new entry value
:



Description
~~~~~~~~~~~

:MATRIX CASE If `x` is a matrix the indices `i` and `j`, may be:
    :Real scalars or vectors or matrices In this case the values given as
    indices should be positive and it is only their integer part which
    taken into account.

        + If `a` is a matrix with dimensions `(size(i,'*'),size(j,'*'))`,
          `x(i,j)=a` returns a new `x` matrix such as
          `x(int(i(l)),int(j(k)))=a(l,k)` for `l` from 1 to `size(i,'*')` and
          `k` from 1 to `size(j,'*')`, other initial entries of `x` are
          unchanged.
        + If `a` is a scalar `x(i,j)=a` returns a new `x` matrix such as
          `x(int(i(l)),int(j(k)))=a` for `l` from 1 to `size(i,'*')` and `k`
          from 1 to `size(j,'*')`, other initial entries of `x` are unchanged.
        + If `i` or `j` maximum value exceed corresponding `x` matrix
          dimension, array `x` is previously extended to the required dimensions
          with zeros entries for standard matrices, 0 length character string
          for string matrices and false values for boolean matrices.
        + `x(i,j)=[]` kills rows specified by `i` if `j` matches all columns
          of `x` or kills columns specified by `j` if `i` matches all rows of
          `x`. In other cases `x(i,j)=[]` produce an error.
        + `x(i)=a` with an `a` vector returns a new `x` matrix such as
          `x(int(i(l)))=a(l)` for `l` from 1 to `size(i,'*')`, other initial
          entries of `x` are unchanged.
        + `x(i)=a` with an `a` scalar returns a new `x` matrix such as
        `x(int(i(l)))=a` for `l` from 1 to `size(i,'*')`, other initial
        entries of `x` are unchanged. If `i` maximum value exceed `size(x,1)`,
        `x` is previously extended to the required dimension with zeros
        entries for standard matrices, 0 length character string for string
        matrices and false values for boolean matrices.
            :if `x` is a 1x1 matrix `a` may be a row (respectively a column)
              vector with dimension `size(i,'*')`. Resulting `x` matrix is a row
              (respectively a column) vector
            : :if `x` is a row vector `a` must be a row vector with dimension
              `size(i,'*')`
            : :if `x` is a column vector `a` must be a column vector with
              dimension `size(i,'*')`
            : :if `x` is a general matrix `a` must be a row or column vector with
              dimension `size(i,'*')` and `i` maximum value cannot exceed
              `size(x,'*')`.
            :

        + `x(i)=[]` kills entries specified by `i`.

    : :The : symbol The `:` symbol stands for "all elements".

        + `x(i,:)=a` is interpreted as `x(i,1:size(x,2))=a`
        + `x(:,j)=a` is interpreted as `x(1:size(x,1),j)=a`
        + `x(:)=a` returns in `x` the `a` matrix reshaped according to `x`
          dimensions. `size(x,'*')` must be equal to `size(a,'*')`.

    : :Vectors of boolean If an index ( `i` or `j`) is a vector of
      booleans it is interpreted as `find(i)` or respectively `find(j)`.
    : :Polynomials If an index ( `i` or `j`) is a vector of polynomials or
      implicit polynomial vector it is interpreted as `horner(i,m)` or
      respectively `horner(j,n)` where `m` and `n` are associated `x`
      dimensions. Even if this feature works for all polynomials, it is
      recommended to use polynomials in `$` for readability.
    :

: :LIST OR TLIST CASE

    + If they are present the `ki` give the path to a sub-list entry of
      `l` data structure. They allow a recursive insertion without
      intermediate copies. The `l(k1)...(kn)(i)=a` and
      `l(list(k1,...,kn,i)=a)` instructions are interpreted as: `lk1 =
      l(k1)` `.. = ..` `lkn = lkn-1(kn)` `lkn(i) = a` `lkn-1(kn) = lkn` `..
      = ..` `l(k1) = lk1` And the `l(k1)...(kn)(i,j)=a` and
      `l(list(k1,...,kn,list(i,j))=a` instructions are interpreted as: `lk1
      = l(k1)` `.. = ..` `lkn = lkn-1(kn)` `lkn(i,j) = a` `lkn-1(kn) = lkn`
      `.. = ..` `l(k1)= lk1`
    + `i` may be :

        + a real non negative scalar. `l(0)=a` adds an entry on the "left" of
          the list. `l(i)=a` sets the `i` entry of the list `l` to `a`. If
          `i>size(l)`, `l` is previously extended with zero length entries
          (undefined). `l(i)=null()` deletes the `i`th list entry.
        + a polynomial. If `i` is a polynomial it is interpreted as
          `horner(i,m)` where `m=size(l)`. Even if this feature works for all
          polynomials, it is recommended to use polynomials in `$` for
          readability.

    + `k1,..kn` may be :

        + real positive scalar.
        + a polynomial, interpreted as `horner(ki,m)` where `m` is the
          corresponding sub-list size.
        + a character string associated with a sub-list entry name.


:



Remarks
~~~~~~~

For soft coded matrix types such as rational functions and state space
linear systems, `x(i)` syntax must not be used for vector entry
insertion due to confusion with list entry insertion. `x(1,j)` or
`x(i,1)` syntax must be used.



Examples
~~~~~~~~


::

    // MATRIX CASE
    a=[1 2 3;4 5 6]
    a(1,2)=10
    a([1 1],2)=[-1;-2]
    a(:,1)=[8;5]
    a(1,3:-1:1)=[77 44 99]
    a(1)=%s
    a(6)=%s+1
    a(:)=1:6
    a([%t %f],1)=33
    a(1:2,$-1)=[2;4]
    a($:-1:1,1)=[8;7]
    a($)=123
    //
    x='test'
    x([4 5])=['4','5']
    //
    b=[1/%s,(%s+1)/(%s-1)]
    b(1,1)=0
    b(1,$)=b(1,$)+1
    b(2)=[1 2] // the numerator
    // LIST OR TLIST CASE
    l=`list`_(1,'qwerw',%s)
    l(1)='Changed'
    l(0)='Added'
    l(6)=['one more';'added']
    //
    //
    dts=`list`_(1,`tlist`_(['x';'a';'b'],10,[2 3]));
    dts(2).a=33
    dts(2)('b')(1,2)=-100




See Also
~~~~~~~~


+ `find`_ find indices of boolean vector or matrix true elements
+ `horner`_ polynomial/rational evaluation
+ `parents`_ ( ) left and right parenthesis
+ `extraction`_ matrix and list entry extraction


.. _parents: parents.html
.. _find: find.html
.. _horner: horner.html
.. _extraction: extraction.html


