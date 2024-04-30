# SGroups.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.9')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.9')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.CDKConstants;
import org.openscience.cdk.sgroup.Sgroup;
import org.openscience.cdk.sgroup.SgroupType;

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")

println("The S groups:")
sgroups = mol.getProperty(CDKConstants.CTAB_SGROUPS);
for (sgroup : sgroups) {
  if (sgroup.getType() == SgroupType.CtabStructureRepeatUnit) {
    println("" + sgroup.type + " with " + sgroup.getAtoms().size() + " atoms and "  + sgroup.getBonds().size() + " bonds")
  }
}
```
**Output:**
```plain
The S groups:
CtabStructureRepeatUnit with 1 atoms and 2 bonds
CtabStructureRepeatUnit with 1 atoms and 2 bonds
```
