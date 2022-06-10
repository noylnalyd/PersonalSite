---
title: Simulated Annealing TSP Solver
summary: An iterative and parallelized approach to high-node TSP.
tags:
  - Algorithms
date: '2016-04-27T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/georgecushen
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---

The Travelling Salesman Problem (TSP) is a famous problem in computer science with a challenging time complexity. The task is to find a shortest path that (1) Starts at a node and (2) Passes through all nodes in (3) The least amount of cost/time/distance. Originally posed for the travelling salesmen and the post office, the problem has widespread applicability including traffic design, printed circuit boards, and X-ray analysis.

TSP has an NP-complete runtime, so short of a miraculous discovery, the computational time for TSP scales exponentially with the number of nodes. A dynamic-programming approach can smartly reduce the complexity to $n^2 \cdot 2^n$
