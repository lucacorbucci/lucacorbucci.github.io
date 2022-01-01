---
title: Autonomic Farm Pattern
summary: "Parallel and Distributed Systems: Paradigms and Models Final Project (2018-19). Master Degree in Computer Science @ University of Pisa"
tags:
  - University
date: "2018-09-10T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

# image:
#   caption: Photo by rawpixel on Unsplash
#   focal_point: Smart

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/lucacorbucci
url_code: "https://github.com/lucacorbucci/Autonomic-Farm-Pattern"
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---

<em>Tech Stack: C++, FastFlow</em>

This is the final project of the course "Parallel and Distributed Systems: Paradigms and Models" at the University of Pisa.

## Autonomic-Farm-Pattern

### Description

The goal is to provide a farm pattern ensuring (best effort) a given service time leveraging on dynamic variation of
the parallelism degree. The farm is instantiated and run by providing:

- A collection of input tasks to be computed (of type Tin)
- A function<Tout(Tin)> computing the single task
- An expected service time TSgoal
- An initial parallelism degree nw

During farm execution, autonomic farm management should increase or decrease the parallelism degree in such a way its service time is as close as possible to the expected service time TSgoal.
The pattern should be tested providing a collection of tasks such that the tasks in the initial, central and final part all require a different average time to be computed (e.g. 4L in the first part, L in the second part and 8L in the third part) and the task collection execution time is considerably longer than the time needed to reconfigure the farm.
