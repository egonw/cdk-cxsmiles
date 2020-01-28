# Creating CXSMILES

This chapter covers the following use case: experiment data has provided
a short list of possible chemical structures, for example, resulting from
a database search on molecular formula or m/z value. Often, the top hits
of posititional isomers, and the wish exists to convert these isomers
into a Markush structure and represented as CXSMILES.

## Maximal Common Substructure

**Script** [code/MCS.groovy](code/MCS.code.md)
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.3')
@Grab(group='org.openscience.cdk', module='cdk-data', version='2.3')
uiTester = new UniversalIsomorphismTester();
sp = new SmilesParser(
  DefaultChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("NCC(=O)OC1=CC=CC=C1C(=O)O")
mol2 = sp.parseSmiles("CCC(=O)OC1=CC=CC=C1C(=O)O")
List<IAtomContainer> list = uiTester.getOverlaps(mol1, mol2);
println "Overlaps: ${list.size()}"
for (ac in list) {
  println "  atom count in overlap: ${ac.atomCount}"
}
```

## SDF in, CXSMILES out


## References



