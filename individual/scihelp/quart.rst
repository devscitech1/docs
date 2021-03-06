


quart
=====

computation of quartiles



Calling Sequence
~~~~~~~~~~~~~~~~


::

    s=quart(x)
    s=quart(x,'r') or m=quart(x,1)
    s=quart(x,'c') or m=quart(x,2)




Arguments
~~~~~~~~~

:x real or complex vector or matrix
:



Description
~~~~~~~~~~~

For a vector or a matrix x, [q]=quart(x,y) returns in the vector q the
quartiles of x. [q]=quart(x,'r') (or, equivalently, [q]=quart(x,1))
are the rowwise percentiles. It returns in each column of the matrix q
the quartiles of data in the corresponding column of x.

[q]=quart(x,'c') (or, equivalently, [q]=quart(x,2)) are the columnwise
quartiles. It returns in each row of the matrix q the quartiles of
data in the corresponding row of x.



Examples
~~~~~~~~


::

    x=[6 7 0 7 10 4 2 2 7 1;
       6 0 5 5 5 2 0 6 8 10;
       8 6 4 3 5 9 8 3 4 7;
       1 3 2 7 6 1 1 4 8 2;
       6 3 5 1 6 5 9 9 5 5;
       1 6 4 4 5 4 0 8 1 8;
       7 1 3 7 8 0 2 8 10 8;
       3 6 1 9 8 5 5 3 2 1;
       5 7 6 2 10 8 7 4 0 8;
       10 3 3 4 8 6 9 4 8 3]
    q=quart(x)
    q=quart(x,'r')
    q=quart(x,'c')




Bibliography
~~~~~~~~~~~~

Wonacott, T.H. & Wonacott, R.J.; Introductory Statistics, fifth
edition, J.Wiley & Sons, 1990.



