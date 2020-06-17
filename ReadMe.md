WLDiagram R class
=================

The R class WLDiagram draws a Walter and Lieth (1960) diagram.
Units for the diagram can be either SI or Imperial.

This class was originally part of the R package ClimatePrimers, produced
at the Natural Resource Ecology Laboratory, Colorado State University,
and previously at the North Central Climate Adaptation Science Center
at Colorado State University.

![](./Example-WLDiagram.png?raw=true "WLDiagram plot from test")


## Usage

Package 'grid' draws the plot.
A grob (grid plot object) is returned,
which can then be displayed with 'grid.draw'.

Climatic data is a
data.frame containing 12 columns (one per month, January to December)
and 4 rows, one per variable. The variables are:

| variable | description | units |
| ---------| ------------| ------|
| prec | Mean monthly precipitation| in or mm |
| tmin | Mean maximum daily temperature per month | F or C |
| tmax | Mean minimum daily temperature per month | F or C |
| atmn | Absolute monthly minimum temperature per month | F or C |

Absolute monthly minimum temperature is
used to determine the probable frost months
(when absolute monthly minimums are equal or lower than 0 C).

As described by Walter and Lieth, when monthly precipitation is
greater than 100 mm, the scale is increased from 2 mm/C to 20 mm/C
to avoid too high diagrams in very wet locations. This change is
indicated by a black horizontal line, and the graph over it is
filled in solid blue.

When the precipitation graph lies under the temperature graph (P <
2T) we have an arid period (filled in dotted red vertical lines).
Otherwise the period is considered wet (filled in blue lines),
unless 'p3line=TRUE', that draws a precipitation black line with a
scale P = 3T; in this case the period in which 3T > P > 2T is
considered semi-arid.

Daily maximum average temperature of the hottest month and daily
minimum average temperature of the coldest month are frequently
used in vegetation studies, and are labeled in black at the left
margin of the diagram.

### About WLDiagram::diagwl.grid plot function

This function was modified the from the climatol::diagwl function;
see the R package climatol for the original.

Modifications to the original function:

* The original used the R base graphics package.
  This version uses the R grid package.
* The original diagwl function returns the final grob.
  This version returns a grobTree.
* Added English translations to the original Spanish comments.
* Added additional error checks.
* Added optional display of English units along with SI units.
* Viewport is only in npc units; lines units are not used.
* Code for drawing of the precipitation line with diagonal
  lines under it, has been rewritten.

### Run the test

    R  # start the R console in this directory
    source( "Test_WLDiagram.R" )


## Explaination of the diagram

![](./WLDiagram-Annotated.svg?raw=true "WLDiagram Annotated")

The Walter and Lieth (1960, 1963) climate diagrams summarize mean precipitation and temperature for one site or region. Vertical scales are constant so that the visual pattern from different locations can be quickly compared. The astronomic summer is always shown in the middle of the diagram, hence the month scale begins in January in the northern hemisphere, and July in the southern. Vertical blue lines indicate humid periods, and dashed red lines indicate dryer periods. Months with likely frost and probable frost are shown in the bar at 0 C.


## Author

Thomas E. Hilinski <tom.hilinski@colostate.edu>

Plot function is derived from function diagwl in the
R package climatol, written by
Jose A. Guijarro <jguijarrop at aemet.es>

Suggestions and feedback were provided by
Dennis Ojima and Robert Flynn at the
Natural Resource Ecology Laboratory, Colorado State University.

## Files

    WLDiagram.R            - class WLDiagram

    ClimateVars.R          - Functions for climate variable names
    MiscUtils.R            - Miscellaneous functions
    TextProcessing.R       - Utilities for modifying text for display
    Units.R                - Units conversion functions
    PlotBase.R             - Base class for class WLDiagram

    Test_WLDiagram.R       - Test class WLDiagram
    data_PerMonth.rds      - Data for test
    Example-WLDiagram.png  - Plot produced by test script.

## Reference

Walter, H., Lieth, H., 1960.
Klimadiagramma-Weltatlas. G. Fischer Verlag, Jena.

## License

See the file LICENSE.md in this repository.
