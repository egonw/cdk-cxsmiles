# CxSMILES in the CDK

The CDK supports a subset of CxSMILES only and this chapter should give an overview
over how far the support goes. Also refer to 
[this discussion](https://github.com/cdk/depict/issues/7)
between Emma Schymanski and John Mayfield.

## Parsing CxSMILES

CxSMILES for lipids can use the `[H]C\C=C\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht|` syntax.
We can parse this into a CDK data model with the regular approach. In Groovy this
looks like this:

<code>ParseCXSMILES</code>

However, we can also use [pybacting]() and parse the CxSMILES with Bacting
(which uses the CDK in turn) in Python:

```python
from pybacting import cdk
from scyjava import to_python as j2p
import IPython

cxmol = cdk.fromSMILES("[H]C\\C=C\\CC(=O)O |Sg:n:1:x:ht,Sg:n:4:y:ht| x+y=17")
svg = j2p(cdk.asSVG(cxmol))
display(IPython.display.SVG(svg))
```

We can even open this as a Jupyter Notebook in
[Google Colab]([Open in Google Colab](https://colab.research.google.com/github/egonw/cdk-cxsmiles/blob/master/nb/parseCxSMILES.ipynb)).

## The internal graph model


## References

<references/>

