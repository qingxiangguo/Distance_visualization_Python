**Pairwise distance visualization in Python**

**Contributors**

Qingxiang Guo

**About**

The following contents contains source code for the analyses and plots in Parasites & Vectors paper, 2018, “Morphological plasticity in *Myxobolus* Bütschli, 1882: a taxonomic dilemma case and renaming of a parasite species of the common carp”

**Abstract**

Myxozoans are a group of cnidarian parasites, the present taxonomy of which favors a more comprehensive characterization strategy combining spore morphology, biological traits (host/organ specificity, tissue tropism), and DNA data over the classical morphology-based taxonomy. However, a systematist might again run into a taxonomic dilemma if more than two of the following exceptional cases were encountered at the same time: extensive intraspecific polymorphism, interspecific morphological similarity, identical interspecific biological traits and blurred small-subunit (SSU) rDNA-based species boundaries. In the present study, spores of a species of *Myxobolus* Bütschli, 1882 with two morphotypes (wide type and narrow type) were collected from the gills of common carp *Cyprinus carpio* Linnaeus. Confusingly, the wide type was found to be identical to *Myxobolus paratoyamai* Kato, Kasai, Tomochi, Li & Sato, 2017 in spore morphology and SSU rDNA sequence, which confidently suggested their conspecificity; while the narrow type, was highly similar to *Myxobolus toyamai* Kudo, 1917 based on spore morphology and SSU rDNA sequence and thus could not be easily classified. This discordance between wide type and narrow type has caused a taxonomic dilemma. To address this problem, a hypothesis about the conspecificity of the narrow type and *M. toyamai* was addressed.

**Notes**

Written by Qingxiang Guo, qingxiang.guo@outlook.com, distributed without any guarantees or restrictions.

**Codes**

**1. Pairwise distance visualization in Python**

import networkx as nx

import numpy as np

import string

dt = [('len', float)]

A = np.array([(0, 0.004, 0.013, 0.034, 0.033, 0.033, 0.01),

`               `(0.004, 0, 0.016, 0.038, 0.036, 0.036, 0.014),

`               `(0.013, 0.016, 0, 0, 0.04, 0.04, 0.02),

`               `(0.034, 0.038, 0.041, 0, 0.001, 0.001, 0.031),

`               `(0.033, 0.036, 0.04, 0.001, 0, 0, 0.03),

`               `(0.033, 0.036, 0.04, 0.001, 0, 0, 0.03),

`               `(0.01, 0.014, 0.02, 0.031, 0.03, 0.03, 0)

`               `])\*100

A = A.view(dt)

G = nx.from\_numpy\_matrix(A)

G = nx.relabel\_nodes(G, dict(zip(range(len(G.nodes())),string.ascii\_uppercase)))

G = nx.drawing.nx\_agraph.to\_agraph(G)

G.node\_attr.update(color="red", width="0.1",height="0.1",  shape="circle")

G.edge\_attr.update(color="blue", width="1.0")

G.draw('/tmp/out.pdf', format='pdf', prog='neato')

**Please cite this paper as**

Guo, Q., Huang, M., Liu, Y., Zhang, X., & Gu, Z. (2018). Morphological plasticity in Myxobolus Bütschli, 1882: a taxonomic dilemma case and renaming of a parasite species of the common carp. Parasites & vectors, 11(1), 1-11. 

**License**

All source code, i.e. scripts/\*.pl, scripts/\*.sh or scripts/\*.py are under the MIT license.
