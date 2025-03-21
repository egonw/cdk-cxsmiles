# DataModel.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.10')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")

println("The atoms:")
for (atom : mol.atoms()) {
  println("" + atom.getSymbol() + " with " + atom.getImplicitHydrogenCount() + " hydrogens")
}

 println()

println("The bonds:")
for (bond : mol.bonds()) {
  println("" + bond.getOrder() + " between " + bond.getAtomCount() + " atoms")
}
```
**Output:**
```plain
The atoms:
H with 0 hydrogens
C with 2 hydrogens
C with 1 hydrogens
C with 1 hydrogens
C with 2 hydrogens
C with 0 hydrogens
O with 0 hydrogens
O with 1 hydrogens

The bonds:
SINGLE between 2 atoms
SINGLE between 2 atoms
DOUBLE between 2 atoms
SINGLE between 2 atoms
SINGLE between 2 atoms
DOUBLE between 2 atoms
SINGLE between 2 atoms
```
