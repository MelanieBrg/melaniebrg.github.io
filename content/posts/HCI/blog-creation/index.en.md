---
title: "Blog Set Up"
date: 2020-06-08T08:06:25+06:00
description: Step by step tutorial to set up this website
menu:
  sidebar:
    name: Blog Set up
    identifier: blog
    parent: hci
    weight: 30
author:
  name: Mélanie Brégou
  image: /images/author/me.png
math: true
---

As a first assigment of Human Computer Interface class, we had to create a Blog to showcase the work we will do during our master. I created my website using **Hugo**, a fast and modern static site generator. 

Here are the different steps to set up this portfolio :

##### Installation on MacOs

- Open a terminal and type the command `brew install hugo`
- Go the website [Hugo Themes](https://themes.gohugo.io)
- Choose Toha theme and click on the [Github repository](https://github.com/hugo-toha/toha)
- Fork the repository and change the repository name to [your github username].github.io
- Clone the repository 


##### Website personalization
- Once it is cloned open the project in Visual Studio Code
- Modify the **config.yaml** file and set baseURL parameter to https://[your github username].github.io and choose the languages you want to use for the website

- Adapt the template to your needs such as **/data** yaml files for the portfolio page and **/content/posts** for the blog articles.


##### Deployment in Github Pages
- Make sure your repository name is [your github username].github.io
- Create a gh-pages branch typing the command `git checkout -b gh-pages` 
- Push the source branch into Github `git push gh-pages gh-pages`
- Check if the template provide a workflow in **.github/workflows/deploy-site.yaml** 
- Go back to the main branch and push all your changes
- Now your website is accessible on the url https://[your github username].github.io



