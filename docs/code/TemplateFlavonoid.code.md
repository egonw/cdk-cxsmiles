# TemplateFlavonoid.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.9')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.9')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.9')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

flavo = sp.parseSmiles(
  "O*.O*.C1=C(C(=C2C(=C1)OC(=CC2=O)C3=CC(=C(C=C3)))).O* |m:3:4.5,m:1:8.9,m:22:18.19|"
)
new DepictionGenerator()
  .withMolTitle()
  .depict(flavo)
  .writeTo("flavonoid.svg");
```
**Output:**
```plain
```
