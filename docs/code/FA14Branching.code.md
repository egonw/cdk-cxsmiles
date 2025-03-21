# FA14Branching.groovy
**Source code:**
```groovy
@Grab(group='io.github.egonw.jliebisch', module='liebisch', version='1.0')
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.10')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;

import io.github.egonw.jliebisch.LMAbbrevTool

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

mol1 = sp.parseSmiles("CC(CC(C(=C)C(C)(C)C)(C(=O)(O))C)(C)C")
new DepictionGenerator()
  .withMolTitle()
  .depict(mol1)
  .writeTo("FA_14_1.svg");
```
**Output:**
```plain
```
