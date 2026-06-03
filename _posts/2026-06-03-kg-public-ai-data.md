---
title:  "A Knowledge Graph of AI models & data"
date:   2026-06-03
tags: ["Open Data", "Public AI", "Knowledge Graph", "Linked Data"]
categories: ["Open"]
# toc: true
---

What information is publicly available about AI models?
Do we know what data they've used for training, their training strategy...?

While this information is currently only sparsely available from the main LLM service providers, this might be about to change under new EU regulation.
The EU's [AI Act Article 53(1)(d)](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-53), released in July 2025 and set to be [enforced from 2nd August 2026](https://digital-strategy.ec.europa.eu/en/policies/guidelines-gpai-providers), requires AI providers to disclose some minimal information regarding the training content that they use. This includes data size, modalities, languages, names of public datasets, and more.

Transparency over training data should foster good practices for model providers, giving the public oversight of and insight into the models, their biases and possible copyright infringements.


The visualisation below shows a few models that have published a GPAI notice, along with their training data sources. You can also display more models, see whether they used data for pre or post-training in some cases, and hover/click on them for more information.

<iframe src="https://mrmvn.github.io/public-ai-data-viz/"
        width="100%" height="640" style="border:0" loading="lazy"
        title="Public AI Data Sources Viz"></iframe>

> If you can't see a model on there, it's probably because its training data sources have not been disclosed.

This static graph viz was compiled using information disclosed by a few model providers, either in a GPAI notice, in a technical article, or a model card (e.g., on Hugging Face).

Starting from models that had disclosed their training datasets, I created a knowledge graph hosted at [https://public-ai-data-sources.wikibase.cloud/](https://public-ai-data-sources.wikibase.cloud/). Hosting on [wikibase.cloud](https://www.wikibase.cloud/) has several advantages: it's free, it's public (to the point that anyone can contribute to it after logging in), and it can interoperate with Wikidata. While Wikidata has [a project on AI](https://www.wikidata.org/wiki/Wikidata:WikiProject_Artificial_Intelligence), it doesn't have the ideal properties for this project yet (*trained on*, *pre-trained on*, *GPAI notice*...), so I decided to create a new wikibase to experiment freely with a dedicated ontology and database.

Please feel free to edit or improve the knowledge graph directly on the wikibase. I'll keep updating the visualisation regularly. And if you have any other feedback or questions, please contact me at [contact-mario-morvan at pm.me](mailto:contact-mario-morvan@pm.me).

