# VisualizeOverlap.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.10')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;

uiTester = new UniversalIsomorphismTester();
sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

mol1 = sp.parseSmiles("NCC(=O)OC1=CC=CC=C1C(=O)O")
mol2 = sp.parseSmiles("CCC(=O)OC1=CC=CC=C1C(=O)O")

List<IAtomContainer> list = uiTester.getOverlaps(mol1, mol2);
overlap = list[0]
substructure = mol1.builder.newInstance(IAtomContainer.class)
maplist = uiTester.getSubgraphAtomsMap(mol1, overlap);
for (mapping in maplist) { substructure.addAtom(mol1.getAtom(mapping.id1)) }
new DepictionGenerator()
  .withHighlight(substructure.atoms(), java.awt.Color.lightGray)
  .depict(mol1)
  .writeTo("overlap.svg");
```
**Output:**
```plain
```
