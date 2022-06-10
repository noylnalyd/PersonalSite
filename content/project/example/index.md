---
title: Simulated Annealing TSP Solver
summary: An iterative and parallelized approach to high-node TSP.
tags:
  - Algorithms
date: '2016-04-27T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo from Wikipedia
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

    The Travelling Salesman Problem (TSP) is a famous problem in computer science with a challenging time complexity. The task is to find a path that (1) Starts at a node and (2) Passes through all nodes in (3) The least amount of cost/time/distance. Originally posed for the travelling salesmen and the post office, the problem has widespread applicability including traffic design, printed circuit boards, and X-ray analysis.

    TSP has an NP-complete runtime, so short of a miraculous discovery, the computational time for TSP scales exponentially with the number of nodes. A dynamic-programming approach can smartly reduce the complexity to $O(n^2 \cdot 2^n)$ where $n$ is the number of nodes. For a postman, planning TSP for a modest $n=30$ houses would result in $966$ billion computations.

    But postmen don't care about having the fastest route possible. For that matter, neither do traffic designers or circuit manufacturers. They want practical solutions: A reasonably fast path computed in a reasonable amount of time.

    The solution is to use heuristic methods that approximate the correct solution. Simulated annealing (SA) is one such approach that assigns potentials to solutions and incrementally improves the solution with each iteration. Nodes are assigned a group of neighbors called a $P$-family that are the nearest points in vaguely every direction. For the postal service, your $P$-family would likely be your next-door neighbors on the left, right, and across the street. Simulated annealing generates paths between $P$-family members, and attempts to connect these paths at each iteration in new ways; Improvements are kept and deteriorations are ignored. SA TSP in a brief amount of iterations can generate a path through all nodes that will be fast. SA TSP gets even faster when applied to a problem rooted in geometry: Choosing a $P$-family is obvious when neighbors are just a house away, and simulated annealing reflects that observation.

    For me this project was an exercise in parallelizing code. I used OpenMPI in C++ to parallelize the problem. TSP is readily parallelizable: The positioning of far-away nodes is unlikely to affect nearby paths, so whole parts of the graph can be split between each CPU. OpenMPI allows CPUs to share solution data across these graph partitions.
