# TemplateLipidDoubleBond.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.11')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.11')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.11')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

lipid = sp.parseSmiles(
  "[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht| x+y=15"
)
new DepictionGenerator()
  .withMolTitle()
  .depict(lipid)
  .writeTo("lipid_doublebond.svg");
```
**Output:**
```plain
```
