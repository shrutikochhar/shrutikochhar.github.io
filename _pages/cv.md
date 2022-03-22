---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

I am a final year Ph.D. student at the University of British Columbia working on computational genomics. I am currently looking for internship/part time contract roles (with a possibility for extension) in Computational Biology, Machine Learning, Data Science and Software Development.

Education
======
* Ph.D. in Electrical and Computer Engineering (<span style="color:#2C4381">Thesis: Computational Models for Genomic Representations)</span>, The University of British Columbia, Vancouver, 2022 (expected)
* M.A.Sc. in Electrical and Computer Engineering, The University of British Columbia, Vancouver, 2022
* B.Tech. in Electronics and Communication Enginnering, National Institute of Technology Karnataka, India, 2017 

Work experience
======
* ## Ph.D. Research Assistant, The University of British Columbia <span style="color:#2C4381">(Jan 2019 - Current)</span>
  * Currently working on building representations for the genome, mainly epigenomic and Hi-C representations 
  * My thesis aims to unify recurrent and graph neural networks for learning representations of epigenomic signals (<a href="https://kevinbdsouza.github.io/publication/epilstm"><u>published work</u></a>) and 3D genome organization (<a href="https://kevinbdsouza.github.io/publication/hiclstm"><u>submitted work</u></a>)
  * The representations from our models are useful for a variety of tasks like pan-celltype element identification, novel element detection, transfer learning to unseen cell types, inference of 3D chromatin structure, and in-silico modifications.
  * The software for my research is written mostly in Python using PyTorch and CUDA extensively. The software packages resulting from this work are avaialale on <a href="https://github.com/kevinbdsouza"><u>GitHub</u></a>. We are working on cloud based deployment using GCP/AWS for future releases.
  * **Supervisor**: Prof. Maxwell Libbrecht (<a href="https://www.libbrechtlab.com"><u>Libbrecht lab</u></a>) and Prof. Vijay Bhargava

* ## Machine Learning Intern, Skycope Technologies <span style="color:#2C4381"> (May 2018 - Sep 2018)</span>
  * Built Skycope's data and machine learning infrastructure 
  * Set up Skycope's database server and backend MySQL software for data extraction and manipulation 
  * Modified Faster-RCNN, an existing object detection framework, to successfully detect and locate drone signals in the spectrogram (<a href="https://kevinbdsouza.github.io/publication/frcnn"><u>published work</u></a>)
  * Integrated ML software into Skycope's existing software stack 
  * Skycope is now using this as their flagship service in their automatic drone detection software
  * **Supervisor**: Hamidreza Boostanimehr

* ## M.A.Sc. Research Assistant, The University of British Columbia <span style="color:#2C4381"> (Sep 2017 - Dec 2018)</span>
  * Adopted deep learning frameworks for signal detection and developed hybrid precoding schemes for sequential data
  * Used Python, PyTorch, and CUDA for deep learning. Hybrid precoding schemes were developed in C and MATLAB.
  * **Supervisor**: Prof. Vijay Bhargava

  
Skills
======
* Coding 
  * Python, R, C, C++, Linux, Git, MySQL, PostgreSQL
* Machine Learning 
  * Deep Learning, Sequential Models, Representation Learning, Statistics, Regression, Random Forests
* ML tools 
  * PyTorch, GCP, CUDA, AWS, BigQuery, Numpy, Pandas, Scipy, Scikit-learn, Jupyter
* Data Science 
* Bioinformatics
* Software Development 
* Biology 
  * Chromatin Structure, Epigenomics, RNA-seq


Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service 
======
* Joint-Secretary at Autism Society of Udupi (ASU)
  * ASU is a non-profit organisation in Udupi, India, that aims to create awareness about Autism among parents, teachers, health professionals, students, general public and all the stakeholders so that early diagnosis and early intervention could give the child maximum benefits. 
  * Currently working alongside primary schools to educate teachers about autism. Partnering with various organisations working towards similar causes. 
* Mentor at Climate Hub, UBC
  * The UBC Climate Hub aims to connect university and community stakeholders to take bold climate action for a just and equitable future.
  * Worked with undergraduate students to find interdisciplinary climate solutions and contribute to climate awareness.
* Mentor at iGEM, UBC
  * The International Genetically Engineered Machines (iGEM) Competition aims to produce organisms with unusual properties to tackle modern problems using synthetic biology. 
  * Worked with undergraduate students to a transcription-based biosensor to detect levels of saxitoxin, a toxin responsible for paralytic shellfish poisoning in humans. 
* Volunteer at Lets Talk Science
  * Mentored high school students to inculcate in them aptitude and curiosity towards science.
* Volunteer at Geneskool, Genome BC
  * Conducted workshops on the basics of genetics, traits and phenotypes for elementary grade students.
