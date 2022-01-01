---
title: ESPWeatherStation
summary: Homemade temperature sensor
tags:
  - Personal
date: "2019-10-01T00:00:00Z"

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
url_code: ""
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

<em>Tech Stack: Python, MQTT, MongoDB, Flask, Docker, Flutter</em>

This is a personal project I've developed using a NODEMCU (ESP88266) and a temperature sensor DHT22.
The sensor detects the temperature and sends the data to a RaspberryPi using MQTT.
The RaspberryPi stores the data in a local database and then sends the data to a VPS.
On the VPS the temperature data is stored in a database and I developed a Flask API to access them.
I'm currently using Flutter to visualize the data.
