---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "ML Student Projects: Dots-and-Boxes"
subtitle: ""
summary: ""
authors: ["wannes", "hendrik"]
# Add tags for all research topics you think are relevant:
tags: ["Master student", "Master course", "Education"]
# Uncomment your categories:
categories: [
"Games",
]
date: 2019-11-30T11:18:29+02:00
lastmod: 2020-04-30T11:18:29+02:00
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

This games was explored in the course "Machine Learning: Project" (Prof. Hendrik Blockeel, Dr. Wannes Meert).
Students developed agents that are able to play the Dots-and-Boxes game.

The game implementation is available at https://github.com/wannesm/dotsandboxes (and can be played interactively).

{{< figure src="dotsandboxes.png" >}}


### Rules of the game

> Starting with an empty grid of dots, two players take turns adding a single horizontal or vertical line between two unjoined adjacent dots. The player who completes the fourth side of a 1×1 box earns one point and takes another turn. (A point is typically recorded by placing a mark that identifies the player in the box, such as an initial.) The game ends when no more lines can be placed. The winner is the player with the most points. The board may be of any size. When short on time, a 2×2 board (a square of 9 dots) is good for beginners. A 5×5 is good for experts.
> ([Wikipedia](https://en.wikipedia.org/wiki/Dots_and_Boxes))

{{< figure src="dotsandboxes2.png" width="300px" >}}



> While the game has very simple rules, it has a large number of possible states (more speciﬁcally, 
 $|S| = 2^{r(c+1)+(r+1)c}$ states for an $r \times c$ game), and an even larger number ($\log_2(|S|)!$) of unique games can be played. No general strategy for optimal play is known. Currently, a 4 × 5 game is the largest game that is solved.
> (Barker, J. K. and Korf, R. E. Solving dots-and-boxes. AAAI 2012)

### Agents

The agents available in the Dots and Boxes demo are developed by students from the Master of Computer Science at KU Leuven as part of the 2017-2018 course Machine Learning Project, taught by Prof. Hendrik Blockeel and Wannes Meert.

The machine learning technologies used in the agents are:

- Monte-Carlo Tree Search to simulate game-play
- Q-learning to learn about good actions
- Artificial Neural Net / Deep learning to learn about good board states
- Logic rules to reason about domain specific concepts such as ‘chains’ and ‘sacrificing'

### Credits

Hendrik Blockeel, Wannes Meert, Pieter Robberechts, Arne De Brabandere and Sebastijan Dumančić contributed to this course.

