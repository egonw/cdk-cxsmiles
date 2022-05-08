# Introduction

At the Dagstuhl Computation Metabolomics meeting there was a session about core structures.
The research question here is what the right balance is of representation of multiple
structures, matching measured data. [ChemAxon extended SMILES](https://chemaxon.com/marvin-archive/latest/help/formats/cxsmiles-doc.html),
or <a name="tp1">CxSMILES</a>, came up as one solution [<a href="#citeref1">1</a>,<a href="#citeref2">2</a>].
This repository contains code using the <a name="tp2">Chemistry Development Kit</a> [<a href="#citeref3">3</a>,<a href="#citeref4">4</a>,<a href="#citeref5">5</a>]
for various tasks around this question. The following chapters discuss these.

## CxSMILES in Wikidata

Prior to the Computation Metabolomics 2022 meeting a proposal was made to add a Wikidata
property for CxSMILES which was approved during the meeting. The SPARQL query
[https://w.wiki/58rF](https://w.wiki/58rF) returns a list of Wikidata items with a
CxSMILES value.

## References

1. <a name="citeref1"></a>Alexandrov T, Böcker S, Dorrestein P, Schymanski E. Computational Metabolomics: Identification, Interpretation, Imaging (Dagstuhl Seminar 17491). 2018.  doi:[10.4230/DAGREP.7.12.1](https://doi.org/10.4230/DAGREP.7.12.1) ([Scholia](https://scholia.toolforge.org/doi/10.4230/DAGREP.7.12.1))
2. <a name="citeref2"></a>Ludwig M, Neumann S, Willighagen E. Cheminformatics for Users. In: Computational Metabolomics: From Cheminformatics to Machine Learning (Dagstuhl Seminar 20051). 2020. 
3. <a name="citeref3"></a>Steinbeck C, Han Y, Kuhn S, Horlacher O, Luttmann E, Luttmann E, et al. The Chemistry Development Kit (CDK): an open-source Java library for Chemo- and Bioinformatics. JCICS. 2003 Feb 11;43(2):493–500.  doi:[10.1021/CI025584Y](https://doi.org/10.1021/CI025584Y) ([Scholia](https://scholia.toolforge.org/doi/10.1021/CI025584Y))
4. <a name="citeref4"></a>Steinbeck C, Hoppe C, Hoppe C, Kuhn S, Floris M, Guha R, et al. Recent Developments of the Chemistry Development Kit (CDK) - An Open-Source Java Library for Chemo- and Bioinformatics. Curr Pharm Des [Internet]. 2006 Jun 1;12(17):2111–20. Available from: https://cdk.github.io/cdk-paper-2/ doi:[10.2174/138161206777585274](https://doi.org/10.2174/138161206777585274) ([Scholia](https://scholia.toolforge.org/doi/10.2174/138161206777585274))
5. <a name="citeref5"></a>Willighagen E, Mayfield JW, Alvarsson J, Berg A, Carlsson L, Jeliazkova N, et al. The Chemistry Development Kit (CDK) v2.0: atom typing, depiction, molecular formulas, and substructure searching. J Cheminform. 2017 Jun 6;9(1).  doi:[10.1186/S13321-017-0220-4](https://doi.org/10.1186/S13321-017-0220-4) ([Scholia](https://scholia.toolforge.org/doi/10.1186/S13321-017-0220-4))


