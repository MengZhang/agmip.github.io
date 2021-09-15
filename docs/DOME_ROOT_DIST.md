# ROOT_DIST - Root distribution function

Distributes roots (or other soil parameters) using an exponential decay curve from a maximum value in the top soil to a minimum value at depth.

### Inputs:
* M = Maximum value in the top PP cm of soil (units depend on variable)
* PP = depth of top soil, or pivot point of curve (cm)
* RD = maximum rooting depth (cm), or depth at which the value is 2% of the maximum value

### Implicit Inputs (i.e., available in the data):
* SLLB = array of depths to bottom of soil layer (cm)

### Outputs:
* F = array of soil factors which decline exponentially between PP and RD (units depend on variable, same units as M)

### Procedure:

```
/* exponential decay rate */
 k = LN(0.02)/(RD - PP)

/* loop thru soil layers */ 

/* midpoints of soil layers */
 mid(1) = SLLB(1) / 2 
 mid(j) = [SLLB(j) + SLLB(j-1)] / 2

 
If mid(j) <= PP
  then F(j) = M
  else F(j) = M * EXP{k *(mid(j) - PP)}
``` 

[Home](index.md)