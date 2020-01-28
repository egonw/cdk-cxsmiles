# CXSMILES in the CDK

The CDK supports a subset of CXSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussing](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CXSMILES

### Lipids

CXSMILES for lipids can use the `C\C=C\CC(=O)O |Sg:n:0:x:ht,Sg:n:3:y:ht|` syntax.
We can parse this into a CDK data model with the following code:

