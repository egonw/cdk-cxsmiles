# Example.groovy
**Source code:**
```groovy
import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.*;
@Grab(group='org.openscience.cdk', module='cdk-bundle', version='2.3')
sp = new SmilesParser(
  DefaultChemObjectBuilder.getInstance()
)
mol = sp.parseSmiles("CC(=O)OC1=CC=CC=C1C(=O)O")
println "Aspirin has ${mol.atomCount} atoms."
```
**Output:**
```plain
Aspirin has 13 atoms.
```
