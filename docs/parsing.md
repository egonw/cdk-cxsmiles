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

However, we can also use [pybacting]() and parse the CxSMILES with <a name="tp2">Bacting</a> [<a href="#citeref1">1</a>]
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

## References

1. <a name="citeref1"></a>Willighagen E. Bacting: a next generation, command line version of Bioclipse. JOSS. 2021 Jun 23;6(62):2558.  doi:[10.21105/JOSS.02558](https://doi.org/10.21105/JOSS.02558) ([Scholia](https://scholia.toolforge.org/doi/10.21105/JOSS.02558))


