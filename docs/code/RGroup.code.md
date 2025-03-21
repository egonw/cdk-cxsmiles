# RGroup.groovy
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

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

lipid = sp.parseSmiles(
  "[NH3+]CCOP([O-])(=O)OC[C@@H](CO\\C=C/[*])OC([*])=O |\$;;;;;;;;;;;;;;R;;;R\$|"
)
new DepictionGenerator()
  .withMolTitle()
  .depict(lipid)
  .writeTo("rgroup.svg");
```
**Output:**
```plain
```
