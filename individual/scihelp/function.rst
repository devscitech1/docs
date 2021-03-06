


function
========

opens a function definition



endfunction
===========

closes a function definition



Description
~~~~~~~~~~~


::

    function <lhs_arguments>=<function_name><rhs_arguments>
      <statements>
    endfunction


Where

:<function_name> stands for the name of the function
: :<rhs_arguments> stands for the input argument list. It may be

    + a comma separated sequence of variable names enclosed in
      parenthesis, like `(x1,...,xm)`. Last variable name can be the key
      word `varargin` (see varargin)
    + the sequence `()` or nothing, if the function has no input argument.

: :<lhs_arguments> stands for the output argument list. It may be

    + a comma separated sequence of variable names enclosed in brackets,
      like `[y1,...,yn]`. Last variable name can be the key word `varargout`
      (see varargout)
    + the sequence `[]` ,if the function has no input argument. In this
      case the syntax may also be: `function <function_name><rhs_arguments>`

: :<statements> stands for a set of scilab instructions (statements)
  This syntax may be used to define function (see functions) inline or
  in a script file (see exec). For compatibility with old Scilab
  versions, functions defined in a script file containing only function
  definitions can be "loaded" into Scilab using the `exec` function.
:

The `function <lhs_arguments>=<function_name><rhs_arguments>` sequence
cannot be split over several lines. This sequence can be followed by
statements in the same line if a comma or a semicolon is added at its
end.

function definitions can be nested



Examples
~~~~~~~~


::

    //inline definition (see function)
    function [x, y]=myfct(a, b)
    x=a+b
    y=a-b
    endfunction
    
    [x,y]=myfct(3,2)
    
    //a one line function definition
    function y=sq(x),y=x^2,endfunction
    
    sq(3)
    
    //nested functions definition
    function y=foo(x)
    a=`sin`_(x)
    function y=sq(x), y=x^2,endfunction
    y=sq(a)+1
    endfunction
    
    foo(%pi/3)
    
    // definition in an script file (see exec)
    `exec`_ SCI/modules/elementary_functions/macros/asinh.sci;




See Also
~~~~~~~~


+ `functions`_ Scilab procedures and Scilab objects
+ `exec`_ script file execution


.. _exec: exec.html
.. _functions: functions.html


