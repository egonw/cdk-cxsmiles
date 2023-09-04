# Liebisch abbreviations

The Liebisch abbrevations are a shorthand notation for lipid structures. This is particularly useful
when the lipid is incompletely characterized [<a href="#citeref1">1</a>,<a href="#citeref2">2</a>].

For example, we can use the following code to depict `CE 16:1`, using CXSMILES as intermediate step:

**Script** [code/DepictLipidAbbrev.groovy](code/DepictLipidAbbrev.code.md)
```groovy
cxsmiles = LMAbbrevTool.cxsmiles("CE 16:1")
mol1 = sp.parseSmiles(cxsmiles)
new DepictionGenerator()
  .depict(mol1)
  .writeTo("CE_16:1.svg");
```

The output looks like this:

<img src="./images/generated/CE_16:1.svg" width="400" alt="Depiction of the 2D structure of CE 16:1" />

## References

1. <a name="citeref1"></a>Liebisch G, Vizcaíno JA, Köfeler H, Trötzmüller M, Griffiths WJ, Schmitz G, et al. Shorthand notation for lipid structures derived from mass spectrometry. J Lipid Res. 2013 Apr 2;54(6):1523–30.  doi:[10.1194/JLR.M033506](https://doi.org/10.1194/JLR.M033506) ([Scholia](https://scholia.toolforge.org/doi/10.1194/JLR.M033506))
2. <a name="citeref2"></a>Liebisch G, Fahy E, Aoki J, Dennis EA, Durand T, Ejsing C, et al. Update on LIPID MAPS Classification, Nomenclature and Shorthand Notation for MS-derived Lipid Structures. J Lipid Res. 2020 Oct 9;  doi:[10.1194/JLR.S120001025](https://doi.org/10.1194/JLR.S120001025) ([Scholia](https://scholia.toolforge.org/doi/10.1194/JLR.S120001025))


