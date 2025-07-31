# CxSMILES in the CDK

The CDK supports a subset of CxSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussion](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CxSMILES

CxSMILES for lipids can use the `[H]C\C=C\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|` syntax.
We can parse this into a CDK data model with the regular approach.

### Groovy

In <topic>Groovy</topic> this
looks like this:

<code>ParseCXSMILES</code>

### Python

However, we can also use [pybacting](https://pypi.org/project/pybacting/) and parse the CxSMILES with <topic>Bacting</topic> [<cite>Q107332190</cite>]
(which uses the CDK in turn) in <topic>Python</topic>:

```python
from pybacting import cdk
from scyjava import to_python as j2p
import IPython

cxmol = cdk.fromSMILES("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
svg = j2p(cdk.asSVG(cxmol))
display(IPython.display.SVG(svg))
```

We can even open this as a <topic>Jupyter Notebook</topic> in
[Google Colab](https://colab.research.google.com/github/egonw/cdk-cxsmiles/blob/master/nb/parseCxSMILES.ipynb).

There are more examples available from [this notebook](https://github.com/egonw/cdk-cxsmiles/blob/master/nb/lipid_cxsmiles_scyjava_cdk.ipynb)
by Zhixu Ni, which can also be opened in [Google Colab](https://colab.research.google.com/github/egonw/cdk-cxsmiles/blob/master/nb/lipid_cxsmiles_scyjava_cdk.ipynb).

### CDKDepict

Finally, the online [CDKDepict](https://www.simolecule.com/cdkdepict/depict.html) can parse and process CxSMILES strings for
you without any coding.

## The internal graph model

After the CxSMILES is parsed by the CDK, it is stored in memory is an <topic>IAtomContainer</topic>.
This IAtomContainer is the CDK data model for bonded atoms. Most commonly it is used to store the
chemical graph in which atoms are represented as vertices and bonds as edges. 

We can list the atoms and bonds with this code:

<code>DataModel</code>

which lists:

<out>DataModel</out>

The other details are stored as properties on the atom container referring to the atoms
and bonds they apply to. As such, it can be seen as coloring the graph:

<code>SGroups</code>

which lists:

<out>SGroups</out>

## Writing as an SD file

We can also write a CXSMILES to a SD file. We can use the following code for this:

<code>WriteSDF</code>

The output uses the `*` as pseudoatom as in the input SMILES and exports the
CXSMILES aspects as additional annotation after the mol block:

<in type="verbatim">code/polybisacarb.sdf</in>

## References

<references/>

