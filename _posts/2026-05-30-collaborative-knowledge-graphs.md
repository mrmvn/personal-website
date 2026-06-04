---
title:  "Collaborative Knowledge Graphs"
date:   2026-05-30
last_modified_at: 2026-06-04
tags: ["Knowledge Graph", "Co-production"]
categories: ["Blog"]
toc: true
---

<!-- Main goal: establish a typology of CKGs, show existing success, their promise and untapped potential -->
Open, collaborative curation of knowledge graphs (KGs) has already contributed to making the internet more structured and trustworthy, and shows promise for continuing to do so in the coming decades.
We use the term **collaborative knowledge graph** (CKG) for KGs that are collaboratively curated by a group of people.
Below is a review of different examples of CKGs, identifying three main types of collaboration. 
The aim is to broadly cover the panorama of CKGs, but certainly not of all open KG databases.


## Why Knowledge Graphs?

Graphs are most suitable to encode and represent interconnections in data, as edges between nodes. Knowledge graphs add a semantic layer to graphs, whereby nodes become typed entities linked through typed relations or statements. This combined relational and semantic structure is particularly well suited for tracing, verifying, querying information. It can foster not only trust, but also interoperability between different KG databases, using shared standards or principles such as [linked data](https://en.wikipedia.org/wiki/Linked_data).

In a web whose traffic is increasingly mediated by bots, and where information access is to be mediated largely through search engines and LLMs, structuring data becomes even more important and valuable. As LLM training —and to some extent, inference— break the link between original information sources and output statements, human-curated KGs provide deterministically queriable, verifiable, and answerable knowledge. This structured, high-trust data can then be used in other collaborative projects or to improve the reliability of LLMs through training[^guu] or inference [^lewis][^pan][^frog][^lavrinovics]. 


## Examples of CKGs

We'll be using these examples throughout:
- [Wikidata](https://www.wikidata.org/)[^vrandecic], the central knowledge graph of encyclopedic knowledge, used across Wikimedia projects and the most studied CKG — collaborative at every layer (data, ontology, bots),
- [Wikibase ecosystem](https://wikibase-metadata.wmcloud.org/)[^diefenbach], the interoperable pool of KGs built on Wikidata's software, each with its own community and governance,
- [DBpedia](https://www.dbpedia.org/)[^lehmann], structured knowledge extracted from Wikipedia and a founding hub of the Linked Open Data cloud, where collaboration sits in the extraction framework and ontology mappings rather than data entry,
- [ORKG](https://orkg.org/)[^auer][^jaradeh], a graph of machine-actionable scholarly knowledge — papers, comparisons, reviews — contributed by logged-in researchers,
<!-- - [ConceptNet](https://conceptnet.io/)[^speer], a crowdsourced multilingual graph of commonsense knowledge, grown from the Open Mind Common Sense project, -->
- [schema.org](https://schema.org/)[^guha], a shared vocabulary for marking up structured data on web pages, collaborative only at the ontology layer and governed by a small group with strong big-tech ties,
- [OBO foundry](https://obofoundry.org/)[^smith], a federation of interoperable biomedical ontologies coordinated under explicit shared design principles.


## A typology of collaboration in KGs

Collaboration can happen at different levels, namely data entry, ontology or algorithmic curation. These are more continuous dimensions to think of collaboration than separate buckets: a KG can have more or less of each type.

### Collaborative data entry

A first way to collaborate on knowledge graphs is to let a group of humans create and edit graph data itself.
The resulting KGs are sometimes called crowdsourced KGs.

Wikidata allows anyone —logged in or not— to edit the KG by creating or editing items and statements. It currently has about 44,000 [active users](https://www.wikidata.org/wiki/Special:ActiveUsers) monthly, a total of 122 million items, and more than 2 billion edits (labels, references, statements...). Each item carries multilingual labels, and is publicly licensed under CC0, explaining why Wikidata has become a reuse hub across many projects.

Beyond Wikidata, there are hundreds of 'Wikibases', i.e. other KGs based on the Wikibase software. These projects are generally managed by different communities, with their own rules and objectives. Among prominent Wikibases featuring collaborative data entry, we find: 
FactGrid (historical research; ~700 users, passed 1M items Oct 2024, CC0, run by the Gotha Research Centre / NFDI4Memory), Rhizome ArtBase (born-digital art), Lingua Libre (audio), the EU Knowledge Graph,[^diefenbach] MaRDI (mathematics, ~7M items), and PersonalData.io. The Wikibase Registry is itself a CKG of KGs. Note however, that many Wikibases are expert-curated communities, not open to anyone like Wikidata. 

ORKG invites contributions from logged-in users to add or edit various elements of the KG: not only reviews or metadata about individual papers, but crucially, comparisons between papers that get a DOI each. The resulting scholarly KG is thus crowdsourcing contributions mainly from the researcher community rather than the general public. Contributions such as comparisons, visualisations, reviews and lists can be accessed directly on the website, or via the ORKG Ask platform which uses a LLM with vector-search layer to provide natural language access into the graph.


### Collaborative Ontologies

An ontology is the schema layer of a KG: the vocabulary of entity types (classes) and relation types (properties), together with the constraints governing how they legitimately combine. Below we outline three ways in which ontologies can be collaboratively defined:  schema emerging from data entry, schema as the product itself, and schema embodied in explicit extraction mappings. 

[Wikidata's ontology](https://www.wikidata.org/wiki/Wikidata:WikiProject_Ontology) is itself collaboratively maintained. While anyone can create classes (items, with Q-IDs), proposing properties (with P-IDs) requires community discussion and consensus.
This process helps keep the ontology consistent, but can also slow schema evolution and requires active community moderation. In practice, only a small fraction of Wikidata users shape its ontology, suggesting that its collaborative aspect happens more at the data entry level.[^piscopo2]


Other wikibase-like CKGs manage their ontologies differently. For example, FactGrid which tolerates competing ontologies in one pool.
A selling point of wikibases is their support for mapping items with Wikidata or other wikibases, enabling interoperability between wikibases when parts of their ontologies map.
However, independently-built ontologies don't easily map onto Wikibase ontologies, limiting the potential for interoperability[^dobriy][^shimizu].

Other CKG projects aim at producing a schema as their main product, not as a byproduct of their knowledge building practice. That's the case of OBO foundry, which federates more than one hundred biomedical ontologies under explicit shared principles, and is open to any interested individuals. We could also mention schema.org, a shared vocabulary for web markup, developed through the W3C Schema.org Community Group but launched and still steered by the major search engines (Google, Microsoft, Yahoo, Yandex). Although its curation [process](https://schema.org/docs/howwework.html) is open and collaborative in principle, it remains tied to corporations and governed by a small number of actors.

DBpedia features yet another collaborative way to curate its [ontology](https://mappings.dbpedia.org/index.php/How_to_edit_the_DBpedia_Ontology). Indeed, it is derived from infobox-to-ontology mappings that are collaboratively maintained through the public mapping wiki. This leads us to our last collaborative dimension, making use of algorithms to curate KGs.

### Collaborative algorithmic curation

Several KGs involve the use of algorithms, bots and tools to automate tasks and support humans in the data curation process. When there is a collaborative process to govern the use of these algorithms, we will include this as another dimension of collaboration in KG curation.

DBpedia offers a striking example of collaborative algorithmic KG curation. Indeed, its construction relies solely on an extraction framework and mappings wiki, both collaboratively maintained. 

On Wikidata, [bots](https://www.wikidata.org/wiki/Wikidata:Bots) currently account for [more than half](https://wikidata.wikiscan.org/) of the edits, sharing the load with humans. They must follow certain requirements and be approved by the community to perform specific tasks. Although integral to the growth and success of Wikidata, this human-bot collaboration has also created some new challenges.[^koutsiana][^piscopo3][^muller] Beyond bot edits, Wikidata also makes use vandalism-detection models such as those underlying [ORES](https://www.wikidata.org/wiki/Wikidata:ORES)[^sarabadani], making use of ML models trained on data labelled by volunteers to help volunteers flag vandalism.[^heindorf] There also are prospects for "significantly improving" the accuracy of these systems,[^trokhymovych] which would sharpen, rather than remove, the question of algorithmic governance on Wikidata.


## Final points

Although we outlined three general categories of collaboration, every project has its own focus community and governance structure. Collaboration varies quantitatively and qualitatively in each case, crossing over different modes with a mix that may vary in time.
 
Even when there exist collaborative processes, data, ontology or algorithmic curation is often reserved to a small group of skilled developers or domain experts, in some cases with strong ties with major big tech companies (e.g., schema.org). This creates biases and generates a power asymmetry, skewing most CKG projects.[^gianluca] 
Improving the accessibility of editing interfaces and processes would already alleviate some of these issues, but this will likely remain a persisting challenge for these and future CKGs.

In the coming years, I wouldn't be surprised to see CKGs being used for new and diverse applications such as fact-checking, impact assessment, value alignment; to see some as providing a shared, verifiable substrate for an agent-mediated web, and others as the ground for new forms of collaboration between humans and machines.


## References

[^gianluca]: Demartini, Gianluca. ‘Implicit Bias in Crowdsourced Knowledge Graphs’. Companion Proceedings of The 2019 World Wide Web Conference (New York, NY, USA), WWW ’19, 13 May 2019, 624–30. https://doi.org/10.1145/3308560.3317307.
<!-- [^piscopo1]: Piscopo, Alessandro, Chris Phethean, and Elena Simperl. ‘What Makes a Good Collaborative Knowledge Graph: Group Composition and Quality in Wikidata’. In Social Informatics, edited by Giovanni Luca Ciampaglia, Afra Mashhadi, and Taha Yasseri. Springer International Publishing, 2017. https://doi.org/10.1007/978-3-319-67217-5_19. -->
[^piscopo2]: Piscopo, Alessandro, and Elena Simperl. ‘Who Models the World? Collaborative Ontology Creation and User Roles in Wikidata’. Proc. ACM Hum.-Comput. Interact. 2, no. CSCW (2018): 141:1-141:18. https://doi.org/10.1145/3274410.
[^koutsiana]: Koutsiana, Elisavet, Gabriel Maia Rocha Amaral, Neal Reeves, Albert Meroño-Peñuela, and Elena Simperl. ‘An Analysis of Discussions in Collaborative Knowledge Engineering through the Lens of Wikidata’. Journal of Web Semantics 78 (October 2023): 100799. https://doi.org/10.1016/j.websem.2023.100799.
[^vrandecic]: Vrandečić, Denny, and Markus Krötzsch. ‘Wikidata: A Free Collaborative Knowledgebase’. Commun. ACM 57, no. 10 (2014): 78–85. https://doi.org/10.1145/2629489.
<!-- [^farber]: Färber, Michael, Basil Ell, Carsten Menne, and Achim Rettinger. A Comparative Survey of DBpedia, Freebase, OpenCyc, Wikidata, and YAGO. n.d. -->
[^pan]: Pan, Shirui, Linhao Luo, Yufei Wang, Chen Chen, Jiapu Wang, and Xindong Wu. ‘Unifying Large Language Models and Knowledge Graphs: A Roadmap’. IEEE Transactions on Knowledge and Data Engineering 36, no. 7 (2024): 3580–99. https://doi.org/10.1109/TKDE.2024.3352100.
[^guha]: Guha, R. V., Dan Brickley, and Steve Macbeth. ‘Schema.Org: Evolution of Structured Data on the Web’. Communications of the ACM 59, no. 2 (2016): 44–51. https://doi.org/10.1145/2844544.
[^jaradeh]: Jaradeh, Mohamad Yaser, Allard Oelen, Kheir Eddine Farfar, et al. ‘Open Research Knowledge Graph: Next Generation Infrastructure for Semantic Scholarly Knowledge’. Proceedings of the 10th International Conference on Knowledge Capture (New York, NY, USA), K-CAP ’19, 23 September 2019, 243–46. https://doi.org/10.1145/3360901.3364435.
[^lehmann]: Lehmann, Jens, Robert Isele, Max Jakob, et al. ‘DBpedia – A Large-Scale, Multilingual Knowledge Base Extracted from Wikipedia’. Semantic Web 6, no. 2 (2015): 167–95. https://doi.org/10.3233/SW-140134.
[^diefenbach]: Diefenbach, Dennis, Max De Wilde, and Samantha Alipio. ‘Wikibase as an Infrastructure for Knowledge Graphs: The EU Knowledge Graph’. In The Semantic Web – ISWC 2021, vol. 12922, edited by Andreas Hotho, Eva Blomqvist, Stefan Dietze, et al. Lecture Notes in Computer Science. Springer International Publishing, 2021. https://doi.org/10.1007/978-3-030-88361-4_37.
[^auer]: Auer, Sören, Viktor Kovtun, Manuel Prinz, Anna Kasprzik, Markus Stocker, and Maria Esther Vidal. ‘Towards a Knowledge Graph for Science’. Proceedings of the 8th International Conference on Web Intelligence, Mining and Semantics (New York, NY, USA), WIMS ’18, 25 June 2018, 1–6. https://doi.org/10.1145/3227609.3227689.
[^shimizu]: Shimizu, Cogan, Andrew Eells, Seila Gonzalez, et al. ‘Ontology Design Facilitating Wikibase Integration -- and a Worked Example for Historical Data’. arXiv:2205.14032. Preprint, arXiv, 27 May 2022. https://doi.org/10.48550/arXiv.2205.14032.
[^dobriy]: Dobriy, Daniil, and Axel Polleres. Analysing and Promoting Ontology Interoperability in Wikibase. n.d.
[^lewis]: Lewis, Patrick, Ethan Perez, Aleksandra Piktus, et al. ‘Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks’. arXiv:2005.11401. Preprint, arXiv, 12 April 2021. https://doi.org/10.48550/arXiv.2005.11401.
[^guu]: Guu, Kelvin, Kenton Lee, Zora Tung, Panupong Pasupat, and Ming-Wei Chang. REALM: Retrieval-Augmented Language Model Pre-Training. n.d.
[^speer]: Speer, Robyn, Joshua Chin, and Catherine Havasi. ‘ConceptNet 5.5: An Open Multilingual Graph of General Knowledge’. Preprint, 12 December 2016. https://arxiv.org/abs/1612.03975v2.
[^smith]: Smith, Barry, Michael Ashburner, Cornelius Rosse, et al. ‘The OBO Foundry: Coordinated Evolution of Ontologies to Support Biomedical Data Integration’. Nature Biotechnology 25, no. 11 (2007): 1251–55. https://doi.org/10.1038/nbt1346.
[^piscopo3]: Piscopo, Alessandro. ‘Wikidata: A New Paradigm of Human-Bot Collaboration?’ arXiv:1810.00931. Preprint, arXiv, 1 October 2018. https://doi.org/10.48550/arXiv.1810.00931.
[^frog]: https://diff.wikimedia.org/2025/07/23/making-question-answering-systems-smarter-with-knowledge-graphs-using-frog-a-wikidata-research-fund-2024-highlight/
[^lavrinovics]: Lavrinovics, Ernests, Russa Biswas, Johannes Bjerva, and Katja Hose. ‘Knowledge Graphs, Large Language Models, and Hallucinations: An NLP Perspective’. Journal of Web Semantics 85 (May 2025): 100844. https://doi.org/10.1016/j.websem.2024.100844.
[^muller]: Müller-Birn, Claudia, Benjamin Karran, Janette Lehmann, and Markus Luczak-Rösch. ‘Peer-Production System or Collaborative Ontology Engineering Effort: What Is Wikidata?’ Proceedings of the 11th International Symposium on Open Collaboration (New York, NY, USA), OpenSym ’15, 19 August 2015, 1–10. https://doi.org/10.1145/2788993.2789836.
[^heindorf]: Heindorf, Stefan, Martin Potthast, Benno Stein, and Gregor Engels. ‘Vandalism Detection in Wikidata’. Proceedings of the 25th ACM International on Conference on Information and Knowledge Management (New York, NY, USA), CIKM ’16, 24 October 2016, 327–36. https://doi.org/10.1145/2983323.2983740.
[^sarabadani]: Sarabadani, Amir, Aaron Halfaker, and Dario Taraborelli. ‘Building Automated Vandalism Detection Tools for Wikidata’. Proceedings of the 26th International Conference on World Wide Web Companion - WWW ’17 Companion, 2017, 1647–54. https://doi.org/10.1145/3041021.3053366.
[^trokhymovych]: Trokhymovych, Mykola, and Lydia Pintscher. Graph-Linguistic Fusion: Using Language Models for Wikidata Vandalism Detection. n.d.
