---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Can computers create jokes?"
subtitle: "The range of tasks Artificial Intelligenge can fulfill keeps strongly growing, but will an AI ever understand how to successfully create jokes? And if so, how?"
summary: ""
authors: ["Thomas Winters"]
tags: ["Computational Humor", "Computational Creativity"]
categories: []
date: 2020-03-23T23:52:28+01:00
lastmod: 2020-03-23T23:52:28+01:00
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

### Computational humor

Can computers be funny?
Certainly your virtual assistant (e.g. *Siri* or *Alexa*) is able to tell a joke if you ask for one, but these are of course pre-written, human-made jokes.
One might wonder if computers are already advanced enough to understand how to construct good jokes.
And if they can write jokes, can they do this in any language and about any topic?
And could they tailor their sense of humor to users?

Many researchers have already looked into humor generation algorithms.
Recent popular neural networks approaches seem to indicate that
writing good jokes is [still far off](https://towardsdatascience.com/teaching-gpt-2-a-sense-of-humor-fine-tuning-large-transformer-models-on-a-single-gpu-in-pytorch-59e8cec40912).
Most of the funny things computers create using neural networks, [seem to mostly occur on accident](https://aiweirdness.com/books).

Further in the past, however, more symbolic approaches have been used to generate subjectively better jokes.
Researchers created programs to, for example, [generate punning riddles](http://joking.abdn.ac.uk/webversion/welcome.php),
[create analogy jokes](http://www.infoivy.com/2013/09/big-data-what-joke-generator-that-is.html)
and [detect double entendres](https://www.popsci.com/technology/article/2011-04/thats-what-she-said-software-recognizes-pervy-double-entendres-automatically/).
These programs usually define some rules that constitute a funny joke, and then fill in the slots randomly.
For example, the [STANDUP punning riddle generator]((http://joking.abdn.ac.uk/webversion/welcome.php)) might generate a joke like:

> What is the difference between a pretty glove and a silent cat?
>
> One is a cute mitten, the other is a mute kitten.

To create such a joke, the generator uses templates.
Template can be seen as sentences with holes, which are later filled in by following certain rules.
For example, for the above joke, the template would be the same as the joke, but without the words *pretty*, *glove*, *silent*, *cat*, *cute*, *mitten*, *mute* and *kitten*:

> What is the difference between a **A** **B** and a **C** **D**?
>
> One is a **E** **F**, the other is a **G** **H**.

These holes are then related to each other using rules, which then fill the holes with appropriate words.
For the above template, there are constraints enforcing that **E** and **G** end with the same sound, and so should **F** and **H**.
Similarly, **E** and **H** start with the same sound, and so do **F** and **G**.
To create the question of the riddle, four pairs of synonyms are required, namely **A** should be a synonym of **E**, **B** of **F** and so on.
In a way, the generator is playing [Mad Libs](http://www.madlibs.com/) with itself, but enforcing slightly more logic in the relations between the words.
  
![mopjesbot](mopjesbot_drawing.jpg)

### Teaching joke patterns
  
So while it might be hard to make a computer come up with a broad range of clever jokes completely from scratch,
 we can teach them how to generate specific types of jokes.
However, while many English language resources exist, not all languages possess such plentiful language resources for enforcing and checking linguistic constraints.
Another problem is that most joke generators use static data sources (e.g. an internal dictionary), and are thus unable to create jokes about topics that are not included in this data, unless they are manually updated.
Old joke generators might thus not be able to make jokes about new music artists or politicians.


We created [bot](https://twitter.com/MopjesBot) for generating Dutch *"Kermit de Kikker"* punning riddles, using limited Dutch language resources,
namely [Wikipedia](https://nl.wikipedia.org/), a [thesaurus](https://www.mijnwoordenboek.nl/synoniem.php) (or [Wiktionary](https://nl.wiktionary.org/wiki/Hoofdpagina)),
[rhyming dictionary](https://www.mijnwoordenboek.nl/rijmwoordenboek/) and [hyphenation](https://www.ushuaia.pl/hyphen/?ln=nl).
All these resources tend to be available online for most of the popular languages.
The classic *"Kermit de Kikker"* (*Dutch for [Kermit the Frog](https://en.wikipedia.org/wiki/Kermit_the_Frog)*) joke is based on finding rhymes of *Kikker* based on what the riddle suggest.
For example:

> Het is groen en het plakt?
>
> Kermit de Sticker

In English, this joke says: *"It's green and adhesive? Kermit the Sticker"*.
This is a joke because *"sticker"* is a rhyme of *"kikker"*, Dutch for *"frog"*.
Usually, this joke is followed by a large succession of similar jokes about Kermit, e.g.

> Het is groen en is pyromaan?
>
> Kermit de Fikker

As you might have realised, this is something we can teach computers to generate for us.
But why stick with only making jokes about *Kermit de Kikker* when you can insert any name?
Given the name *Kanye West* as input, it would perform the following steps:

1. [Find a rhyme](https://www.rhymezone.com/r/rhyme.cgi?Word=west&typeofrhyme=perfect&org1=syl&org2=l&org3=y)
on the last word with the same number of syllables, e.g. *rest* .
If the last word of the input has multiple syllables, look for rhymes on any combination of consequent syllables.
Prefer more common words using a word frequency list, if this is available in the language of choice.

2. Replace the relevant syllables of the input name with the rhyme word, e.g. Kanye Rest.

3. Use [Wikipedia](https://wikipedia.org) to find a nice description of the entity with the input name.
This is not that hard to extract from the Wikipedia page, since the introduction usually start with *\[entity_name\] **is/was/are** \[explanation\]*.
By taking the part after the *"to be"* verb, and until any punctuation or start of clause, the program can distill a brief description.
For example, it would describe [Kanye West](https://en.wikipedia.org/wiki/Kanye_West) as *an American rapper*.

4. It now only has to describe the rhyme word to complete the pun riddle.
To achieve this, either a [thesaurus](https://www.thesaurus.com/browse/rest) (for short descriptions),
or segments from [Wiktionary](https://en.wiktionary.org/wiki/rest) (for longer, more interesting descriptions) could be used.
The algorithm should however make sure that the description do not contain the word to guess itself, since that would spoil the fun.
The word frequency table could also be used to choose less common (and thus more specific) descriptive words.
For example, it could describe *rest* as *"relief from work"*.

5. Now it can fill all these words into the the template, to create the following joke:
> It's an American rapper and is relief from work?
>
> Kanye Rest

These jokes tend to become more interesting once you have multiple of them, as they turn into a fun guessing game.
Luckely, given that we completely automated the generation process, the described program can easily generate many more jokes about this person.

We build a Twitterbot, called [MopjesBot](https://twitter.com/MopjesBot), that generates five unique jokes using this schema on a daily basis.
It first checks the news for articles, then filters out articles about too sensitive topics, and finally picks the name that occurs most in these articles.
The complete overview of all steps it follows to generate these jokes are summarised in the diagram below:

![mopjesbot overview](mopjesbot_flow.png)

This system is thus able to generate jokes following a specific template and schema,
but also nudges the jokes to have a higher probability of having certain characteristics (e.g. common or less common words in certain template "holes").
  
### Learning what constitutes a joke

While it's wonderful that we can already make computers generate jokes using templates and schemas, implementing such joke generators requires a large amount of human effort.
The computer is also not really gaining insights into humor itself, but rather the human giving the machine explicit insights into a specific type of joke.

So, could it learn these insights by itself?
This is one task we want to tackle in the future, which can be subdivided in multiple parts:
  - can we automatically extract meaningful relations between words of a good joke?
  - can we find out which jokes are better than others by learning probabilities, and use these to "nudge" the generators into generating better jokes?
  
The former is something we have [explored in the past](https://www.researchgate.net/publication/325432136_Automatic_Joke_Generation_Learning_Humor_from_Examples), and are still actively investigating.
The latter task could be achieve using preference learning.
[Preference learning](https://en.wikipedia.org/wiki/Preference_learning) is a task where given a set of two data points, the algorithm has to predict which one is preferred by a human.
This could then be used to find optimal parameters to contruct a joke that a particular user or group of users might like.

The future of automatic joke generation is thus exciting, and still full of opportunities.
We can already create joke generation algorithms by hand and getting close to learn them automatically.
In the future, we might not need to listen to pre-written jokes told by Siri any more, and instead could enjoy personalised, generated humor.
Or, as our algorithm might say:

> It's a branch of artificial intelligence which uses computers in humor research and is a claim of questionable accuracy?
>
> Computational Rumor
