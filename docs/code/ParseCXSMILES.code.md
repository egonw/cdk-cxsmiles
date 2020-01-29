# ParseCXSMILES.groovy
**Source code:**
```groovy
import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.3')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.3')

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
```
**Output:**
```plain
```
