# CxSMILES in the CDK

The CDK supports a subset of CxSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussion](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CxSMILES

CxSMILES for lipids can use the `[H]C\C=C\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|` syntax.
We can parse this into a CDK data model with the regular approach:

**Script** [code/ParseCXSMILES.groovy](code/ParseCXSMILES.code.md)
```groovy
sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
```

## The internal graph model


## References



