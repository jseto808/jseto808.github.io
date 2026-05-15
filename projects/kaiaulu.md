---
layout: project
type: project
image: img/kaiaulu/kaiaulu-sq.png
title: "Kaiaulu"
date: 2026-05-12
published: true
labels:
  - Software Engineering Research
  - Data Science
  - R
  - GitHub
  - DV8
  - Open Source
summary: "Contributed to Kaiaulu, an open-source R toolkit for mining and analyzing software repositories, by overhauling its graph construction system and extending tool integrations."
---

<div class="text-center p-4">
  <img width="254px" src="../img/kaiaulu/kaiaulu-logo.png" class="img-thumbnail">
</div>

## Project Summary

[Kaiaulu](https://github.com/sailuh/kaiaulu) is an open-source R toolkit developed at the University of Hawaiʻi at Mānoa for mining and analyzing software repositories. It supports a wide range of data sources, including Git logs, Jira issue trackers, mbox mailing list archives, and third-party static analysis tools like DV8, Understand, and Depends, enabling empirical software engineering research at scale.

## Overview

As part of a research team led by Carlos Paradis (Data Scientist at KBR, Inc., Ph.D. in Computer Science from UH Mānoa), I helped build a pipeline to determine the causal effect of negative sentiment on code contribution in open-source communities. My work focused on extending Kaiaulu's graph infrastructure and tool integrations to support the data collection and network construction stages of that pipeline.

## My Contributions

### S3 Graph Model System

The original codebase built and passed networks inconsistently across analysis functions, requiring callers to manually specify what kind of network they were working with. I overhauled this by introducing two standardized S3 graph constructors:

- **`model_unimodal_graph`**: for networks where all nodes are the same type (e.g., developer-developer or file-file networks)
- **`model_multimodal_graph`**: for networks where nodes belong to two or more distinct types (e.g., author-file or author-commit-file networks), with bipartite graphs handled as a special case via an `is_bipartite` flag

Both constructors encode graph properties (direction, weight, and node structure) directly into the S3 class vector, so downstream functions can dispatch on them without any manual specification from the caller.

I then refactored core analysis and projection functions throughout the package to use S3 generic dispatch, so they automatically detect the type of network they receive and handle it correctly, removing the need for callers to pass that information manually each time.

### Custom Edge Weight Parameters

I added `weight` and `weight_agg` parameters to Kaiaulu's network transform functions, enabling graphs to be weighted by any column in the underlying edgelist rather than just co-occurrence counts. In practice this allows networks to be weighted by sentiment and emotion scores derived from developer communication (e.g., mailing list or issue comment data), opening up affective network analysis in addition to structural analysis.

### Extended DV8 Integration

I extended Kaiaulu's integration with DV8, a third-party architecture analysis tool, to handle more complex nested data structures, specifically parsing DV8 cluster hierarchies recursively rather than assuming a flat structure. I also parameterized DV8 filenames throughout the pipeline so that different DV8 outputs can be targeted without hardcoding paths.

### New Vignettes

I added three new R Markdown vignettes to the package:

- **DV8 Author Communication Showcase**: demonstrates combining DV8 architecture data with developer communication networks weighted by emotion scores
- **Custom Graph Weight Showcase**: walks through using the new `weight` and `weight_agg` parameters to build sentiment- and emotion-weighted networks
- **Radio Silence Showcase**: demonstrates detecting periods of communication inactivity within developer networks

## What I Learned

Working on Kaiaulu gave me hands-on experience with R's S3 object system, including how to design generic functions that dispatch on class to achieve clean polymorphic behavior without formal class hierarchies. It also deepened my understanding of empirical software engineering research and how version control history, issue trackers, mailing lists, and static analysis tools can be combined into unified network representations to study how software teams work. Contributing 51 commits to an active research tool reinforced the importance of designing consistent, well-documented APIs that other researchers can build on.

Source: <a href="https://github.com/sailuh/kaiaulu"><i class="large github icon "></i>sailuh/kaiaulu</a>
