# TemplateCopolymer.groovy
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

polymer = sp.parseSmiles(
  "[*]C(=O)CC(C)OC(=O)CC(CC)O[*] |Sg:n:1,2,3,4,5,6:m:ht,Sg:n:7,8,9,10,11,12,13:n:ht|"
)
new DepictionGenerator()
  .depict(polymer)
  .writeTo("copolymer.svg");
```
**Output:**
```plain
```
