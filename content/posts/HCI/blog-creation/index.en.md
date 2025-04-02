---
title: "Creating a Portfolio Website with Hugo and Deploying on GitHub Pages"
date: 2023-09-23
description: Step by step tutorial to set up this website
menu:
  #sidebar:
  #  name: Portfolio Set up
  #  identifier: blog
  #  parent: hci
  #  weight: 10
hero: blog.png
author:
  name: Mélanie Brégou
  image: /images/author/me.png
math: true
---

As part of my Human-Computer Interface class, I was tasked with creating a blog to showcase my work during my master's program. I opted to build my website using Hugo, a fast and modern static site generator. In this guide, I will walk you through the steps to set up your own portfolio website using Hugo and deploy it on GitHub Pages.

Here are the different steps to set up this portfolio :

##### Installation on MacOs

- Open a terminal and execute the following command to install Hugo using Homebrew: `brew install hugo`
- Visit the [Hugo Themes](https://themes.gohugo.io) website and choose the Toha theme. Then, access the [Github repository](https://github.com/hugo-toha/toha).
- Fork the repository and rename it to [your GitHub username].github.io
- Clone the repository to your local machine: `git clone https://github.com/[your GitHub username]/[your GitHub username].github.io.git`


##### Website personalization
- Once you have cloned the repository, open the project in Visual Studio Code or your preferred text editor.
- Modify the **config.yaml** file and set `baseURL = https://[your github username].github.io`. Choose the languages you want to use for the website
- Customize the template to suit your needs. You can use YAML files in the **/data** directory for the portfolio page and create blog articles in the **/content/posts** .
- Visualize your website locally with the following command `hugo server -D`


##### Deployment in Github Pages
- Ensure that your repository name is [your GitHub username].github.io
- Create a **gh-pages** branch typing the following command : `git checkout -b gh-pages` 
- Push the **gh-pages** branch to Github : `git push origin gh-pages`
- Check if the template provides a workflow in **.github/workflows/deploy-site.yaml** for automated deployments using GitHub Actions.
- Go back to the main branch and push all your changes
- Your portfolio website is now accessible at https://[your github username].github.io



