Debugging Scala Implicits in IntelliJ
=====================================

This document outlines several complementary approaches for statically analysing Scala implicits in IntelliJ.

JetBrains provides a [document explaining the first two steps][working-with-scala-implicit-conversions], but excludes the clarification around analysing pimped methods.

*Note: These shortcuts are for OSX.*

Viewing implicit conversions<a name="implicit-conversions"></a>
----------------------------

1.  Highlight the converted type.

    **Important:** When investigating a conversion that introduces a pimped method, you MUST highlight the object only, NOT the pimped method. This is because the object is what's being converted. Selecting the method too will attempt to resolve the implicit conversion on the type returned by the pimped method, which probably isn't what you want to do!

2.  `CTRL` + `Q`

Viewing actual implicit parameters<a name="actual-implicits"></a>
----------------------------------

1.  Highlight a method with an implicit parameter list.

2.  `CMD` + `SHIFT` + `P`

*See [Viewing code without implicits](#without-implicits) if you receive 'Parameter not found'*

Viewing actual implicit parameters on implicit conversions<a name="actual-implicits-on-conversions"></a>
----------------------------------------------------------

The following requires modifying the code:

1.  Perform steps in 'Viewing implicit conversions'

2.  Highlight appropriate implicit conversion function.

3.  `ALT` + `ENTER` (and then `ENTER` to select 'Make explicit').

4.  Perform steps in [Viewing actual implicit parameters](#actual-implicits).

Viewing code without implicits<a name="without-implicits"></a>
------------------------------

This is the last resort: it displays the 'unravelled' Scala code, which is useful if you don't have IntelliJ or IntelliJ is unable to
resolve implicit parameters:

1.  Run from the command line:

        sbt "set scalacOptions in Compile += \"-Xprint:typer\"" "compile"

2.  Ignore the initial output.

3.  'Touch' the file you are interested in.

4.  Re-run step 1.

[working-with-scala-implicit-conversions]: http://confluence.jetbrains.com/display/IntelliJIDEA/Working+with+Scala+Implicit+Conversions "Working with Scala Implicit Conversions"
