


auread
======

load .au sound file



Calling Sequence
~~~~~~~~~~~~~~~~


::

    y=auread(aufile)
    y=auread(aufile,ext)
    [y,Fs,bits]=auread(aufile)
    [y,Fs,bits]=auread(aufile,ext)




Arguments
~~~~~~~~~

:aufile string (The .au extension is appended if no extension is
  given)
: :Fs ...
: :[] integer, frequency sampling in Hz.
: :ext string ( `'size'` or `'snd'`) or integer (to read n samples) or
  1 x 2 integer vector [n1,n2] (to read from n1 to n2).
:



Description
~~~~~~~~~~~

Utility function to read `.au` sound file. `auread(aufile)` loads a
sound file specified by the string aufile, returning the sampled data
in y. Amplitude values are in the range [-1,+1].

Supports multi-channel data in the following formats: 8-bit mu-law,
8-, 16-, and 32-bit linear, and floating point.

`[y,Fs,bits]=auread(aufile)` returns the sample rate (Fs) in Hertz and
the number of bits per sample used to encode the data in the file.

`auread(aufile,n)` returns the first n samples from each channel.

`auread(aufile,[n1,n2])` returns samples n1 to n2.

`auread(aufile,'size')` returns the size of the audio data contained
in the file in place of the actual audio data, returning the vector as
[samples channels].

`auread(aufile,'snd')` returns information about the sample and data
as a tlist.



Examples
~~~~~~~~


::

    y=`wavread`_('SCI/modules/sound/demos/chimes.wav');
    
    // default is 8-bits mu-law
    `auwrite`_(y,TMPDIR+'/tmp.au');
    y1=auread(TMPDIR+'/tmp.au');
    `max`_(`abs`_(y-y1))




See Also
~~~~~~~~


+ `savewave`_ save data into a sound wav file.
+ `analyze`_ frequency plot of a sound signal
+ `mapsound`_ Plots a sound map


.. _savewave: savewave.html
.. _analyze: analyze.html
.. _mapsound: mapsound.html


