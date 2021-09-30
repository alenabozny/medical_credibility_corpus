# Medical online contents' credibility dataset
We share the dataset collected between the months 12-2019 and 02-2020. It contains **sentences** extracted from popular medical online articles with corresponding **credibility labels** provided by human experts (medical practitioners from a proper fields).

![alt text](https://www.zeitbasierte-gestaltung.de/wp-content/uploads/2017/09/logo-polish-japanese-academy-of-information-technology@2x.png "Logo PJAIT")

*This work was financed by the statutory funds of the Polish-Japanese Academy of Information Technology.*

## Annotation protocol
Medical experts evaluated the credibility of sentences with the following set of labels and the corresponding instruction: 

* CRED (credible) - a sentence is reliable; does not raise major objections; contains verifiable information from the medical domain; 
* NONCRED (non-credible) - a sentence contains false or unverifiable information; contains persuasion contrary to current medical recommendations; contains outdated information; 
* NEU (neutral) - a sentence does not contain factual information (e.g., is a question); is not related to medicine; 

We have collected following information for each sentence: 

* **sequence_nr** - position of the sentence in the corresponding article;
* **body** - text of the sentence;
* **category** - what category the sentence relates to (children_antibiotics, psychiatry, ssri_during_pregnancy, etc.)
* **time_start** and **time_end** for each evaluation; 
* **context_window** - number of surrounding sentences needed to understand the context of the sentence being evaluated; 
* **tags**/**reason** - (optional) the predefined tag or a custom reason for evaluating the sentence as non-credible; 

For a detailed annotation protocol and experimental procedure description please refer to the [article](https://preprints.jmir.org/preprint/26065).

## Dataset

The structure of the "sentences.csv" file is as follows:

sentence_id | article_id | sequence_nr | body | category | label | keywords | time_start | time_end | context_window | tags | reason
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
5327 | 123 | 1 | "Psychiatric drugs do more harm than good ..." | psychiatry | NONCRED | "drug, gøtzsche, psychiatric, dementia, antipsychotic" | 2019-12-19 16:06:56.694 | 2019-12-19 16:12:11.418 | 0 | is anecdote

The structure of "articles.csv" file is as follows:

article_id | title | pub_date | access_date | url | keywords
--- | --- | --- | --- | --- | ---
123 | Psychiatric drugs do more harm than good, says expert, Society, The Guardian | 2015-05-12 | 2019-10-23 | https://www.theguardian.com/society/2015/may/12/psychiatric-drugs-more-harm-than-good-expert | drug, gøtzsche, psychiatric, dementia, antipsychotic

Values are separated by semicolons.

## Limitations of the dataset

There are about 5% of duplicated sentences in the file **sentences.csv**. Duplicates' presence is due to the imperfection of the web crawler used for articles' retrieval as well as automatic sentence segmentation. There are two main reasons:
1. Lists' items separation mechanism:

Whenever encountered a list, such as:
'''html
<ul> Lorem ipsum. Dolor sit amet:
  <li> Item 1. </li>
  <li> Item 2. </li>
  <li> Item 3. </li>
</ul>
'''
the algorithm divided it to such set of sentences:
'''
Lorem ipsum.
Dolor sit amet: Item 1.
Lorem ipsum.
Dolor sit amet: Item 2.
Lorem ipsum.
Dolor sit amet: Item 3.
'''
However, each duplicated sentence received separate label during the annotation process. Some of the duplicates received different labels due to inter-expert disagreements or due to different context window within which it was viewed. If you wish to download the cleaned dataset, please use **sentences_cleaned_duplicates.csv** instead **sentences.csv**. In this file duplicate sentences with repeated label and a 0 context window have an empty label field.

2. There are also some sentences containing e.g. short headers (e.g. "Claim 4.") numbers or single punctuation marks. Those are easy to get rid of during data preprocessing and are always labelled as neutral.

Note that not all duplicates result out of errors.


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

## Citing
If you find this repository helpful, feel free to cite our publication 

```
@Online{nabozny2020digging/online,
  author      = {Nabożny A., Balcerzak B., Wierzbicki A, Morzy M.},
  title       = {Digging for the truth: the case for active annotation in evaluating the credibility of online medical information},
  date        = {2020-11-26},
  eprinttype  = {JMIR preprint},
  eprint      = {preprint/26065}
  doi         = {10.2196/preprints.26065}
}
```
