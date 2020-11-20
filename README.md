# Medical online contents' credibility dataset
We share the dataset collected between the months 12-2019 and 02-2020. It contains **sentences** extracted from popular medical online articles with corresponding **credibility labels** provided by human experts (medical practitioners from a proper fields).

*This work was financed by the statutory funds of the Polish-Japanese Academy of Information Technology.*

## Annotation protocol
Medical experts evaluated the credibility of sentences with the following set of labels and the corresponding instruction: 

* CRED (credible) - a sentence is reliable; does not raise major objections; contains verifiable information from the medical domain; 
* NONCRED (non-credible) - a sentence contains false or unverifiable information; contains persuasion contrary to current medical recommendations; contains outdated information; 
* NEU (neutral) - a sentence does not contain factual information (e.g., is a question); is not related to medicine; 

Additionally, we have collected following information for each sentence: 

* time_start and time_end for each evaluation; 
* (optional) the predefined tag or a custom reason for evaluating the sentence as non-credible; 
* number of surrounding sentences needed to understand the context of the sentence being evaluated; 

For a detailed annotation protocol and experimental procedure description please refer to the article {TBA}.

## Dataset

The structure of the "sentences.csv" file is as follows:

sentence_id | article_id | body | category | label | keywords | time_start | time_end | context_window | tags | reason
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
5327 | 123 | "Psychiatric drugs do more harm than good ..." | psychiatry | NONCRED | "drug, gøtzsche, psychiatric, dementia, antipsychotic" | 2019-12-19 16:06:56.694 | 2019-12-19 16:12:11.418 | 0 | is anecdote

The structure of "articles.csv" file is as follows:

article_id | title | pub_date | access_date | url | keywords
--- | --- | --- | --- | --- | ---
123 | Psychiatric drugs do more harm than good, says expert, Society, The Guardian | 2015-05-12 | 2019-10-23 | https://www.theguardian.com/society/2015/may/12/psychiatric-drugs-more-harm-than-good-expert | drug, gøtzsche, psychiatric, dementia, antipsychotic

## Maintainers
* [Aleksandra Nabożny](https://github.com/alenabozny "aleksandra.nabozny@pja.edu.pl")

## Contributors
We are grateful to all contributors of this dataset!
* [Aleksandra Nabożny](https://github.com/alenabozny "aleksandra.nabozny@pja.edu.pl")
* [Kamil Warpechowski](https://github.com/kwarpechowski "kwarpech@pja.edu.pl")
* [Bartłomiej Balcerzak](https://github.com/alenabozny/medical_credibility_corpus "b.balcerzak@pjwstk.edu.pl")
* Medical experts who remain anonymus to the public

## License
The Dataset is made available under a [Creative Commons CC-BY-NC 4.0 license](https://creativecommons.org/licenses/by-nc/4.0/legalcode).

## Citing & Authors
If you find this repository helpful, feel free to cite our publication 
`@TBA`
