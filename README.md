Breakpoint Slicer
=================

Along with Respond To, Breakpoint Slicer is an alternative syntax for [Breakpoint][1].


Concept
-------

Imagine the breakpoints of your site on a scale:

     Breakpoint:   0                 400px     600px     800px       1050px
                   ├───────────────────┼─────────┼─────────┼───────────┼─────────>

See those spans between breakpoints? Let's name them "slices".

Breakpoint Slicer numbers the slices sequentially:

     Breakpoint:   0                 400px     600px     800px       1050px
                   ├───────────────────┼─────────┼─────────┼───────────┼─────────>
     Slice #:                1              2         3          4          5
     
The goal of breakpoint slicer is to let you quickly set breakpoints using those numbers instead of px/em values.


Usage
-----

Breakpoint Slicer offers four handy mixins that let you set breakpoint ranges easily: `at`, `from`, `to` and `between`:

Styles under `at(3)`        are applied when browser window width is inside the 3rd slice.

Styles under `from(3)`      are applied when browser window width is inside the 3rd slice or larger.

Styles under `to(3)`        are applied when browser window width is inside the 3rd slice or larger.

Styles under `between(2,4)` are applied when browser window width is inside the 2nd, 4rd slice or any slice between the two (if any).

     Breakpoint:   0                 400px     600px     800px       1050px
                   ├───────────────────┼─────────┼─────────┼───────────┼─────────>
     Slice #:                1         ·    2         3          4     ·    5
                   ·                   ·         ·         ·           ·
                   ·                   ·         ·  at(3)  ·           ·
                   ·                   ·         ├─────────┤           ·
                   ·                   ·         ·         ·           ·
                   ·                   ·         · from(3) ·           ·
                   ·                   ·         ├───────────────────────────────>
                   ·                   ·                   ·           ·
                   ·                   ·            to(3)  ·           ·
                   ├───────────────────────────────────────┤           ·
                                       ·                               ·
                                       ·         between(2, 4)         ·
                                       ├───────────────────────────────┤


Note that the last slice does not have a right edge. When it is invoked, the media query will have no max-width value.

Some mixins become synonomous when used for the last slice:

     Breakpoint:   0                 400px     600px     800px       1050px
                   ├───────────────────┼─────────┼─────────┼───────────┼─────────>
     Slice #:                1         ·    2         3          4     ·    5
                                       ·                               ·
                                       ·                               ·  at(5)
                                       ·                               ├─────────>
                                       ·                               ·
                                       ·                               · from(5)
                                       ·                               ├─────────>
                                       ·
                                       ·                  from(2)
                                       ├─────────────────────────────────────────>
                                       ·
                                       ·               between(2, 5)
                                       ├─────────────────────────────────────────>

And `to` becomes meaningless:

     Breakpoint:   0                 400px     600px     800px       1050px
                   ├───────────────────┼─────────┼─────────┼───────────┼─────────>
     Slice #:      ·         1              2         3          4          5
                   ·
                   ·                                                      to(5)
                   ├─────────────────────────────────────────────────────────────>

Note that the max-width of your site's container should be somewhere in the fifth slice.



  [1]: https://github.com/Team-Sass/breakpoint
