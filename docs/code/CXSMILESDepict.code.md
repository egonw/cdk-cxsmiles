# CXSMILESDepict.groovy
**Source code:**
```groovy
import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.DefaultChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.3')
@Grab(group='org.openscience.cdk', module='cdk-data', version='2.3')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.3')


sp = new SmilesParser(
  DefaultChemObjectBuilder.getInstance()
)

mol1 = sp.parseSmiles("C\\C=C\\CC(=O)O")
sp.parseMolCXSMILES("|Sg:n:0:x:ht,Sg:n:3:y:ht|", mol1)
new DepictionGenerator()
  .depict(mol1)
  .writeTo("lipids.svg");
```
**Output:**
```plain
```
