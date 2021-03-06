


assert_cond2reqdigits
=====================

Suggests the number of required digits, given the condition number.



Calling Sequence
~~~~~~~~~~~~~~~~


::

    d = assert_cond2reqdigits ( condition )
    d = assert_cond2reqdigits ( condition , offset )
    d = assert_cond2reqdigits ( condition , offset , b )




Parameters
~~~~~~~~~~

:condition : a matrix of doubles, the condition number. The condition
  number must be strictly positive.
: :offset : a matrix of doubles, a shift for the number of required
  base-b digits (default offset=0). For example, offset=-1 produces a
  smaller number of required digits (reduces the required accuracy),
  offset=1 produces a larger number of required digits (increases the
  required accuracy).
: :b : a matrix of doubles, integer values, the b (default b = 10).
: :d : a matrix of doubles, the number of required digits. This is a
  positive real, between 0 and 15.95, if b=10 or between 0 and 53, if
  b=2.
:



Description
~~~~~~~~~~~

Depending on the condition number, returns the corresponding number of
required decimal digits.

Any optional parameter equal to the empty matrix [] is set to its
default value.

We emphasize that this number of required digits is only a suggestion.
Indeed, there may be correct reasons of using a lower or a higher
relative tolerance.



+ Consider the case where an excellent algorithm is able to make
  accurate computations, even for an ill-conditionned problem. In this
  case, we may require more accuracy (positive offset).
+ Consider the case where there is a trade-off between performance and
  accuracy, where performance wins. In this case, we may require less
  accuracy (negative offset).



Any scalar input argument is expanded to a matrix of doubles of the
same size as the other input arguments.

The algorithm is the following. We compute the base-10 logarithm of
condition, then subtract the offset. This number represents the
expected number of lost digits. We project it into the interval
[0,dmax], where dmax -log10(2^(-53)) is the maximum achievable number
of accurate digits for doubles. We compute the number of required
digits d, by difference between dmax and the number of lost digits.
Then the relative tolerance is 10^-d.





Examples
~~~~~~~~


::

    assert_cond2reqdigits ( 0 ) // 15.95459
    assert_cond2reqdigits ( 1 ) // 15.95459
    assert_cond2reqdigits ( 1.e1 ) // 14.95459
    assert_cond2reqdigits ( 1.e2 ) // 13.95459
    assert_cond2reqdigits ( 1.e3 ) // 12.95459
    assert_cond2reqdigits ( 1.e16 ) // 0
    assert_cond2reqdigits ( 1.e17 ) // 0
    assert_cond2reqdigits ( 1.e18 ) // 0
    
    // Matrix input.
    condition = [0,1,10,100,1000,1.D13,1.D14,1.D15,1.D16,1.D17,1.D18];
    assert_cond2reqdigits ( condition )
    
    // Using offset
    // Netative offset : decrease number of required digits (requires less accuracy)
    assert_cond2reqdigits ( 1.e2 , [0 -1] ) // [13.95459    12.95459]
    // Positive offset : increase number of required digits (requires more accuracy)
    // See that the impact of offset is constrained.
    assert_cond2reqdigits ( 1.e2 , [0 1 2 3] ) // [13.95459    14.95459    15.95459    15.95459]
    // Netative offset (requires less accuracy)
    // See that the impact of offset is constrained.
    assert_cond2reqdigits ( 1.e14 , [0 -1 -2 -3] ) // [1.9545898    0.9545898    0.    0.]
    
    // Using base-2
    assert_cond2reqdigits ( 0     , [] , 2 ) // 53
    assert_cond2reqdigits ( 1     , [] , 2 ) // 53
    assert_cond2reqdigits ( 1.e1  , [] , 2 ) // 49.678072
    assert_cond2reqdigits ( 1.e2  , [] , 2 ) // 46.356144
    assert_cond2reqdigits ( 1.e3  , [] , 2 ) // 43.034216
    assert_cond2reqdigits ( 1.e16 , [] , 2 ) // 0
    assert_cond2reqdigits ( 1.e17 , [] , 2 ) // 0
    assert_cond2reqdigits ( 1.e18 , [] , 2 ) // 0
    
    // Plot the number of required decimal digits depending on the condition
    condition = `logspace`_(0,18,1000);
    d = assert_cond2reqdigits ( condition );
    `plot`_(condition,d)
    h=`gcf`_();
    h.children.log_flags="lnn";
    h.children.children.children.thickness=4;
    xt = h.children.x_ticks;
    xt.locations = 10^(0:2:18)';
    xt.labels = ["10^0";"10^2";"10^4";"10^6";"10^8";"10^10";"10^12";"10^14";"10^16";"10^18"];
    h.children.x_ticks=xt;
    `xtitle`_("Number of required digits","Condition","Required decimal digits");
    
    // Plot the number of required binary digits depending on the condition
    condition = `logspace`_(0,18,1000);
    d = assert_cond2reqdigits ( condition , [] , 2 );
    `plot`_(condition,d)
    h=`gcf`_();
    h.children.log_flags="lnn";
    h.children.children.children.thickness=4;
    xt = h.children.x_ticks;
    xt.locations = 10^(0:2:18)';
    xt.labels = ["10^0";"10^2";"10^4";"10^6";"10^8";"10^10";"10^12";"10^14";"10^16";"10^18"];
    h.children.x_ticks=xt;
    `xtitle`_("Number of required digits","Condition","Required binary digits");
    d = assert_cond2reqdigits ( condition , +10 , 2 );
    `plot`_(condition,d,"r")
    d = assert_cond2reqdigits ( condition , -10 , 2 );
    `plot`_(condition,d,"g")
    `legend`_(["Offset=0","Offset=+10","Offset=-10"]);




History
~~~~~~~
Version Description 5.4.0 Function introduced


