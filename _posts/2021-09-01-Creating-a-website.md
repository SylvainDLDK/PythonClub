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

Finally, and this is optionnal, I decided to buy myself a domain name and use it to refer to the Python Club instead of using the GitHub domain name (github.io). There are many providers of domain names, I used [Google Domains](https://domains.google/) to buy sylvaindldk.fr for ~1000 Yen/year. The .jp version was 4 times more expensive! For some reason, the .jp Top-Level Domain (like .fr, .com, .jp) is much more expensive than the .com or .fr. I was perfectly happy with the cheaper French .fr.

After tweeking a few settings, you can now also access the Python Club at [https://pythonclub.sylvaindldk.fr](https://pythonclub.sylvaindldk.fr). 

# Adding blog posts in practice

Just add your jupyter .ipynb notebooks into the /\_notebooks folder, your word .doc files into the /\_word folder, and your markdown .md files in /\_posts. Follow the naming and front matter convention described [here](https://github.com/fastai/fastpages#automatically-convert-notebooks-to-blog-posts) and [there](https://github.com/fastai/fastpages#customizing-blog-posts-with-front-matter). 
