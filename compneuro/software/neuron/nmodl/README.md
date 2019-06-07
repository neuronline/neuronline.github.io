# NEURON NMODL (.mod) Files

## General Information

* Named blocks have the general form ```KEYWORD { statements }```
* User defined variables can be up to 20 characters.

### Variable Declaration Blocks
* Users may specify units appropriate for variables, except for those defined by neuron:
    * ```v``` (millivolts)
    * ```t``` (milliseconds)
    * ```celsius``` (C)
    * ```diam``` (um)
    * ```area``` (um^2)
* Ex:
    ```` 
    PARAMETER {  
      g = 0.001  (siemens/cm2)  < 0, 1e9 >
    }
    ````
#### ```PARAMETER```
* Variables specified here are assigned by user or changed by hoc 
* They do not typically change but can throughought but can emulate some external influence on the characteristic properties of the model
    * Time-dependent PARAMETER changes - Models with discontinuities
* They appear in nrnpointmenu
* Ex:
    ```
    g = 0.001  (siemens/cm2)  < 0, 1e9 >  : variable = value (units) <minimum, maximum value that can be entered via gui>
    ```
* Any parameter that doesn't appear in a ```NEURON``` block's ```RANGE``` statement will have a ```GLOBAL``` scope, meaning that chaning the value will affect every instance of that mechanism throughout an entire model.

#### ```STATE```
#### ```ASSIGNED```
Can be used to declare two kinds of variables:
* those given values outside the mod file
* those that appear on the left hand side of assignment statements in the mod file
The first group includes variables potentially available to every mechanism, like ```v, celsius, t``` and ionic variables.

The second group omits variables that are unknons in simmultaneous linear or nonlinear algebraic equations, or that are dependent variables in differential equations, or kinetic reaction schemes

* Values are not visible at the ```hoc``` level unless it's declared in a ```RANGE``` or ```GLOBAL``` statement

### Special Blocks
#### ```NEURON```
The ```NEURON``` blockdefines what the model of the mechanism looks like from the outside. 
#### ```INITIAL```
#### ```BREAKPOINT```
#### ```DERIVATIVE```
#### ```KINETIC```
#### ```FUNCTION```

### Keywords
#### ```SUFFIX```
Two purposes of ```SUFFIX```:
* Identifies this to be a distributed mechanism, used by an ```insert``` statement
* Tells the NEURON interpreter that the names for variables and parameters that belong to this mechanism will include the suffix. Ex:

*.mod file*
```
: comment here
NEURON {
  SUFFIX leak
  RANGE i
}
```

*NEURON file*
```
insert leak
print i_leak
```
#### ```NONSPECIFIC_CURRENT```
The ```NONSPECIFIC_CURRENT``` has two purposes:
* the value ```i``` specified after (Ex: ```NONSPECIFIC_CURRENT i```) will be reckonded in charge balance equations
* This current will make no contributions to mass balance equations
#### ```RANGE```
* Anything denoted by range is accessible by the ```hoc``` interpreter
* These variables are a function of position and can have different values for each of the segments that make up a section
* Each variable mentioned in ```RANGE``` should be declared in a ```PARAMETER``` or ```ASSIGNED``` block.
* Alternative to ```RANGE``` is ```GLOBAL```
#### ```GLOBAL```

### Other
#### Comments
* A single line comment starts with a colon "```:```"
* Multiline comments start with ```COMMENT``` and end with ```ENDCOMMENT```
#### Special Variables
```v,celsius,t,diam,area,dt```

```c
COMMENT
This is a
multiple line
comment
ENDCOMMENT
```

## Examples


### LEAK Current
```
: A passive leak current
NEURON {  
  SUFFIX leak  : How the mechanism will be refered to by NEURON code (insert leak) 
  NONSPECIFIC_CURRENT i  
  RANGE i, e, g : Values here will need to appear in PARAMETER or ASSIGNED
}
PARAMETER {  
  g = 0.001  (siemens/cm2)  < 0, 1e9 >  : variable = value (units)
  e = -65    (millivolt)
}
ASSIGNED {  
  i  (milliamp/cm2)  
  v  (millivolt)
}
BREAKPOINT { 
  i = g*(v - e) 
}
```

## References

* [NEURON Chapter 9](https://neuron.yale.edu/ftp/ted/book/revisions/chap9indexedref.pdf)
* [NEURON Chapter 10](https://neuron.yale.edu/ftp/ted/book/revisions/chap10indexedref.pdf)
