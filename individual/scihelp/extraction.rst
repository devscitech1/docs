


extraction
==========

matrix and list entry extraction



Calling Sequence
~~~~~~~~~~~~~~~~


::

    x(i)
    x(i,j)
    x(i,j,k,..)
    [...]=l(i)
    [...]=l(k1)...(kn)(i) or [...]=l(list(k1,...,kn,i))
    l(k1)...(kn)(i,j) or l(list(k1,...,kn,list(i,j))




Arguments
~~~~~~~~~

:x matrix of any possible types
: :l list variable
: :i,j, k indices
: :k1,...kn indices
:



Description
~~~~~~~~~~~

:MATRIX CASE `i`, `j`, `k`,.. can be:
    :a real scalar or a vector or a matrix with positive elements.

        + `r=x(i,j)` builds the matrix `r` such as
          `r(l,k)=x(int(i(l)),int(j(k)))` for `l` from 1 to `size(i,'*')` and
          `k` from 1 to `size(j,'*')`. `i` ( `j`) Maximum value must be less or
          equal to `size(x,1)` ( `size(x,2)`).
        + `r=x(i)` with `x` a 1x1 matrix builds the matrix `r` such as
          `r(l,k)=x(int(i(l)),int(i(k)))` for `l` from 1 to `size(i,1)` and `k`
          from 1 to `size(i,2)`. Note that in this case index `i` is valid only
          if all its entries are equal to one.
        + `r=x(i)` with `x` a row vector builds the row vector `r` such as
          `r(l)=x(int(i(l)))` for `l` from 1 to `size(i,'*')` `i` Maximum value
          must be less or equal to `size(x,'*')`.
        + `r=x(i)` with `x` a matrix with one or more columns builds the
          column vector `r` such as `r(l)` ( `l` from 1 to `size(i,'*')`)
          contains the `int(i(l))` entry of the column vector formed by the
          concatenation of the `x`'s columns. `i` Maximum value must be less or
          equal to `size(x,'*')`.

    : :the symbol `:` `` which stands for "all elements".

        + `r=x(i,:)` builds the matrix `r` such as `r(l,k)=x(int(i(l)),k))`
          for `l` from 1 to `size(i,'*')` and `k` from 1 to `size(x,2)`
        + `r=x(:,j)` builds the matrix `r` such as `r(l,k)=x(l,int(j(k)))` for
          `l` from 1 to `size(r,1)` and `k` from 1 to `size(j,'*')`.
        + `r=x(:)` builds the column vector `r` formed by the column
          concatenations of `x` columns. It is equivalent to
          `matrix(x,size(x,'*'),1)`.

    : :a vector of boolean If an index ( `i` or `j`) is a vector of
      booleans it is interpreted as `find(i)` or respectively `find(j)`
    : :a polynomial If an index ( `i` or `j`) is a vector of polynomials
      or implicit polynomial vector it is interpreted as `horner(i,m)` or
      respectively `horner(j,n)` where `m` and `n` are associated `x`
      dimensions. Even if this feature works for all polynomials, it is
      recommended to use polynomials in `$` for readability.
    :
For matrices with more than 2 dimensions (see:`hypermatrices`_) the
  dimensionality is automatically reduced when right-most dimensions are
  equal to 1.
: :LIST OR TLIST CASE If they are present the `ki` give the path to a
sub-list entry of `l` data structure. They allow a recursive
extraction without intermediate copies. The instructions
`[...]=l(k1)...(kn)(i)` and `[...]=l(list(k1,...,kn,i))` are
interpreted as: `lk1 = l(k1)` `.. = ..` `lkn = lkn-1(kn)` `[...] =
lkn(i)`. And the `l(k1)...(kn)(i,j)` and `l(list(k1,...,kn,list(i,j))`
instructions are interpreted as: `lk1 = l(k1)` `.. = ..` `lkn =
lkn-1(kn)` `lkn(i,j)` When path points on more than one list component
the instruction must have as many left hand side arguments as selected
components. But if the extraction syntax is used within a function
input calling sequence each returned list component is added to the
function calling sequence. Note that, `l(list())` is the same as `l`.
    :i and j may be :
        :real scalar or vector or matrix with positive elements.
          `[r1,...rn]=l(i)` extracts the `i(k)` elements from the list `l` and
          store them in `rk` variables for `k` from 1 to `size(i,'*')`
        : :the symbol `:` which stands for "all elements".
        : :a vector of booleans. If `i` is a vector of booleans it is
          interpreted as `find(i)`.
        : :a polynomial If `i` is a vector of polynomials or implicit
          polynomial vector it is interpreted as `horner(i,m)` where
          `m=size(l)`. Even if this feature works for all polynomials, it is
          recommended to use polynomials in `$` for readability.
        :

    : :k1 ... kn may be :
        :real positive scalar
        : :a polynomial interpreted as `horner(ki,m)` where `m` is the
          corresponding sub-list size.
        : :a character string associated with a sub-list entry name.
        :

    :

:



Remarks
~~~~~~~

For soft coded matrix types such as rational functions and state space
linear systems, `x(i)` syntax may not be used for vector element
extraction due to confusion with list element extraction. `x(1,j)` or
`x(i,1)` syntax must be used.



Examples
~~~~~~~~


::

    // MATRIX CASE
    a=[1 2 3;4 5 6]
    a(1,2)
    a([1 1],2)
    a(:,1)
    a(:,3:-1:1)
    a(1)
    a(6)
    a(:)
    a([%t %f %f %t])
    a([%t %f],[2 3])
    a(1:2,$-1)
    a($:-1:1,2)
    a($)
    //
    x='test'
    x([1 1;1 1;1 1])
    //
    b=[1/%s,(%s+1)/(%s-1)]
    b(1,1)
    b(1,$)
    b(2) // the numerator
    // LIST OR TLIST CASE
    l=`list`_(1,'qwerw',%s)
    l(1)
    [a,b]=l([3 2])
    l($)
    x=`tlist`_(l(2:3)) //form a tlist with the last 2 components of l
    //
    dts=`list`_(1,`tlist`_(['x';'a';'b'],10,[2 3]));
    dts(2)('a')
    dts(2)('b')(1,2)
    [a,b]=dts(2)(['a','b'])




See Also
~~~~~~~~


+ `find`_ find indices of boolean vector or matrix true elements
+ `horner`_ polynomial/rational evaluation
+ `parents`_ ( ) left and right parenthesis
+ `insertion`_ partial variable assignation or modification


.. _parents: parents.html
.. _insertion: insertion.html
.. _horner: horner.html
.. _find: find.html
.. _hypermatrices: hypermatrices.html


