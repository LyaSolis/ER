# ER
Entity Relationship

Data - WebAnno
--------------------------------------
Sentence Representation

If a sentence spans multiple lines, the text is split at the line feed characters (ASCII 12) and multiple
#Text= lines are generated. Note that carriage return characters (ASCII 13) are kept as escaped
characters (\r).
Example: Original multi-line text:

#Text=Bell , based in Los Angeles , makes and distributes
#Text=electronic , computer and building products .

-------------------------------------
Token and Sub-token Annotations

Tokens represent a span of text within a sentence. Tokens cannot overlap, although then can be
directly adjacent (i.e. without any whitespace between them). 
The start offset of the first character of the first token corresponds to the start of offset of the sentence.
Token annotation starts with a sentence-token number marker followed by the begin-end offsets and the token itself, separated by a TAB characters.

Example: Token position

1-2 4-8 Haag

Here 1 indicates the sentence number, 2 indicates the token number (here, the second token in the
first sentence) and 4 is the begin offset of the token and 8 is the end offset of the token while Haag is
the token.

Sub-token representations are affixed with a . and a number starts from 1 to N.
Example: Sub-token positions
1-3 9-14 plays
1-3.1 9-13 play
1-3.2 13-14 s
Here, the sub-token play is indicated by sentence-token number 1-3.1 and the sub-token s is
indicated by 1-3.2.

-------------------------------------
Chain Annotations
In the Chain annotation, two columns (TAB separated) are used to represent the referenceType and the referenceRelation. 

A chain ID is attached to the referenceType to distinguish to which of the chains the annotation belongs. 

The referenceRelation of the chain is represented as:

the relation value → the CH-LINK number 
(where CH=chain number - LINK=link number (the order the chain))

Example: Chain layer declaration in file header
#T_CH=de.tudarmstadt.ukp.dkpro.core.api.coref.type.CoreferenceLink|referenceType|referenceRelation

Example: Chain annotations
1-1 0-2   He        pr[1] coref->1-1
1-2 3-7   shot      _ _
1-3 8-15  himself   pr[1] coref->1-2
1-4 16-20 with      _ _
1-5 21-24 his       pr[1] *->1-3
1-6 25-33 revolver  _ _
1-7 33-34 .         _ _
In this example, token 1-3 is marked as pr[1] which indicates that the referenceType is pr and it is
part of the chain with the ID 1. The relation label is coref and with the CH-LINK number 1-2 which
means that it belongs to chain 1 and this is the second link in the chain.



sentence-token_number | begin-end_offsets | token | referenceRelation(relation label) | referenceType 

In this example, token 11-7 is marked as demography[4] which indicates that the referenceType is demography and it is
part of the chain with the ID 4. The relation label (*->4-1) is * and with the CH-LINK number 4-1 which
means that it belongs to chain 4 and this is the first link in the chain.

11-1	1431-1432	A	            *[12]	*[12]	_	_	
11-2	1433-1438	total	        *[12]	*[12]	_	_	
11-3	1439-1441	of	          *[12]	*[12]	_	_	
11-4	1442-1445	269	          *[12]	*[12]	_	_	
11-5	1446-1454	patients	    *[12]	*[12]	_	_	
11-6	1455-1459	aged	        *[12]	*[12]	_	_	
11-7	1460-1461	≥	            *[12]	*[12]	*->4-1	demography[4]	
11-8	1461-1463	65	          *[12]	*[12]	*->4-1	demography[4]	
11-9	1464-1469	years	        *[12]	*[12]	*->4-1	demography[4]	
11-10	1470-1474	with	        *[12]	*[12]	_	_	
11-11	1475-1485	previously	  *[12]	*[12]	_	_	
11-12	1486-1495	untreated	    *[12]	*[12]	_	_	
11-13	1496-1503	chronic	      *[12]	*[12]	_	_	
11-14	1504-1515	lymphocytic	  *[12]	*[12]	_	_	
11-15	1516-1524	leukemia	    *[12]	*[12]	_	_	
11-16	1525-1529	with	        *[12]	*[12]	_	_	
11-17	1529-1530	-	            *[12]	*[12]	_	_	
11-18	1531-1534	out	          *[12]	*[12]	_	_	
11-19	1535-1538	del	          *[12]	*[12]	*->44-1	mutation[44]	
11-20	1538-1539	(	            *[12]	*[12]	*->44-1	mutation[44]	
11-21	1539-1542	17p	          *[12]	*[12]	*->44-1	mutation[44]	
11-22	1542-1543	)	            *[12]	*[12]	*->44-1	mutation[44]	
11-23	1544-1548	were	        *[12]	*[12]	_	_	
11-24	1549-1559	randomized	  *[12]	*[12]	_	_	
11-25	1560-1561	1	            *[12]	*[12]	_	_	
11-26	1561-1562	:	            *[12]	*[12]	_	_	
11-27	1562-1563	1	            *[12]	*[12]	_	_	
11-28	1564-1566	to	          *[12]	*[12]	_	_	
11-29	1567-1576	ibrutinib	    *[12]	*[12]	*->43-1	therapy\_group[43]	
11-30	1577-1578	(	            *[12]	*[12]	_	_	
11-31	1578-1579	n	            *[12]	*[12]	_	_	
11-32	1579-1580	=	            *[12]	*[12]	_	_	
11-33	1580-1583	136	          *[12]	*[12]	_	_	
11-34	1583-1584	)	            *[12]	*[12]	_	_	
11-35	1585-1587	or	          *[12]	*[12]	_	_	
11-36	1588-1600	chlorambucil	*[12]	*[12]	*->22-1	therapy\_group[22]	

