# Depiction of CXSMILES

This section will contain the Groovy script to do the depiction too, but
for now you can use the online [CDK Depict tool](https://www.simolecule.com/cdkdepict/depict.html).

## Groovy code

We can also create depictions of CXSMILES with Groovy code, here for a class of lipids:

**Script** [code/CXSMILESDepict.groovy](code/CXSMILESDepict.code.md)
```groovy
mol1 = sp.parseSmiles("C\\C=C\\CC(=O)O")
sp.parseMolCXSMILES("|Sg:n:0:x:ht,Sg:n:3:y:ht|", mol1)
new DepictionGenerator()
  .depict(mol1)
  .writeTo("lipids.svg");
```

The output looks like this:

![SVG depiction of the lipds](./images/generates/lipids.svg)

## References



