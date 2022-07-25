---
title: ChatterBox
summary: Operating System Project (2016-17). Bachelor Degree in Computer Science @ University of Pisa.
tags:
  - University
date: "2016-07-27T00:00:00Z"

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
url_code: "https://github.com/lucacorbucci/ChatterBox"
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

<em>Tech Stack: C</em>

**Operating Systems and Laboratory** Project @ Unipi.
Academic year 2016/2017.

The text of the project is available here: http://didawiki.di.unipi.it/doku.php/informatica/sol/laboratorio17/progetto and in the "Testo Progetto" folder in the repo.
A final report is available in the "Report" folder.

### How to try Chatterbox

To test the project:

```
git clone https://github.com/lucacorbucci/ChatterBox.git
cd Chatterbox
make
```

Then you can launch the server using the command:

```
./chatty -f ./DATA/chatty.conf1
```

You can run the client using the following command:

```
./client -l /tmp/chatty_socket -c luca
```

There are some flags useful to configure and use the client.

### Test

In the folder Test you can find some tests that can be used to try the Project.
