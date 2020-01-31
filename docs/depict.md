# Depiction of CxSMILES

This section will contain the Groovy script to do the depiction too, but
for now you can use the online [CDK Depict tool](https://www.simolecule.com/cdkdepict/depict.html).

## Groovy code

We can also create depictions of CxSMILES with Groovy code, here for a class of lipids:

**Script** [code/CXSMILESDepict.groovy](code/CXSMILESDepict.code.md)
```groovy
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
new DepictionGenerator()
  .depict(mol1)
  .writeTo("lipids.svg");
```

The output looks like this:

<img src="./images/generated/lipids.svg" width="400" alt="SVG depiction of the lipds" />

## References



