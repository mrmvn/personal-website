---
title:  "Citation Location Needed"
date:   2026-05-17
last_modified_at: 2026-05-20
tags: ["Wikipedia", "citations"]
categories: ["Research", "Blog"]
excerpt: "How specifying in-source location can help fight misinformation on Wikipedia"
toc: true
---

[Verifiability](https://en.wikipedia.org/wiki/WP:V) is at the very core of Wikipedia's philosophy.
It requires that any non obvious claim be directly backed up by a [reliable source](https://en.wikipedia.org/wiki/WP:RS).
The best way of enabling this is to [place citations directly in the text](https://en.wikipedia.org/wiki/Wikipedia:Inline_citation), often right after the claims they support.

But how verifiable is Wikipedia in practice? How to improve its effective verifiability?
This blog post touches on these questions, and makes a case for accrued use of in-source locators in citations.

<!-- ## Intro -->
<!-- ## Problem -->

### Problematic citations
Citations can be problematic in various ways, for example if they contain inaccurate or inauthentic metadata, or refer to dubious/unreliable source.
On English Wikipedia, there are 95 different inline templates used to flag verifiability issues, often to do with problematic citations:
[\{\{failed verification\}\}](https://en.wikipedia.org/wiki/Template:Failed_verification),
[\{\{citation not found\}\}](https://en.wikipedia.org/wiki/Template:Citation_not_found),
[\{\{irrelevant citation\}\}](https://en.wikipedia.org/wiki/Template:Irrelevant_citation),
[\{\{verify source\}\}](https://en.wikipedia.org/wiki/Template:Verify_source),
[\{\{AI-generated source?\}\}](https://en.wikipedia.org/wiki/Template:AI-generated_source),
[\{\{AI-retrieved source\}\}](https://en.wikipedia.org/wiki/Template:AI-retrieved_source)...

Even a correctly formatted citation to a reputable source can be misleading, if the citing statement can't actually be *entailed* (i.e. derived) from the cited source(s).
<!-- While no estimate on the rate of claims unsupported by their sources exist on Wikipedia as a whole -->
While building datasets for automatic verification from Wikipedia by annotating claims with respect to their references, these two research papers point to possibly worrying levels of unsupported statements:
- Petroni et al. 2023[^petroni_2023] estimate that "more than 40% of the time, no evidence can be found in the reference to verify a claim",
- Kamoi et al. 2023[^kamoi_2023] find that 33% of claims (55.8% of subclaims) are fully supported, while 12.3% of claims (25.9% of subclaims) are not supported, and 54.7% of claims (18.2% of subclaims) are only partially supported.

While these studies cannot be extrapolated to the whole of Wikipedia because of how datasets are constructed and claims annotated, they sugggest that entailment rates might be much lower than expected on the collaborative encyclopedia.
Problematic citations pose a risk to knowledge integrity, and thus should urge us to seriously consider the problem of effective claim verification on Wikipedia.

<!--Overall, problematic citations pose a risk to Wikipedia's verifiability knowledge integrity, we ought to -->

### Verifying is hard

<!-- [^fetahu_2016][^redi_2019][^chou_2020][^przybyla_2022] are more about identifying need for sources and finding possible ones -->

Verifying citation entailment meets several hurdles in practice. 
First, it requires access to the source document, which can be [restricted by location, time, cost, language, etc](https://en.wikipedia.org/wiki/Wikipedia:Reliable_sources/Cost). In a 2018 blog post[^redi_2018], Redi et al. estimated that "*less than half* of the official versions of scholarly publications cited with an identifier in Wikipedia are freely available on the web".

Assuming that a citation's source is accessible, the next step and core of the verification process is to peruse the source in order to identify sufficient evidence justifying the claim.
This is what annotators did to label the SIDE[^petroni_2023] and WiCE[^kamoi_2023] datasets.

Note that the verification task is ambiguously defined, since it might not be perfectly clear which part of the citing statement (paragraph, sentence, clause...) exactly is meant to be supported by the source.
This led several works to decompose the claims in subclaims[^kamoi_2023], or in predicting the citation span [^fetahu_2017].


Regardless of whether it is done by humans or automatic systems, verifying citations is a difficult task with associated costs.


### Ever more citations

On the below Figure, we show the evolution of the number of citations on the English Wikipedia. 
We did so by randomly sampling 20000 articles from dumps at different dates, and counting the number of "\<ref\>" tags as well as other citation templates: [\{\{sfn\}\}](https://en.wikipedia.org/wiki/Template:Sfn), [\{\{sfnp\}\}](https://en.wikipedia.org/wiki/Template:Sfnp), [\{\{r\}\}](https://en.wikipedia.org/wiki/Template:r).

![Trend of total number of citations on the English Wikipedia between 2014 and 2026]({{'/assets/images/trend_total_citations.png'}})


Compared to the number of articles that has increased by 1.5x, the number of citations increased by 3.1x from Nov 2014 to Jan 2026.
On the one hand, having more and more citations in total and per article is a good sign for verifiability of content. 
On the other hand, it increases the volume of citations to verify.
Assuming that we'd want to verify all Wikipedia citations, this would mean more than 70 million of them in 2026, with a number that increases rapidly. Are we able to keep up with it?
And beyond the mere volume, are new citations more or less likely to be problematic than old ones, and in what ways?


Though important, we won't dig much further into these questions right now. 
Suffice it to highlight that if problematic citations indeed threaten Wikipedia's knowledge integrity, then this threat is likely to keep growing because of the increasing number of citations, and not least, the increasing use of AI in editing articles.

<!-- ### The total cost of verification -->

<!-- ## Analysis -->

### *Where* in the source?

To make the job of verifying citations entailment easier, one can specify which part of the source supports the citing statement.
This simple trick saves time to the verifier by limiting the text to be compared against.  <!-- maybe a note on audio/video too -->
Wikipedia's guidelines on citing sources encourages this practice especially for lenghty sources:

> ["When citing lengthy sources, you should identify which part of a source is being cited."](https://en.wikipedia.org/wiki/Wikipedia:Citing_sources#Identifying_parts_of_a_source)
<!-- [^wikipedia_citing_sources_1] -->

> ["A footnote may also contain a relevant quotation from the source. This is especially helpful when the cited text is long or dense. A quotation allows readers to immediately identify the applicable portion of the reference. Quotes are also useful if the source is not easily accessible. However, caution should be exercised, as always, to avoid copyright violations."](https://en.wikipedia.org/wiki/Wikipedia:Citing_sources#Additional_annotation)
<!-- [^wikipedia_citing_sources_2] -->

The "references and page numbers" how-to-guide goes on to suggest that: 

> ["It helps to give a page number or page range—or a section, chapter, or  other division of the source—because then the reader does not have to  carefully review the whole cited source to find the relevant supporting evidence, which promotes efficient source checking."](https://en.wikipedia.org/wiki/Help:References_and_page_numbers)
<!-- [^wikipedia_help_ref_pages] -->

These mentions of in-source location can be made directly in unstructured references, or preferably using dedicated parameters in citation templates, such as `p` or `page` for a single page, `pages` or `pp` for a range of pages.
Lesser used parameters include free-format keyword `at`, keywords related to chapters (`chapter`, `contribution`, `entry`, `article`, `section`), quotes (`quote`, `q`, `quotation`, `quotepage`, `qp`, `quotation-page`, `quotepages`, `qpp`, `quotation-pages`, `quote-location`, `quote-loc`, `quotation-location`, `quote-at`), court cases  (`panel`, `pinpoint`, `opinion`), video games (`level`, `scene`), video/audio (`episode`,`time`,`minute`). In the below analysis, all these additional parameters are grouped in the 'other' category.

On the Figure below, we show the evolution of the use of in-source locators, estimated by parsing the citations in our random samples at different dates.

![Evolution of total number of citations and use of in-source locators on the English Wikipedia between 2014 and 2026]({{'/assets/images/trend_total_citations_with_locators.png'}})

Looking at the big picture, it is apparent that the use of locating parameters, even when considering the logical 'OR' of them in green, increase more slowly than the total number of citations. 
Looking at the detail for the 5 most represented citation templates (web, news, book, article, or no template), this discrepancy originates largely from the sharp increase in web-based citations (affecting mainly the 'cite web' and to a certain extent 'cite news' and other templates too), which very scarcely make use of in-source locators. However, other templates such as book, or journal, also see diminishing fraction of citations using in-source locators in general and the `page`/`p` in particular.

In the below barplot, we show the shares of different locators per citation template at the beginning of the year, illustrating the intertemplate discrepancies in the use of in-source locators.
![Number of citation and in-source locators per main template for 20000 random articles on 1st Jan 2026]({{'/assets/images/barplot_located_citations_2026-01-01.png'}})

It is worth noting that the high proportion of page ranges specified with the 'cite journal' template mostly corresponds to the page range corresponding to full articles in their proceedings, providing no useful information to find information within articles themselves.


### Recommendations

- encourage the use of page indications for books, articles, and other page-based sources.
- encourage the use of quotations, especially where pages are ambiguous, or sources hard to access (with caution not to violate copyright law).

Wikipedia's guidelines and the design of its editing mode could be adjusted to support editors.

Furthermore, similarly with the tools deployed to detect the need for citations, the development and deployment of tools to check citations (authencitiy, accuracy, completeness, in-source precision, mutual span, entailment...) could empower editors to detect possible issues and improve existing citations.

Finally, we suggest the possible use of a platform that would indicate the verification status of citations, with annotations from humans or machines.


### Method, Code, Caveats

The code used to produce this analysis and visualisations is available at ...
Should you have questions on the analysis method, please visit the codebase or contact me directly.

Error bars shown on the trend plots correspond to the 95% confidence intervals around the estimated totals. 
These are based on estimates of the numbers of citations per article in the 20000 random samples.

A few caveats:
- some citations may include quotes directly in the text, and these are not counted in the in-source locators,
- some citations may have incorrectly formatted location indicators that have not been parsed and thus counted in this analysis,
We think that these only represent a small fraction of all citations, and do not change in any significant way the argument,


## See also

- Presentation at Wikimania in July 2026 ([Talk page](https://wikimedia.eventyay.com/wm/wikimania2026/talk/YASJQZ/), [Slides](assets/docs/cln_slides_wikimania.pdf), [Recording](https://youtu.be/IKDrJJMUDW8?t=27044))

## References

[^redi_2018]: Redi, M., Taraborelli, D. & Orlowitz, J. How many Wikipedia references are available to read? We measured the proportion of open access sources across languages and topics. Wikimedia Foundation (2018). [wikimediafoundation.org](https://wikimediafoundation.org/news/2018/08/20/how-many-wikipedia-references-are-available-to-read/)

[^petroni_2023]: Petroni, F. et al. Improving Wikipedia verifiability with AI. Nat Mach Intell 5, 1142–1148 (2023). [nature.com](https://www.nature.com/articles/s42256-023-00726-1)

[^kamoi_2023]: Kamoi, R., Goyal, T., Rodriguez, J. & Durrett, G. WiCE: Real-World Entailment for Claims in Wikipedia. in Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing 7561–7583 (Association for Computational Linguistics, Singapore, 2023). [aclanthology.org](https://aclanthology.org/2023.emnlp-main.470/)
[^fetahu_2016]: Fetahu, B., Markert, K., Nejdl, W. & Anand, A. Finding News Citations for Wikipedia. in Proceedings of the 25th ACM International on Conference on Information and Knowledge Management 337–346 (ACM, Indianapolis Indiana USA, 2016). [acm.org](https://dl.acm.org/doi/10.1145/2983323.2983808)
[^redi_2019]: Redi, M., Fetahu, B., Morgan, J. & Taraborelli, D. Citation Needed: A Taxonomy and Algorithmic Assessment of Wikipedia’s Verifiability. (2019) [arxiv.org](https://doi.org/10.48550/arXiv.1902.11116)
[^chou_2020]: Chou, Gonzalves, Waldon & Redi, M. Citation Detective: a Public Dataset to Improve and Quantify Wikipedia Citation Quality at Scale. (2020) [wikiworkshop.org](https://wikiworkshop.org/2020/papers/Wiki_Workshop_2020_paper_12.pdf)
[^przybyla_2022]: Przybyła, P., Borkowski, P. & Kaczyński, K. Countering Disinformation by Finding Reliable Sources: a Citation-Based Approach. in 2022 International Joint Conference on Neural Networks (IJCNN) 1–8 (2022). [ieee.org](https://ieeexplore.ieee.org/abstract/document/9891941)
[^fetahu_2017]: Fetahu, B., Markert, K. & Anand, A. Fine Grained Citation Span for References in Wikipedia. (2017) [arxiv.org](https://doi.org/10.48550/arXiv.1707.07278)

[^wikipedia_citing_sources_1]: https://en.wikipedia.org/wiki/Wikipedia:Citing_sources#Identifying_parts_of_a_source
[^wikipedia_citing_sources_2]: https://en.wikipedia.org/wiki/Wikipedia:Citing_sources#Additional_annotation
[^wikipedia_help_ref_pages]: https://en.wikipedia.org/wiki/Help:References_and_page_numbers