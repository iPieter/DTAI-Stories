+++

math = true

title = "Classifying Italian Newspaper Text: News or Editorial"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Pietro Totis","Manfred Stede"]
authors_link = ["pietrototis.me", "http://www.ling.uni-potsdam.de/~stede/"]
featured = true

abstract = "We present a text classifier that can distinguish Italian news stories from editorials. Inspired by earlier work on English, we built a suitable train/test corpus and implemented a range of features, which can predict the distinction with an accuracy of 89,12%. As demonstrated by the earlier work, such a feature-based approach outperforms simple bag-of-words models when being transferred to new domains. We argue that the technique can also be used to distinguish opinionated from non-opinionated text outside of the realm of newspapers. "

date = 2018-12-01T20:01:54+01:00
draft = false
conference = "Clic-It"
conference_page = "http://clic2018.di.unito.it/it/home/"
url_pdf = "http://ceur-ws.org/Vol-2253/paper02.pdf"

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference paper
# 2 = Journal article
# 3 = Manuscript
# 4 = Report
# 5 = Book
# 6 = Book section
publication_types = ["1"]

# Publication name and optional abbreviated version.
publication = ""
publication_short = ""


# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["Argumentation", "Natural Language Processing"]
categories = []

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = ""
+++
## Description

A crucial task when texts are analyzed from an argumentative perspective is to distingush whether the content expresses an opinion of the writer or an objective statement. We implemented a classification technique based on linguistic features on a corpus composed of Italian news articles and editorials: the classifier proves to be robust against domain change and thus suitable for the more general task of classifying opinonated versus non-opinionated texts.

### Classifier

The classifier follows the approach by [Krüger et. al.](https://www.cambridge.org/core/journals/natural-language-engineering/article/classifying-news-versus-opinions-in-newspapers-linguistic-features-for-domain-independence/A5145D45A3BD6C56B3F7DAB6B7791EBC), who succesfully introduced on English texts a classification strategy based on linguistic features. We consider:

* text statistics (length of a sentence,  frequency of digits,  etc.)
* ratio of punctuation symbols
* ratio of temporal, causal and other connectives
* verb tenses
* pronouns (especially 1st and 2nd person)
* sentiment indicators

### Experiments

#### Newspaper classification

We test our approach first on classifying Italian news articles and editorials. We compare the linguistic feature based classification with unigrams and POS tagging based classification. The results show this technique is comparable to the other approaches from literature.


|   | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| L | 83,4 | 86,0 | 79,4 | 82,6 |
| P | 84,5 | 85,8 | 82,5 | 84,1 |
| U | 82,3  | 80,3 | 85,4 | 82,8 |
| L+P<br>P+U<br>U+P | ~87,5  | ~88,5 | ~86,0  | ~87,2  |
| L+P+U | 89,1 | 89,6  | 88,3 | 89,0 |

L= linguistic features, U= unigrams, P= POS-taging

The following table is a summary of the most important linguistic features reaccording to the internal weights of the SVM classifier. On the left the features pointing towards editorials, on the right those pointing towards news articles:

| Feature |  Weight | | Feature | Weight |
|---|---|---|---|---|
| Pronouns   | 3,55  | | Citations |  4,89 |
| Temporal conn  | 2,06 | | Complexity | 2,67 |
| Sentiment pos   | 1,80  | | Past perfect | 2,11 |
| Negations   | 1,73  | | Future | 2,01 |
| Sentiment neg   | 1,66 | | Token length | 1,88 |


#### Out of domain classification

We then consider a dataset composed of Wikipedia articles and Amazon reviews (Italian), we classify these texts using the classifier trained on the Italian newspaper corpus with the following performance:

|   | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| L | 83,9 | 84,2 | 82,8 | 83,5 |
| P | 64,7 | 63,1 | 69,5 | 66,1 |
| U | 39,2 | 43,3 | 70,0 | 53,5 |
| L+U | 65,0  | 50,6 | 73,3  | 59,9  |
| L+P  | 72,6  | 70,4 | 71,7  | 71,0 |
| U+P  | 50,8 | 50,6 | 73,3 | 59,9  |
| L+P+U | 61,3 | 57,8 | 81,4 | 67,6 |

### Conclusions

We presented a first classifier for distinguishing between "News" and "Editorial" categories in an Italian newspaper corpus. We showed that the linguistic feature-oriented approach outperforms other techniques and shows remarkable robustness when the classifier is appied on a different domain, with the goal of separating opinionated from non-opinionated texts.

Our experiments are comparable to the results obtained by [Krüger et. al.](https://www.cambridge.org/core/journals/natural-language-engineering/article/classifying-news-versus-opinions-in-newspapers-linguistic-features-for-domain-independence/A5145D45A3BD6C56B3F7DAB6B7791EBC), showing that the approach based on linguistic features is not overfitted to the language.
