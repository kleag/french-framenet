ASFALDA French FrameNet Annotated Corpus
----------------------------------------
Conll-style format description
----------------------------------------
25/05/2016

The Conll-style format uses plain conll 2006 format for syntactic dependency trees.
The semantic annotations (frames and roles) are annotated as features, hence within the 6th column
(feature names "frame" and "role").

In CoNLL format, the 6th column is either '_' if the token bears features.
Otherwise it is a comma-separated list of <FEATURE_NAME>=<VALUE>
The semantic feature names are 'frame' and 'role'.

Each frame instance has an FRAME_INSTANCE_ID, starting at 1 for each sentence.
A simple example is : frame=2#FR_Statement-manner-noise

The frame feature complies to the following CFG:
<FRAME_FEATURE> .=. frame=<FRAME_INSTANCE>(,<FRAME_INSTANCE>)*
<FRAME_INSTANCE> .=. <FRAME_INSTANCE_ID>#<FRAME_NAME>(#<FLAGS>)?(#<NULLINST>)*
<FRAME_INSTANCE_ID> .=. <integer>
<FRAME_NAME> .=. <string>
<FLAGS> .=. flags=<FLAG>(\+<FLAG>)*
<FLAG> .=. REFTOPARTICIPANT | ARGCLUSTER | HEADGAP | REDUCEDCOMP
<NULLINST> .=. <ROLE_NAME>=<NI>
<NI> .=. ENI | DNI | UNI


If the same token evokes several frame instances
(which might happen in case of argument cluster, or errors in data)
then the frame instances are comma-separated in the 'frame' feature.

Example : frame=2#FR_Statement-manner-noise,3#FR_Statement-manner-noise

The following example contains 3 frame instances, evoked respectively by tokens 13, 16 and 21:

1	Quant	quant	ADV	ADV	mwehead=P+D|sentid=flmf7aa1ep-234|sentrk=3333	13	mod	13	mod
2	au	à	P+D	P+D	component=y|s=def	1	dep_cpd	1	dep_cpd
3	chancelier	chancelier	N	NC	g=m|mwehead=NC|n=s|role=2.3#Speaker#flags=FULLANTECEDENT#synthead=y|s=c	1	obj.p	1	obj.p
4	de	de	P	P	component=y|role=2.3#Speaker	3	dep_cpd	3	dep_cpd
5	l'	le	D	DET	component=y|n=s|role=2.3#Speaker|s=def	3	dep_cpd	3	dep_cpd
6	Echiquier	échiquier	N	NC	component=y|g=m|n=s|role=2.3#Speaker|s=c	3	dep_cpd	3	dep_cpd
7	,	,	PONCT	PONCT	role=2.3#Speaker|s=w	3	ponct	3	ponct
8	M.	monsieur	N	NC	g=m|n=s|role=2.3#Speaker|s=c	3	mod	3	mod
9	Norman	Norman	N	NPP	g=m|n=s|role=2.3#Speaker|s=p	8	mod	8	mod
10	Lamont	Lamont	N	NPP	g=m|n=s|role=2.3#Speaker|s=p	8	mod	8	mod
11	,	,	PONCT	PONCT	s=w	13	ponct	13	ponct
12	il	il	CL	CLS	g=m|n=s|p=3|role=2.2#Speaker#flags=ANAPH#synthead=y|s=suj	13	suj	13	suj
13	admet	admettre	V	V	frame=2#FR_Statement-manner-noise|m=ind|n=s|p=3|t=pst	0	root	0	root
14	que	que	C	CS	s=s	13	obj	13	obj
15	la	le	D	DET	g=f|n=s|role=2.1#Message|s=def	16	det	16	det
16	reprise	reprise	N	NC	frame=1#Other_sense|g=f|n=s|role=2.1#Message|s=c	17	suj	17	suj
17	sera	être	V	V	m=ind|n=s|p=3|role=2.1#Message#synthead=y|t=fut	14	obj.cpl	14	obj.cpl
18	plus	plus	ADV	ADV	role=2.1#Message	19	mod	19	mod
19	longue	long	A	ADJ	g=f|n=s|role=2.1#Message|s=qual	17	ats	17	ats
20	que	que	C	CS	role=2.1#Message|s=s	19	dep	19	dep
21	prévu	prévoir	V	VPP	frame=3#FR_Expectation#Phenomenon=ENI#Cognizer=UNI|g=m|m=part|n=s|role=2.1#Message|t=past	20	obj.cpl	20	obj.cpl
22	à	à	P	P	role=2.1#Message	19	mod	19	mod
23	se	le/lui	CL	CLR	g=f|n=s|p=3|role=2.1#Message|s=refl	24	aff	24	aff
24	manifester	manifester	V	VINF	m=inf|role=2.1#Message|seclass=demsuj|sesubclass=neutre	22	obj.p	22	obj.p
25	.	.	PONCT	PONCT	s=s	13	ponct	13	ponct


MULTI-WORD FRAME EVOKING ELEMENTS
---------------------------------

The lexical item which evokes a frame can be a multi-word expression.
In that case, the tokens composing the multi-word expression bear a frame feature with same FRAME_INSTANCE_ID.

Syntactic representation of multi-word expressions: 
the tokens forming a multi-word expression have the first token as head, and the subsequent tokens
depend on the first one with a special 'dep_cpd' dependency.
The lemma and part-of-speech of the multi-word expression is provided as mwelemma and mwehead features on the first token.

Example : in the following example, the "en raison d'" evokes the Evidence frame
...
24	en	en	P	P	mwehead=P|mwelemma=en_raison_de|frame=1#Evidence	8	mod	_	_
25	raison	raison	N	NC	component=y|frame=1#Evidence|g=f|n=s|s=c	24	dep_cpd	_	_
26	d'	de	P	P	component=y|frame=1#Evidence	24	dep_cpd	_	_
27	une	un	D	DET	g=f|n=s|role=1.1#Support|s=ind	28	det	_	_
28	expérience	expérience	N	NC	g=f|n=s|role=1.1#Support#synthead=y|s=c	24	obj.p	_	_
29	clinique	clinique	A	ADJ	n=s|role=1.1#Support|s=qual	28	mod	_	_
30	limitée	limité	A	ADJ	g=f|n=s|role=1.1#Support#semhead=y|s=qual	28	mod	_	_
31	dans	dans	P	P	role=1.1#Support	28	dep	_	_
32	cette	ce	D	DET	g=f|n=s|role=1.1#Support|s=dem	33	det	_	_
33	population	population	N	NC	g=f|n=s|role=1.1#Support|s=c	31	obj.p	_	_
34	.	.	PONCT	PONCT	s=s	8	ponct	_	_


ROLE FILLERS
------------

Each role filler of a frame instance has a ROLE_FILLER_ID.
Each token of the role filler bears a "role" feature, 
which complies to the following CFG:

<ROLE_FEATURE> .=. role=<ROLE_INSTANCE>(,<ROLE_INSTANCE>)*
<ROLE_INSTANCE> .=. <FRAME_INSTANCE_ID>.<ROLE_FILLER_ID>#<ROLE_NAME>(<FLAGS>)?(<HEADS>)?
<FLAGS> .=. flags=<FLAG>(\+<FLAG>)*
<FLAG> .=. NLI | ANAPH | FULLANTECEDENT
<HEADS> .=. (synthead|semhead)=y

Example : role=2.3#Speaker

The role filler can have flags, which appear on the first token of the role filler:

Example : role=4.1#Support#flags=NLI+ANAPH

SYNTACTIC HEAD OF A ROLE FILLER
-------------------------------
One token of the role filler is marked as the syntactic head, using 'synthead=y'.
Example : role=3.2#Message#synthead=y

When the role filler forms a single subtree according to the gold dependency tree,
its syntactic head is the root of the subtree.

When the role filler is made of several subtrees, 
a priority order over the parts of speech of the subtrees' roots 
are used to choose a single syntactic head. 
The order is: verb, adjective, noun, adverb, pronoun
(leftmost root is chosen in case of same category, and in case of category outside this list).


SEMANTIC HEAD OF A ROLE FILLER
------------------------------
By default, the semantic head of a role filler is supposed to be its syntactic head.
For certain role fillers, annotators have marked that the semantic head is different from the syntactic head.
In these cases one token bears a 'semhead=y' mark.

Example :
In the following example the "Evidence" frame is evoked by "en raison d'" (multi word expression, tokens 24 to 25).
The Support role is filled by tokens 25 to 31. While the syntactic head is at token 26, the semantic head is at token 28.

Example : in the following example, the "en raison d'" evokes the Evidence frame
...
24	en	en	P	P	mwehead=P|mwelemma=en_raison_de|frame=1#Evidence	8	mod	_	_
25	raison	raison	N	NC	component=y|frame=1#Evidence|g=f|n=s|s=c	24	dep_cpd	_	_
26	d'	de	P	P	component=y|frame=1#Evidence	24	dep_cpd	_	_
27	une	un	D	DET	g=f|n=s|role=1.1#Support|s=ind	28	det	_	_
28	expérience	expérience	N	NC	g=f|n=s|role=1.1#Support#synthead=y|s=c	24	obj.p	_	_
29	clinique	clinique	A	ADJ	n=s|role=1.1#Support|s=qual	28	mod	_	_
30	limitée	limité	A	ADJ	g=f|n=s|role=1.1#Support#semhead=y|s=qual	28	mod	_	_
31	dans	dans	P	P	role=1.1#Support	28	dep	_	_
32	cette	ce	D	DET	g=f|n=s|role=1.1#Support|s=dem	33	det	_	_
33	population	population	N	NC	g=f|n=s|role=1.1#Support|s=c	31	obj.p	_	_
34	.	.	PONCT	PONCT	s=s	8	ponct	_	_



DISCONTINUOUS ROLE FILLERS
--------------------------
Role fillers can be discontinuous: the sequence of tokens with same FRAME_INSTANCE_ID 
and ROLE_FILLER_ID form a single role filler, whether continuous or not.

CONTENT ROLE FILLERS
--------------------
The void prepositions and complementizers were not included in role fillers.
This pertains to coordinated role fillers also, leading to additional discontinuities.

For example in "Judith parle à Pierre et à Anna" (Judith talks to Pierre and to Anna)
the Addressee role filler is "Pierre" + "et" + "Anna",
leaving aside the two prepositions "à".

ANAPHORIC ROLE FILLERS
----------------------
When an anaphoric role filler has its antecedent within the same sentence, 
then the same role is filled by two distinct role fillers (with same role name, but distinct ROLE_FILLER_IDs), 
one with an ANAPH flag and the other with the FULLANTECEDENT flag.
When the antecedent is not in the same sentence, the anaphoric role filler does not bear any ANAPH flag.

Example: In the example below the Speaker role of the FR_Statement-manner-noise frame
is filled by "il" (token 12), which is anaphoric, and whose antecedent is "chancelier de l'Echiquier" (tokens 3 to 6).
These two role fillers fill the same Speaker role, but with 2 different IDs (2.2 and 2.3).

1	Quant	quant	ADV	ADV	mwehead=P+D|sentid=flmf7aa1ep-234|sentrk=3333	13	mod	13	mod
2	au	à	P+D	P+D	component=y|s=def	1	dep_cpd	1	dep_cpd
3	chancelier	chancelier	N	NC	g=m|mwehead=NC|n=s|role=2.3#Speaker#flags=FULLANTECEDENT#synthead=y|s=c	1	obj.p	1	obj.p
4	de	de	P	P	component=y|role=2.3#Speaker	3	dep_cpd	3	dep_cpd
5	l'	le	D	DET	component=y|n=s|role=2.3#Speaker|s=def	3	dep_cpd	3	dep_cpd
6	Echiquier	échiquier	N	NC	component=y|g=m|n=s|role=2.3#Speaker|s=c	3	dep_cpd	3	dep_cpd
7	,	,	PONCT	PONCT	role=2.3#Speaker|s=w	3	ponct	3	ponct
8	M.	monsieur	N	NC	g=m|n=s|role=2.3#Speaker|s=c	3	mod	3	mod
9	Norman	Norman	N	NPP	g=m|n=s|role=2.3#Speaker|s=p	8	mod	8	mod
10	Lamont	Lamont	N	NPP	g=m|n=s|role=2.3#Speaker|s=p	8	mod	8	mod
11	,	,	PONCT	PONCT	s=w	13	ponct	13	ponct
12	il	il	CL	CLS	g=m|n=s|p=3|role=2.2#Speaker#flags=ANAPH#synthead=y|s=suj	13	suj	13	suj
13	admet	admettre	V	V	frame=2#FR_Statement-manner-noise|m=ind|n=s|p=3|t=pst	0	root	0	root
14	que	que	C	CS	s=s	13	obj	13	obj
...


