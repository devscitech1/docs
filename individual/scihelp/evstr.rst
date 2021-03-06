


evstr
=====

evaluation of expressions



Calling Sequence
~~~~~~~~~~~~~~~~


::

    H=evstr(Z)
    [H,ierr]=evstr(Z)




Arguments
~~~~~~~~~

:Z matrix of character strings `M` or `list(M,Subexp)`
    :M matrix of character strings
    : :Subexp vector of character strings
    :

: :H matrix
: :ierr integer, error indicator
:



Description
~~~~~~~~~~~

Returns the result of the evaluation of the matrix of character
strings `M`. Each element of the matrix must define a valid Scilab
expression.

If the evaluation of `M` expression leads to an error, the single
return value version, `H = evstr(M)`, raises the error as usual. The
two return values version, `[H,ierr] = evstr(M)`, on the other hand,
produces no error, but returns the error number in `ierr`.

If `Z` is a list, `Subexp` is a vector of character strings, that
defines sub_expressions which are evaluated before evaluating `M`.
These sub_expressions must be referred to as `%(k)` in `M`, where `k`
is the sub-expression's index in `Subexp`.

evstr('a = 1') is not valid (use `execstr` instead).

Nan, NaN will be interpreted as %nan.

Inf will be interpreted as %inf.



Examples
~~~~~~~~


::

    a = 1; b = 2; Z = ['a', 'b'] ; evstr(Z) 
          a = 1; b = 2; Z = `list`_(['%(1)','%(1)-%(2)'],['a+1','b+1']);
          evstr(Z)
          
          evstr('NaN'), evstr('Inf')




See Also
~~~~~~~~


+ `execstr`_ execute Scilab code in strings


.. _execstr: execstr.html


