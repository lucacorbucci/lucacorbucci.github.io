---
title: SmartAuctions
summary: Final Term - Peer to Peer Systems and Blockchains (2018-19). Master Degree in Computer Science @ University of Pisa .
tags:
  - University
date: "2016-04-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

# image:
#   caption: Photo by rawpixel on Unsplash
#   focal_point: Smart

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/georgecushen
url_code: "https://github.com/lucacorbucci/SmartAuctions"
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

<em>Tech Stack: Solidity, React</em>

[This repo](https://github.com/lucacorbucci/SmartAuctions) contains the final term and the final project developed for the "Peer to Peer Systems and Blockchains" course.
I developed this in June 2019.

A demo of the final project is available [Here](http://116.203.183.105:5000), you need to install metamask to use the site and to do the calls to the contracts.

### Contracts

In the "Contracts" folder there is the final term of the course, i put here the contracts written in Solidity.
There are two contracts, one for the english Auction and one for the Vickrey Auction.
Into the folder "Contracts" there is another readme where i explain the methods of the contracts and how to deploy it using Truffle.

### Frontend.

In the "Frontend" folder there are a lot of files, i put here the auction contracts and also another contract that i wrote in solidity to store in the blockchain the address of the deployes contracts.
I also changed the original Vickrey and English auction contracts based on the calls that i need to do from the frontend.
There are also all the components that i wrote to build the frontend of the distributed application.
For the frontend i used React and Bulma as CSS Framework.
