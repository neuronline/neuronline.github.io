# NEURON NMODL (.mod) Files

## General Information

* Named blocks have the general form ```KEYWORD { statements }```
* User defined variables can be up to 20 characters.

### Variable Declaration Blocks
#### ```PARAMETER```
#### ```STATE```
#### ```ASSIGNED```

### Special Blocks
#### ```NEURON```
#### ```INITIAL```
#### ```BREAKPOINT```
#### ```DERIVATIVE```
#### ```KINETIC```
#### ```FUNCTION```

### Keywords
#### ```SUFFIX```
#### ```NONSPECIFIC_CURRENT```
#### ```RANGE```

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
