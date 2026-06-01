---
title:  "Collaborative Knowledge Graphs"
date:   2026-05-30
categories: ["Blog"]
toc: true
---

<!-- Main goal: establish a typology of CKGs, show existing success, their promise and untapped potential -->

Structuring information through knowledge graphs (KGs) offers many advantages on the web. <!-- maybe make it more punchy and broader -->

Graphs are most suitable to encode and represent interconnections between nodes, i.e. things. Knowledge graphs add a semantic layer, whereby nodes become typed entities linked through typed relations or statements, each type with its properties. This combined relational and semantic structure is particularly well suited for information tracing and statement verification. It can foster not only trust, but also interoperability between different KG databases, using shared standards or following the linked data framework/paradigm.

In a web whose traffic is to be dominated and mediated by bots, in which information is to be mediated largely through search engines and LLMs, structuring data becomes even more important and valuable. As LLM training—and to some extent, inference—break the link between original information sources and output statements, human-curated KGs provide deterministically verifiable, queriable and answerable knowledge. 
<!-- linked sources of information and statements that facilitate verifiability throughout the retrieval chain.   -->
properties: queriable, answerable
+ Use of structured data during pre-training (https://arxiv.org/abs/2002.08909), training or at inference time (GraphRAG https://arxiv.org/abs/2005.11401) help reduce hallucination [^pan]

Here is a review of different examples of collaborative KGs (CKGs), distinguishing different types of collaboration. 
The aim is to broadly cover the panorama of CKGs, but certainly not of all open KG databases.
The potential of CKGs has only partially been tapped, and suggest some frontier applications for them.

## KG examples

We'll be using these main examples throughout:
- [Wikidata](https://www.wikidata.org/)[^vrandecic] for encyclopedic knowledge, the most studied example of CKG,
- [Wikibase ecosystem](https://wikibase-metadata.wmcloud.org/)[^diefenbach], a interoperable pool of KGs, some of which CKGs
- [DBpedia](https://www.dbpedia.org/)[^lehmann],
- [ORKG](https://orkg.org/)[^auer][^jaradeh] for scholarly knowledge,
- [schema.org](https://schema.org/)[^guha]

 If you think there are some important CKGs missing from this review, I'd be very grateful for any suggestions.

## A typology of collaboration in KG curation

A CKG is a KG that is collaboratively curated by a group of people.
Collaboration can happen at different levels, namely data entry, ontology or algorithmic curation.



<!-- This collaboration can happen at different levels:
- editing the graph data, or crowdsourced KGs
- editing the KG schema, or collaborative ontologies
- editing algorithms used to construct or curate the KG, or collective algorithmic KG control
- editing external data that is used to construct the KG 
- editing the rules and permissions, or collective KG governance -->

<!-- These are not hard categories, but rather different axes to understand collaboration. -->

### Collaborative data entry

A first way to collaborate on knowledge graphs is to let a group of humans create and edit the data itself.
The resulting KGs can thus be called crowdourced KGs.

Wikidata allows anyone —logged in or not— to edit the KG by creating or editing items and statements. Editors are encouraged to associate references to justify each property. 

Beyond Wikidata, there are thousands of 'Wikibases', i.e. other projects based on the Wikibase software. These projects are generally managed by different communities, with their own rules and objectives. Among prominent Wikibaseswith collaborative data entry, we find: 


ORKG invites contributions from logged-in users to add or edit various elements of the KG: comparisons, reviews, lists, papers, benchmarks, etc... 

### Collective ontologies

<!-- In Wikidata, properties are items too, whose ID start with a "P", not a "Q" as for entities. -->
Wikidata's ontology is itself collaboratively maintained. While anyone can create classes (items, with Q-IDs), proposing properties (with P-IDs) require community discussion and consensus.
This process helps keep the ontology consistent, but can also slow schema evolution and requires active community moderation.
<!-- Properties may have constraint statements and example usage on their pages. -->
- https://www.wikidata.org/wiki/Wikidata:WikiProject_Ontology
- https://www.wikidata.org/wiki/Help:Property_constraints_portal


<!-- Wikibase software lets its admins decide upon how it should be managed, and thus -->
Several wikibase KGs feature collaborative ontology management: FactGrid (?), Wikibase World (?)... 
Details about how these work..
The different schemas/ontologies may be different, but can also be designed so as to interconnect with other Wikibase projects.
However, harder to interoperate with other KGs which do not follow the Wikibase data model[^dobriy][^shimizu]


Some projects are focused solely on collaborative design of KG ontologies and schemas, with the aim of promoting interoperability among KGs:
- https://schema.org/ (https://schema.org/docs/howwework.html)
- https://obofoundry.org/


DBpedia
- https://mappings.dbpedia.org/index.php/How_to_edit_the_DBpedia_Ontology



### Algorithmic Collaboration

Collective management of algorithms, bots, tools, which curate the KG data.

Bots approval on Wikidata: https://www.wikidata.org/wiki/Wikidata:Bots

DBpedia

LLM-assisted KG construction



<!-- ### Other forms of collaborative governance -->
<!-- optional section -->
<!-- Platform design, rules, permissions that drive the collaborative curation of KGs. -->


### Discussion

<!-- Nuances of governance. -->
<!-- Collaboration/Power asymmetry -->
Though we outlined three different axes of collaboration, every project has its own community and governance structure.
Though involving community processes, ontology and algorithmic curation is often reserved to a small groups of skilled developers, in some cases with strong ties with major big tech companies (e.g., schema.org).


Possible terms to relate: From Peer-production to big-tech control...




### See also

Resources on KGs: ...



### References

[^gianluca]: Demartini, Gianluca. ‘Implicit Bias in Crowdsourced Knowledge Graphs’. Companion Proceedings of The 2019 World Wide Web Conference (New York, NY, USA), WWW ’19, 13 May 2019, 624–30. https://doi.org/10.1145/3308560.3317307.
[^piscopo1]: Piscopo, Alessandro, Chris Phethean, and Elena Simperl. ‘What Makes a Good Collaborative Knowledge Graph: Group Composition and Quality in Wikidata’. In Social Informatics, edited by Giovanni Luca Ciampaglia, Afra Mashhadi, and Taha Yasseri. Springer International Publishing, 2017. https://doi.org/10.1007/978-3-319-67217-5_19.
[^piscopo2]: Piscopo, Alessandro, and Elena Simperl. ‘Who Models the World? Collaborative Ontology Creation and User Roles in Wikidata’. Proc. ACM Hum.-Comput. Interact. 2, no. CSCW (2018): 141:1-141:18. https://doi.org/10.1145/3274410.
[^piscopo3]: Koutsiana, Elisavet, Gabriel Maia Rocha Amaral, Neal Reeves, Albert Meroño-Peñuela, and Elena Simperl. ‘An Analysis of Discussions in Collaborative Knowledge Engineering through the Lens of Wikidata’. Journal of Web Semantics 78 (October 2023): 100799. https://doi.org/10.1016/j.websem.2023.100799.

[^vrandecic]: Vrandečić, Denny, and Markus Krötzsch. ‘Wikidata: A Free Collaborative Knowledgebase’. Commun. ACM 57, no. 10 (2014): 78–85. https://doi.org/10.1145/2629489.

[^farber]: Färber, Michael, Basil Ell, Carsten Menne, and Achim Rettinger. A Comparative Survey of DBpedia, Freebase, OpenCyc, Wikidata, and YAGO. n.d.

[^pan]: Pan, Shirui, Linhao Luo, Yufei Wang, Chen Chen, Jiapu Wang, and Xindong Wu. ‘Unifying Large Language Models and Knowledge Graphs: A Roadmap’. IEEE Transactions on Knowledge and Data Engineering 36, no. 7 (2024): 3580–99. https://doi.org/10.1109/TKDE.2024.3352100.
[^guha]: Guha, R. V., Dan Brickley, and Steve Macbeth. ‘Schema.Org: Evolution of Structured Data on the Web’. Communications of the ACM 59, no. 2 (2016): 44–51. https://doi.org/10.1145/2844544.

[^jaradeh]: Jaradeh, Mohamad Yaser, Allard Oelen, Kheir Eddine Farfar, et al. ‘Open Research Knowledge Graph: Next Generation Infrastructure for Semantic Scholarly Knowledge’. Proceedings of the 10th International Conference on Knowledge Capture (New York, NY, USA), K-CAP ’19, 23 September 2019, 243–46. https://doi.org/10.1145/3360901.3364435.

[^lehmann]: Lehmann, Jens, Robert Isele, Max Jakob, et al. ‘DBpedia – A Large-Scale, Multilingual Knowledge Base Extracted from Wikipedia’. Semantic Web 6, no. 2 (2015): 167–95. https://doi.org/10.3233/SW-140134.
[^diefenbach]: Diefenbach, Dennis, Max De Wilde, and Samantha Alipio. ‘Wikibase as an Infrastructure for Knowledge Graphs: The EU Knowledge Graph’. In The Semantic Web – ISWC 2021, vol. 12922, edited by Andreas Hotho, Eva Blomqvist, Stefan Dietze, et al. Lecture Notes in Computer Science. Springer International Publishing, 2021. https://doi.org/10.1007/978-3-030-88361-4_37.

[^auer]: Auer, Sören, Viktor Kovtun, Manuel Prinz, Anna Kasprzik, Markus Stocker, and Maria Esther Vidal. ‘Towards a Knowledge Graph for Science’. Proceedings of the 8th International Conference on Web Intelligence, Mining and Semantics (New York, NY, USA), WIMS ’18, 25 June 2018, 1–6. https://doi.org/10.1145/3227609.3227689.

[^shimizu]: Shimizu, Cogan, Andrew Eells, Seila Gonzalez, et al. ‘Ontology Design Facilitating Wikibase Integration -- and a Worked Example for Historical Data’. arXiv:2205.14032. Preprint, arXiv, 27 May 2022. https://doi.org/10.48550/arXiv.2205.14032.

[^dobriy]: Dobriy, Daniil, and Axel Polleres. Analysing and Promoting Ontology Interoperability in Wikibase. n.d.
