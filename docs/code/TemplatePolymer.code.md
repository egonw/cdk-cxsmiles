# TemplatePolymer.groovy
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

polymer = sp.parseSmiles(
  "[*]c1Nc(cc1)c1Nc(cc1)[*] |Sg:n:1,2,3,4,5,6,7,8,9,10::ht|"
)
new DepictionGenerator()
  .depict(polymer)
  .writeTo("polymer.svg");
```
**Output:**
```plain
```
