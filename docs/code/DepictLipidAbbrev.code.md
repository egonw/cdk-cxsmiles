# DepictLipidAbbrev.groovy
**Source code:**
```groovy
@Grab(group='io.github.egonw.jliebisch', module='liebisch', version='1.0-SNAPSHOT')
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.9')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.9')
@Grab(group='org.openscience.cdk', module='cdk-depict', version='2.9')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.isomorphism.UniversalIsomorphismTester;
import org.openscience.cdk.depict.DepictionGenerator;

import io.github.egonw.jliebisch.LMAbbrevTool

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

cxsmiles = LMAbbrevTool.cxsmiles("CE 16:1")
mol1 = sp.parseSmiles(cxsmiles)
new DepictionGenerator()
  .withMolTitle()
  .depict(mol1)
  .writeTo("CE_16:1.svg");
```
**Output:**
```plain
```
