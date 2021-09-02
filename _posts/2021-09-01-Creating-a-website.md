---
toc: true
layout: post
description: Using GitHub Pages and fastpages to make this blog.
categories: [github,fastpages]
title: Creating the Python Club website
---

# Birth of the Python Club website

The goal is to set up a simple website, in the form of a blog, to keep tracks of the various subjects that we discuss at our weekly Python club. 

A beginner-friendly solution would be to use the [Google Sites](https://sites.google.com/new?tgif=d) graphical-user interface to generate the site and add contents. This is convenient for any static websites where you want to present yourself (CV, lists of projects, ...) or your research group / company. 

For our Python club, I preferred a slightly more tech-savvy approach based on GitHub Pages and the fastpages project. I was attracted to this solution by the prospect of effortlessly transforming the Jupyter notebooks used for our club presentations into html contents.

# From Jupyter notebooks to html contents

What we produce in the Python club are Jupyter notebooks, which are JSON-formatted files. To display the notebooks on this blog, we need to convert these files into html and host the contents to be publicly available on the web. All these daunting tasks are going to be performed freely by: 
- [GitHub pages](https://pages.github.com/)
- [Jekyll](https://jekyllrb.com/)
- [fastpages](https://github.com/fastai/fastpages)

The idea, explained in fastpages website, is as follows. 
GitHub Pages hosts the contents of our website as a GitHub repository (check [our repo](https://github.com/SylvainDLDK/PythonClub)) and will send it to any Pythonistas wishing to access our website through their web-browser at [https://SylvainDLDK.github.io/PythonClub](https://SylvainDLDK.github.io/PythonClub). 

When we add a new notebook to the repository, a workflow designed by the pastpages project is automatically started as a GitHub Action. This will first convert the notebooks into a markdown file (using [nbdev](https://nbdev.fast.ai/index.html)), and then run a Jekyll script to transform it in a website. 

## Adding blog posts

A nice feature of pastpages is that it automatically convert jupyter notebooks (or .doc file) into blog posts (Markdown .md file), which are then transformed into html with Jekyll. Just drop you notebook into the /notebooks folder. 
You can also directly write the post as a .md file in /posts.
