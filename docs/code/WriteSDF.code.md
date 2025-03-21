# WriteSDF.groovy
**Source code:**
```groovy
@Grab(group='org.openscience.cdk', module='cdk-smiles', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-silent', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-ctab', version='2.10')
@Grab(group='org.openscience.cdk', module='cdk-sdg', version='2.10')

import org.openscience.cdk.smiles.SmilesParser;
import org.openscience.cdk.interfaces.*;
import org.openscience.cdk.silent.SilentChemObjectBuilder;
import org.openscience.cdk.io.*;
import org.openscience.cdk.layout.StructureDiagramGenerator;
import javax.vecmath.Vector2d

sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)

cxSMILES = "O=C(*)Oc1ccc(cc1)C(C)(C)c1ccc(O*)cc1 |Sg:n:0,1,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,19,20::ht|"
mol = sp.parseSmiles(cxSMILES)
sdg = new StructureDiagramGenerator();
sdg.setMolecule(mol);
sdg.generateCoordinates(new Vector2d(0, 1));
mol = sdg.getMolecule();
mol.setProperty("PUBCHEM_SUBSTANCE_SYNONYM", "Poly(bisphenol-A-carbonate")
mol.setProperty("PUBCHEM_SUBSTANCE_COMMENT", cxSMILES)
mol.setProperty("PUBCHEM_EXT_DATASOURCE_REGID", "NISTpolymer0006")
writer = new FileWriter(new File("polybisacarb.sdf"))
SDFWriter sdfWriter = new SDFWriter(writer);
sdfWriter.write(mol);
sdfWriter.close();
writer.close();
```
**Output:**
```plain
```
