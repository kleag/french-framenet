ASFALDA French FrameNet Annotated Corpus
----------------------------------------
release 1.2 march 2017
----------------------------------------

The release contains FrameNet annotations for French.
Frames and roles have been annotated on two syntactic treebanks:

- the Sequoia Treebank (Candito and Seddah, 2012)
- the French Treebank (Abeillé et al., 2003)

concatenated in that order.

The corpus is released as a conll-style format,
containing frame and roles annotations, 
on top of pre-existing morpho-syntactic annotations.

See README_conll_format.txt for the description of the conll-style format.

contact:marie.candito@gmail.com

------------------------------
REFERENCE
------------------------------

For reference if you use the data, and for more details on the annotations, see:

Djemaa Marianne, Candito Marie, Muller Philippe and Vieu Laure. 2016. Corpus annotation within the French FrameNet: a domain-by-domain methodology. In Proceedings of LREC 2016. Portoroz, Slovenia, may 2016.

--------------------------------------------------
NOTE FOR USING THE DATA FOR FRAME-SEMANTIC PARSING
--------------------------------------------------

The provided annotations are not full-text annotations:
some predicate occurrences are not covered by the lexicon,
and thus bear no annotations.
Further, for the lemmas present in the lexicon, the number of occurrences
proposed for annotation was limited to 100.

This entails that the absence of frame annotation on a lemma does not necessarily mean it would not evoke a frame if it had been annotated.

Moreover, the French frames cover 4 notional domains (commercial transactions, cognitive stances, causality and verbal communication). A lemma occurrence proposed for annotation was either
- associated to a frame within these 4 domains
- or associated to a special "dummy" frame called Other_sense

So any work using the data as training data should be restricted to lemma occurrences bearing a frame annotation, this being either a frame pertaining to the 4 domains, or the Other_sense frame.

------------------------------
MACRO ROLES
------------------------------

The frame-specific roles have been clustered into a hierarchy of macro-roles.

The macroroles.xml files provides the hierarchy of macro-roles.
Each macro-role contains macro-roles (submacrorole tags)
and/or frame-specific roles (subrole_main tags).

A given frame-specific role may belong to other macro-roles on top of the main one,
leading to subrole_secondary tags.


-----------------------------------
USUAL SPLIT
-----------------------------------
For machine learning experiments, the usual split when using the FTB and Sequoia corpus is provided in 
the split-sequoiaftb directory: training, dev and test sets are provided, as lists of sentence identifiers.

----------------------------------------
VERSION HISTORY
----------------------------------------

- 1.1: December 2016
- 1.2: March 2017
  ** minor modifications of roles in FR_Getting_money, FR_Judgment_communication (to better follow rules for defining roles)
  ** enhanced computation of role fillers' syntactic heads
- 1.3: November 2017
  ** erroneous remaining "extra-thematic" roles removed or recategorized as "peripheral" (only one non-core role type: for non mandatory subcategorized role)
  ** Support role of FR_Proving actually removed in annotations
