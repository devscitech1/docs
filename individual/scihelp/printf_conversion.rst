


printf_conversion
=================

mprintf, msprintf, mfprintf conversion specifications



Description
~~~~~~~~~~~

Each conversion specification in the `mprintf` , `msprintf` ,
`fprintf` `format` parameter has the following syntax:


+ A % (percent) sign.
+ Zero or more `options`, which modify the meaning of the conversion
  specification. The following list contains the `option` characters and
  their meanings:

    + - : Left align, within the field, the result of the conversion.
    + + : Begin the result of a signed conversion with a sign (+ or -).
    + 'space' : Prefix a space character to the result if the first
      character of a signed conversion is not a sign. If both the (space)
      and + options appear, the (space) option is ignored
    + # : Convert the value to an alternate form. For `c`, `d`, `i`, `s`,
      and `u` conversions, the `#` option has no effect. For `o` conversion,
      `#` increases the precision to force the first digit of the result to
      be a 0 (zero). For `x` and `X` conversions, a nonzero result has 0x or
      0X prefixed to it. For `e, E, f, g,` and `G` conversions, the result
      always contains a decimal point, even if no digits follow it. For `g`
      and `G` conversions, trailing zeros are not removed from the result.
    + 0 : Pad to the field width, using leading zeros (following any
      indication of sign or base) for `d`, `i`, `o`, `u`, `x`, `X`, `e`,
      `E`, `f`, `g`, and `G` conversions; no space padding is performed. If
      the `0` and `\-` (dash) flags both appear, the `0` flag is ignored.
      For `d`, `i`, `o` `u`, `x`, and `X` conversions, if a precision is
      specified, the `0` flag is also ignored.

+ An optional decimal digit string that specifies the minimum field
  width. If the converted value has fewer characters than the field
  width, the field is padded on the left to the length specified by the
  field width. If the left-adjustment option is specified, the field is
  padded on the right.
+ An optional precision. The precision is given by a dot `.` followed
  by a decimal digit string. If no precision is given, the parameter is
  treated as 0 (zero). The precision specifies:

    + The minimum number of digits to appear for `d`, `u`, `o`, `x`, or
      `X` conversions
    + The number of digits to appear after the decimal point for `e`, `E`,
      and `f` conversions
    + The maximum number of significant digits for `g` and `G` conversions
    + The maximum number of characters to be printed from a string in an
      `s` conversion

+ A character that indicates the type of conversion to be applied:

    + % : Performs no conversion. Displays %.
    + d,i: Accepts an integer `value` and converts it to signed decimal
      notation. The precision specifies the minimum number of digits to
      appear. If the value being converted can be represented in fewer
      digits, it is expanded with leading zeros. The default precision is 1.
      The result of converting a zero value with a precision of zero is a
      null string. Specifying a field width with a zero as a leading
      character causes the field width value to be padded with leading
      zeros.
    + u : Accepts an integer `value` and converts it to unsigned decimal
      notation. The precision specifies the minimum number of digits to
      appear. If the value being converted can be represented in fewer
      digits, it is expanded with leading zeros. The default precision is 1.
      The result of converting a zero value with a precision of zero is a
      null string. Specifying a field width with a zero as the leading
      character causes the field width value to be padded with leading
      zeros.
    + o : Accepts an integer `value` and converts it to unsigned octal
      notation. The precision specifies the minimum number of digits to
      appear. If the value being converted can be represented in fewer
      digits, it is expanded with leading zeros. The default precision is 1.
      The result of converting a zero value with a precision of zero is a
      null string. Specifying a field width with a zero as the leading
      character causes the field width value to be padded with leading
      zeros. An octal value for field width is not implied.
    + x, X : Accepts an integer `value` and converts it to unsigned
      hexadecimal notation. The letters ``abcdef'' are used for the `x`
      conversion; the letters ``ABCDEF'' are used for the `X` conversion.
      The precision specifies the minimum number of digits to appear. If the
      value being converted can be represented in fewer digits, it is
      expanded with leading zeros. The default precision is 1. The result of
      converting a zero value with a precision of zero is a null string.
      Specifying a field width with a zero as the leading character causes
      the field width value to be padded with leading zeros.
    + f : Accepts a float or double `value` and converts it to decimal
      notation in the format %[\-] `ddd.ddd`. The number of digits after the
      decimal point is equal to the precision specification.

        + If no precision is specified, six digits are output.
        + If the precision is zero, no decimal point appears and the system
          outputs a number rounded to the integer nearest to `value`.
        + If a decimal point is output, at least one digit is output before
          it.

    + e, E : Accepts a real and converts it to the exponential form %[\-]
      `d.ddde`+/\- `dd`. There is one digit before the decimal point, and
      the number of digits after the decimal point is equal to the precision
      specification.

        + If no precision is specified, six digits are output.
        + If the precision is zero, , no decimal point appears.
        + The `E` conversion character produces a number with E instead of e
          before the exponent. The exponent always contains at least two digits.
          If the value is zero, the exponent is zero.

    + g, G : Accepts a real and converts it in the style of the `e`, `E`,
      or `f` conversion characters, with the precision specifying the number
      of significant digits. Trailing zeros are removed from the result. A
      decimal point appears only if it is followed by a digit. The style
      used depends on the value converted. Style `e` ( `E`, if `G` is the
      flag used) results only if the exponent resulting from the conversion
      is less than -4, or if it is greater or equal to the precision.
    + c : Accepts and displays an integer value converted to a character.
    + s : Accepts a string `value` and displays characters from the string
      to the end or the number of characters indicated by the precision is
      reached. If no precision is specified, all characters up to the end
      are displayed.



A field width or precision can be indicated by an `*` (asterisk)
instead of a digit string. In this case, an integer `value` parameter
supplies the field width or precision. The `value` parameter converted
for output is not fetched until the conversion letter is reached, so
the parameters specifying field width or precision must appear before
the value to be converted (if any).

If the result of a conversion is wider than the field width, the field
is expanded to contain the converted result.

The representation of the plus sign depends on whether the `+` or
(space) formatting option is specified.

display of exponential form %e is platform dependent with a different
number of digits in exponent.
Platform Example: msprintf("%e",1.23e4) Windows 1.23000e+004 Linux/Mac
OS 1.23000e+04


Examples
~~~~~~~~


::

    `mprintf`_('a string: %s\n', 'Scilab');
    `mprintf`_('an integer: %d\n', 10);
    `mprintf`_('an integer: %4d\n', 10);
    `mprintf`_('a left justified integer: %-4d\n', 10);
    `mprintf`_('an integer converted to float: %#fd\n',10);
    `mprintf`_('an integer with a sign: %+4d\n', 10);
    `mprintf`_('an integer with a sign: %+4d\n', -10);
    `mprintf`_('an integer padded with zeros: %04d\n', 10);
    `mprintf`_('an unsigned integer: %u\n', 10);
    `mprintf`_('an unsigned integer: %4u\n', -10);
    `mprintf`_('an integer converted to hexadecimal: %x\n', 10);
    `mprintf`_('a float: %d\n', %pi);
    `mprintf`_('a float: %3.2d\n', %pi);
    `mprintf`_('a float (exponential form): %3.2e\n', %pi);
    `mprintf`_('a float (exponential form): %3.2g\n', %pi);
    `mprintf`_('a character: %c\n', 'a');
    `mprintf`_('a character: %c\n', 'aaa');




See Also
~~~~~~~~


+ `mprintf`_ converts, formats, and writes data to the main scilab
  window
+ `fprintf`_ Emulator of C language fprintf function. This function is
  obsolete
+ `msprintf`_ converts, formats, and writes data in a string


.. _mprintf: mprintf.html
.. _msprintf: msprintf.html
.. _fprintf: fprintf.html


