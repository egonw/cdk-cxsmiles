# CoreStructure.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.10')

import org.openscience.cdk.smiles.SmilesGenerator;
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
substructureAtoms = new java.util.HashSet<IAtom>()
maplist = uiTester.getSubgraphAtomsMap(mol1, overlap);
for (mapping in maplist) {
  mol1Atom = mol1.getAtom(mapping.id1)
  substructureAtoms.add(mol1Atom)
}
for (bond in mol1.bonds()) {
  allCheckedAtomsInSubstructure = true
  for (bondAtom in bond.atoms()) {
    if (substructureAtoms.contains(bondAtom)) {
      atLeastOneAtomInSubstructure = true
    } else {
      allCheckedAtomsInSubstructure = false
    }
  }
  if (allCheckedAtomsInSubstructure) {
    // this is a bond in the substructure
    for (bondAtom in bond.atoms())
      if (!substructure.contains(bondAtom))
        substructure.addAtom(bondAtom)
    substructure.addBond(bond)
  } else if (atLeastOneAtomInSubstructure) {
    // this is an attachment point
  } else {
    // this is a bond in an R group
  }
}
sg = SmilesGenerator.isomeric();
println "core structure:"
println "" + sg.create(substructure)
```
**Output:**
```plain
core structure:
[CH2]C(=O)OC1=CC=CC=C1C(=O)O
```
