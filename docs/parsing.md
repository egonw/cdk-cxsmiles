# CxSMILES in the CDK

The CDK supports a subset of CxSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussion](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CxSMILES

CxSMILES for lipids can use the `[H]C\C=C\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|` syntax.
We can parse this into a CDK data model with the regular approach. In <a name="tp1">Groovy</a> this
looks like this:

**Script** [code/ParseCXSMILES.groovy](code/ParseCXSMILES.code.md)
```groovy
sp = new SmilesParser(
  SilentChemObjectBuilder.getInstance()
)
mol1 = sp.parseSmiles("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|")
```

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

## The internal graph model


## References

1. <a name="citeref1"></a>Willighagen E. Bacting: a next generation, command line version of Bioclipse. JOSS. 2021 Jun 23;6(62):2558.  doi:[10.21105/JOSS.02558](https://doi.org/10.21105/JOSS.02558) ([Scholia](https://scholia.toolforge.org/doi/10.21105/JOSS.02558))


