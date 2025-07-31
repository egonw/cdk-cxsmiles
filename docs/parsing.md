# CxSMILES in the CDK

The CDK supports a subset of CxSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussion](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CxSMILES

CxSMILES for lipids can use the `[H]C\C=C\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|` syntax.
We can parse this into a CDK data model with the regular approach.

### Groovy

In <a name="tp1">Groovy</a> this
looks like this:

**Script** [code/ParseCXSMILES.groovy](code/ParseCXSMILES.code.md)
```groovy
sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
```

### Python

However, we can also use [pybacting](https://pypi.org/project/pybacting/) and parse the CxSMILES with <a name="tp2">Bacting</a> [<a href="#citeref1">1</a>]
(which uses the CDK in turn) in <a name="tp3">Python</a>:

```python
from pybacting import cdk
from scyjava import to_python as j2p
import IPython

cxmol = cdk.fromSMILES("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
svg = j2p(cdk.asSVG(cxmol))
display(IPython.display.SVG(svg))
```

We can even open this as a <a name="tp4">Jupyter Notebook</a> in
[Google Colab](https://colab.research.google.com/github/egonw/cdk-cxsmiles/blob/master/nb/parseCxSMILES.ipynb).

There are more examples available from [this notebook](https://github.com/egonw/cdk-cxsmiles/blob/master/nb/lipid_cxsmiles_scyjava_cdk.ipynb)
by Zhixu Ni, which can also be opened in [Google Colab](https://colab.research.google.com/github/egonw/cdk-cxsmiles/blob/master/nb/lipid_cxsmiles_scyjava_cdk.ipynb).

### CDKDepict

Finally, the online [CDKDepict](https://www.simolecule.com/cdkdepict/depict.html) can parse and process CxSMILES strings for
you without any coding.

## The internal graph model

After the CxSMILES is parsed by the CDK, it is stored in memory is an <a name="tp5">IAtomContainer</a>.
This IAtomContainer is the CDK data model for bonded atoms. Most commonly it is used to store the
chemical graph in which atoms are represented as vertices and bonds as edges. 

We can list the atoms and bonds with this code:

**Script** [code/DataModel.groovy](code/DataModel.code.md)
```groovy
println("The atoms:")
for (atom : mol.atoms()) {
  println("" + atom.getSymbol() + " with " + atom.getImplicitHydrogenCount() + " hydrogens")
}
println("The bonds:")
for (bond : mol.bonds()) {
  println("" + bond.getOrder() + " between " + bond.getAtomCount() + " atoms")
}
```

which lists:

```
The atoms:
H with 0 hydrogens
C with 2 hydrogens
C with 1 hydrogens
C with 1 hydrogens
C with 2 hydrogens
C with 0 hydrogens
O with 0 hydrogens
O with 1 hydrogens

The bonds:
SINGLE between 2 atoms
SINGLE between 2 atoms
DOUBLE between 2 atoms
SINGLE between 2 atoms
SINGLE between 2 atoms
DOUBLE between 2 atoms
SINGLE between 2 atoms
```

The other details are stored as properties on the atom container referring to the atoms
and bonds they apply to. As such, it can be seen as coloring the graph:

**Script** [code/SGroups.groovy](code/SGroups.code.md)
```groovy
println("The S groups:")
sgroups = mol.getProperty(CDKConstants.CTAB_SGROUPS);
for (sgroup : sgroups) {
  if (sgroup.getType() == SgroupType.CtabStructureRepeatUnit) {
    println("" + sgroup.type + " with " + sgroup.getAtoms().size() + " atoms and "  + sgroup.getBonds().size() + " bonds")
  }
}
```

which lists:

```
The S groups:
CtabStructureRepeatUnit with 1 atoms and 2 bonds
CtabStructureRepeatUnit with 1 atoms and 2 bonds
```

## Writing as an SD file

We can also write a CXSMILES to a SD file. We can use the following code for this:

**Script** [code/WriteSDF.groovy](code/WriteSDF.code.md)
```groovy
cxSMILES = "O=C(*)Oc1ccc(cc1)C(C)(C)c1ccc(O*)cc1 |Sg:n:0,1,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,19,20::ht|"
mol = sp.parseSmiles(cxSMILES)
writer = new FileWriter(new File("polybisacarb.sdf"))
SDFWriter sdfWriter = new SDFWriter(writer);
sdfWriter.write(mol);
```

The output uses the `*` as pseudoatom as in the input SMILES and exports the
CXSMILES aspects as additional annotation after the mol block:

```plain

  CDK     07312511242D

 21 22  0  0  0  0  0  0  0  0999 V2000
   -5.2108   -1.5321    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -3.9180   -0.7714    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -3.9304    0.7285    0.0000 *   0  0  0  0  0  0  0  0  0  0  0  0
   -2.6128   -1.5107    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -1.3200   -0.7500    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.0300   -1.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.3000   -0.7500    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.3000    0.7500    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.0300    1.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -1.3200    0.7500    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.6027    1.4936    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    3.8980    0.7372    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    3.5725    2.6379    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.6442    2.6474    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.1670    2.3869    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.7922    3.5074    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.2880    4.9671    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -1.2616    6.1082    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -0.7602    7.5219    0.0000 *   0  0  0  0  0  0  0  0  0  0  0  0
    1.1892    5.2276    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.1623    4.0283    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
  1  2  2  0  0  0  0
  2  3  1  0  0  0  0
  2  4  1  0  0  0  0
  4  5  1  0  0  0  0
  5  6  2  0  0  0  0
  6  7  1  0  0  0  0
  7  8  2  0  0  0  0
  8  9  1  0  0  0  0
  9 10  2  0  0  0  0
  5 10  1  0  0  0  0
  8 11  1  0  0  0  0
 11 12  1  0  0  0  0
 11 13  1  0  0  0  0
 11 14  1  0  0  0  0
 14 15  2  0  0  0  0
 15 16  1  0  0  0  0
 16 17  2  0  0  0  0
 17 18  1  0  0  0  0
 18 19  1  0  0  0  0
 17 20  1  0  0  0  0
 20 21  2  0  0  0  0
 14 21  1  0  0  0  0
M  STY  1   1 SRU
M  SAL   1 15  21  18   2   4   9   6  20   7   1  16  14   8  12  10  11
M  SAL   1  4  13  15   5  17
M  SBL   1  2  19   2
M  SMT   1 n
M  SCN  1   1 HT
M  SDI   1  4   -1.6471    7.0407   -0.3747    6.5894
M  SDI   1  4   -4.5992   -0.0270   -3.2492   -0.0159
M  END
> <PUBCHEM_SUBSTANCE_COMMENT>
O=C(*)Oc1ccc(cc1)C(C)(C)c1ccc(O*)cc1 |Sg:n:0,1,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,19,20::ht|

> <PUBCHEM_EXT_DATASOURCE_REGID>
NISTpolymer0006

> <PUBCHEM_SUBSTANCE_SYNONYM>
Poly(bisphenol-A-carbonate

$$$$
```

## References

1. <a name="citeref1"></a>Willighagen E. Bacting: a next generation, command line version of Bioclipse. JOSS. 2021 Jun 23;6(62):2558.  doi:[10.21105/JOSS.02558](https://doi.org/10.21105/JOSS.02558) ([Scholia](https://scholia.toolforge.org/doi/10.21105/JOSS.02558))


