---
title: "Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines"

summary: Implementation of all the milestones of the Big Data Analytics course
tags:
  - University
date: "2021-01-14T00:00:00Z"

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
url_code: "https://github.com/lucacorbucci/BigDataAnalytics"
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

<em>Tech Stack: Python, Matplotlib, Pandas, Keras, Streamlit, Docker</em>

[The repository](https://github.com/lucacorbucci/BigDataAnalytics) contains all the milestones implemented during the course "Big Data Analytics" @ the University of Pisa. The team that worked on this project is the "MaLuCS" team which was composed by:

- Luca Corbucci
- Cinzia Lestini
- Marco Giuseppe Marino
- Simone Rossi

The goal of course was to develop a big data analytics project. The projects were based on real-world datasets covering several thematic areas.

The project is divided into 3 main milestones:

- Data Understanding and Project Formulation
- Model(s) construction and evaluation
- Model interpretation/explanation

At the end of each of these milestones, we presented our results and we wrote a report. At the end of the course, we developed a final notebook to show the results reached during all the midterm.

## Folder structure

There is a folder for each Midterm, in each of these folders you can find a Jupyter Notebook, a dataset and the slides of the presentation.
There is a folder called "Final Term" that contains the final notebook and the code of the Streamlit web app.
There is a folder called "Report" which contains the report we wrote for the exam.

## Final Term

### Notebook

Inside the Jupyter notebook you can find all the most important task of our project:

- Data Cleaning: this part was developed during the first Midterm.
- Prediction: this part was developed during the second Midterm.
- Explanation: this part was developed during the third Midterm.

### Streamlit

We developed a simple web app using Streamlit to visualize our work.

In the web app, you can upload the sample dataset and then you will see the same pieces of information that you can compute in the notebook.

In the bottom of the page, you can select an instance of the dataset to see the explanation.

You can visualize the web app using this link: http://62.171.188.29:8501/.

Alternatively, you can host on your own computer, we used Docker to simplify the execution of this service:
Run Streamlit using Docker

Run docker-compose up in your terminal to run src/main.py in Streamlit, then open localhost:8501/ in your browser to visualize our project.
