# Depiction of CXSMILES

This section will contain the Groovy script to do the depiction too, but
for now you can use the online [CDK Depict tool](https://www.simolecule.com/cdkdepict/depict.html).

**Script** [code/CXSMILESDepict.groovy](code/CXSMILESDepict.code.md)
```groovy
sp = new SmilesParser(
  DefaultChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("C\\C=C\\CC(=O)O")
sp.parseMolCXSMILES("|Sg:n:0:x:ht,Sg:n:3:y:ht|", mol1)
```

## References



