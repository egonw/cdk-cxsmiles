# CDK CxSMILES

**Egon L. Willighagen, Adriano Rutz**

© 2020-2022 The Authors

License: CC-BY 4.0 International

## Origin

At the Dagstuhl Computation Metabolomics meeting in
<a href="https://www.dagstuhl.de/en/program/calendar/semhp/?semnr=20051">2020</a> [<a href="#citeref1">1</a>] and
<a href="https://www.dagstuhl.de/en/program/calendar/semhp/?semnr=22181">2022</a>
there were sessions about core structures, structure identity certainty, and identification.

## Acknowledgments

We thank everyone who contributed to the discussions at the two Computation Metabolomics meetings.
In 2020 this was Marcus Ludwig, Steffen Neumann, Michael Witting, Marcus Ludwig, Corey Broeckling,
Laurent Gatto, Xiuxia Du, Alexis Delabriere, Jan Lisec, and Andrea Brunner, and in 2022 this was
Soha Hassoun, Roman Bushuiev, Louis-Felix Nothias, Sebastian Böcker, Justin van der Hooft, and
Adriano Rutz. Also thanks to Emma Schymanski, John Mayfield, and Carolin Huber for online replies.

## Contents

1. [Introduction](intro.md) <br />
1.1. [CxSMILES in Wikidata](intro.md#cxsmiles-in-wikidata) <br />
2. [CxSMILES in the CDK](parsing.md) <br />
2.1. [Parsing CxSMILES](parsing.md#parsing-cxsmiles) <br />
2.1.1. [Groovy](parsing.md#groovy) <br />
2.1.2. [Python](parsing.md#python) <br />
2.1.3. [CDKDepict](parsing.md#cdkdepict) <br />
2.2. [The internal graph model](parsing.md#the-internal-graph-model) <br />
3. [Classes of compounds and where to find a CxSMILES](templates.md) <br />
3.1. [Lipids](templates.md#lipids) <br />
3.1.1. [Lipids with a double bond somewhere in the tail](templates.md#lipids-with-a-double-bond-somewhere-in-the-tail) <br />
3.1.2. [Lipids with two double bonds somewhere in the tail](templates.md#lipids-with-two-double-bonds-somewhere-in-the-tail) <br />
3.1.3. [Lipids with two tails](templates.md#lipids-with-two-tails) <br />
3.2. [Positional uncertainty](templates.md#positional-uncertainty) <br />
3.2.1. [Flavonoid](templates.md#flavonoid) <br />
3.3. [Polymers](templates.md#polymers) <br />
4. [Creating CxSMILES](chapter2.md) <br />
4.1. [Step 1: the core structure](chapter2.md#step-1:-the-core-structure) <br />
4.2. [Step 2: the side chains](chapter2.md#step-2:-the-side-chains) <br />
4.3. [Step 3: the attachment points](chapter2.md#step-3:-the-attachment-points) <br />
5. [Depiction of CxSMILES](depict.md) <br />
5.1. [Groovy code](depict.md#groovy-code) <br />
6. [Enumerating chemical structures for a CxSMILES](enumeration.md) <br />
6.1. [Filtering by molecular formula](enumeration.md#filtering-by-molecular-formula) <br />

[Index](indexList.md) <br />

## References

1. <a name="citeref1"></a>Ludwig M, Neumann S, Willighagen E. Cheminformatics for Users. In: Computational Metabolomics: From Cheminformatics to Machine Learning (Dagstuhl Seminar 20051). 2020. 

