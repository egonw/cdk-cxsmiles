# ParseCXSMILES.groovy
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
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
```
**Output:**
```plain
```
