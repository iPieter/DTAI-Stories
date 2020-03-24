---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Time Series Clustering"
subtitle: ""
summary: ""
authors: ["wannes"]
tags: ["time series", "clustering", "Application"]
categories: ["Anomaly Detection"]
date: 2020-03-24T16:58:21+01:00
lastmod: 2020-03-24T16:58:21+01:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---


Clustering is one of the most widely used techniques for time series because it allows to identify and summarize patterns that are of interest (e.g., frequent or anomalous patterns). Furthermore, it does not rely on costly human supervision of time-consuming labeling.
As a result, time series clustering has been studied for many different applications such as astronomy, biology, meteorology, medicine, finance, robotics, engineering, etc..

## Unsupervised Clustering: DTW

Time series clustering is heavily dependent on the choice of the distance used to compare two series. Typically, one is interested in similarity between shapes represented by a series, irrespective of phase or amplitude. And while many distance measures have been proposed, it has been shown that distance measures that can deal with invariances to amplitude and phase perform particularly well.
One of the best performing similarity measures is Dynamic Time Warping (DTW).

![DTW Warpring](dtw_warp.png)

The resulting clustering is robust against small changes between time series. As can be seen in the figure underneath, DTW allows a clustering that nicely groups similar series.

![DTW clustering](dtw_clustering.png)


The toolbox is available at https://github.com/wannesm/dtaidistance/ .



## Semi-supervised Clustering: COBRAS

Clustering is ubiquitous in data analysis. There is a large diversity in algorithms, loss functions, similarity measures, etc. This is partly due to the fact that clustering is inherently subjective: in many cases, there is no single correct clustering, and different users may prefer different clusterings, depending on their goals and prior knowledge [17]. Depending on their preference, they should use the right algorithm, similarity measure, loss function, hyperparameter settings, etc. This requires a fair amount of knowledge and expertise on the user's side.
Semi-supervised clustering methods deal with this subjectiveness in a differ- ent manner. They allow the user to specify constraints that express their subjective interests. These constraints can then guide the algorithm towards solutions that the user finds interesting. Many such systems obtain these constraints by asking the user to answer queries of the following type: should these two elements be in the same cluster? A so-called must-link constraint is obtained if the answer is yes, a cannot-link otherwise. In many situations, answering this type of questions is much easier for the user than selecting the right algorithm, defining the similarity measure, etc. Active semi-supervised clustering methods
aim to limit the number of queries that is required to obtain a good clustering by selecting informative pairs to query.
In the context of clustering time series, the subjectiveness of clustering is even more prominent. In some contexts, the time scale matters, in other contexts it does not. Similarly, the scale of the amplitude may (not) matter. One may want to cluster time series based on certain types of qualitative behavior (monotonic, periodic, ...), local patterns that occur in them, etc. Despite this variability, and although there is a plethora of work on time series clustering, semi-supervised clustering of time series has only very recently started receiving attention.

![cobras](cobras_logo.png)

Clustering is ubiquitous in data analysis, including analysis of time series. But it is inherently subjective: different users may prefer different clusterings for a particular dataset. Semi-supervised clustering addresses this by allowing the user to provide examples of instances that should (not) be in the same cluster. 

The COBRAS-TS algorithm is a semi-supervised clustering method that can use indirect feedback from users. It clusters with the user in the loop. The user can provide indirect feedback where it is only required to tell the system for a few time series whether two time series represent the same behavior or not. As a result the COBRAS-TS system can identify clusters that are characterized by small local patterns.

![img1](img1.png)
![img2](img2.png)

An interface is provided to the user that actively asks for feedback about time series where the method is the most unsure about how to cluster them.

![gui](cobras_schema.png)
![gui](cobras_example.png)

The toolbox is available at https://dtai.cs.kuleuven.be/software/cobras/ .




