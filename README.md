Debugging Scala Implicits in IntelliJ
=====================================

Viewing implicit conversions
----------------------------

1.  Highlight the converted type.

    -   IMPORTANT: When investigating a conversion that is introducing a pimped method, you MUST highlight the object only, NOT the
        pimped method. This is because the object is the thing being converted. Selecting the method too will attempt to resolve the
        implicit conversion on the type returned by the pimped method, which probably isn't what you want to do!

2.  CTRL+Q


Viewing actual implicit parameters
----------------------------------

1.  Highlight a method with an implicit parameter list.

2.  CMD+SHIFT+P

*See 'Viewing code without implicits' if you receive 'Parameter not found'*

Viewing actual implicit parameters on implicit conversions
----------------------------------------------------------

1.  Perform steps in 'Viewing implicit conversions'

2.  Highlight appropriate implicit conversion function.

3.  ALT+ENTER (and then ENTER to select 'Make Explicit').

4.  Perform steps in 'Viewing actual implicit parameters'.

Viewing code without implicits
------------------------------

This is the last resort: it displays the 'unravelled' Scala code, which is useful if you don't have IntelliJ or IntelliJ is unable to
resolve implicit parameters:

1.  Run from the command line:

        sbt "set scalacOptions in Compile += \"-Xprint:typer\"" "compile"

2.  Ignore the initial output.

3.  'Touch' the file you are interested in.

4.  Re-run step 1.
