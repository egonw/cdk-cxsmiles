# LiebischExamples.groovy
**Source code:**
```groovy
@Grab(group='io.github.egonw.jliebisch', module='liebisch', version='1.0-SNAPSHOT')

 import io.github.egonw.jliebisch.LMAbbrevTool

println LMAbbrevTool.cxsmiles("CE 8:0")
println LMAbbrevTool.cxsmiles("FA 14:1")
println LMAbbrevTool.cxsmiles("LPC 10:1")
```
**Output:**
```plain
C1[C@H](OC(=O)CCCCCCC)CC2=CC[C@@]3([H])[C@]4([H]...
  )CC[C@]([H])([C@]([H])(C)CCCC(C)C)[C@@]4(C)CC[...
  C@]3([H])[C@@]2(C)C1
OC(=O)CC=CC[H] |Sg:n:3:x:ht,Sg:n:6:y:ht| x+y=11
[C@](COP(=O)([O-])OCC[N+](C)(C)C)([H])(O)COC(=O)...
  CC=CC[H] |Sg:n:19:x:ht,Sg:n:22:y:ht| x+y=7
```
