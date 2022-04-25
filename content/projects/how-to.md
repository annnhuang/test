---
title: "How to Build Your Own Website Using Hugo, GitHub, and Netlify"
lead: At last! Finally built a blog I like using Hugo, GitHub and Netlify 😎
date: 2022-04-22
toc: true
tags:
  - "Development"
  - "Tutorial"
categories:
  - "Projects"
  
# Theme-Defined params
comments: false # Enable Disqus comments for specific page
authorbox: true # Enable authorbox for specific page
toc: true # Enable Table of Contents for specific page
mathjax: false # Enable MathJax for specific page
socialshare: false # Enable social share links after post for specific page
autonumbering: true # Enable Autonumbering of sections and subsections for specific page
thumbnail: "" # Thumbnail to be displayed with Post Title
---

Here are 5 simple steps to creating your own website using [Hugo], GitHub and Netlify on a Mac. This tutorial assumes that you have the following: 1) a [GitHub account], 2) [Netlify account], and 3) [Git].

## Step 1 Install necessary packages and programs

Open terminal, and follow instructions on the official documentation to install the pacakge manager [Homebrew]. Once you have sucessfully installed Hombrew, type: `brew install hugo` in your terminal.

```
brew install hugo
```
Type `which hugo` to check if it has been sucessfully installed. Also type `hugo version` to check its version. 

## Step 2 Create a new site

On terminal, navigate to the folder where you wish to store/host your site locally. To do this you could first check where you are in the directory by typing `pwd`, then simply type `cd` to change to the desired location. There, create a new site by typing `hugo new site [insert_your_site_name_here]`. For example:

```
hugo new site anotherblog
```
This command generates a static site folder named "anotherblog" inside my home directory.

## Step 3 Pick a theme and use it

Choose a [hugo theme]. Navigate to its GitHub Repo by clicking the "Download" button. These Hugo themes usually come with a README file that instructs you the best way to install the theme, e.g. using `git clone` or `git submodule add`. The theme I am using is called [Mainroad].

[Mainroad]: https://github.com/Vimux/Mainroad

![Alternate Text](/img/mainroad_page.png)

On Terminal, navigate to the root directory of the site you've created (e.g. type `cd anotherblog`). Once you are inside, copy and paste the link copied from Github and install the theme by running `git submodule add [url_to_the_theme]`. For me, it looked like the following:

```
git submodule add https://github.com/vimux/mainroad.git themes/mainroad
```

Once it is installed, use any source code editor, e.g. Atom or Visual Studio Code to open and make changes to the hugo site ("anotherblog") you have created just now. You should see the default folders including `archetypes`, `content`, `static`, etc. Importantly, you should see the theme you have downloaded in the `themes` folder. Then find and click on the `config.toml` file, and type the name of your theme:

```
theme = "mainroad"
```

You may preview the site locally by running:

```
hugo server
```
You should see that the web server is available at //localhost:1313/. Copy and paste it into your brower to preview.

![Alternate Text](/img/hugo_server.png)

You may create a post or do whatever you’d like to your new site. You could follow the `exampleSite` included in the `themes/mainroad` folder. For example, try copying the `about.md` file and paste it inside the `content` folder underneat `archetypes`. You should see an “About” page on the local web server.

## Step 4 Link your site to GitHub.

Before committing and pushing the changes to Github, create a submodule path in `.gitmodules`. In the home directory of your site, simply click create new file, and name it `.gitmodules`. Inside my `.gitmodules` file looks like this:

```
[submodule "themes/mainroad"]
    path = themes/mainroad
    url = https://github.com/Vimux/Mainroad.git
```

This is an important step because it creates a mapping reference to the source repository, which will later allow a successful deployment via Netlify. For more information see this [post] on Stack Overflow.

Go to your GitHub account, and create a repository with a name you want. Then follow instructions on GitHub to link the repository to the local folder.

![Alternate Text](/img/github_creat_repo.png)
![Alternate Text](/img/repo_instruct.png)

Essentially, you'd want to push your hugo site to the Github repo. Below are some quick keys I use to track the changes I've made, commmit them and push them onto the GitHub repo using the `git` command. More tips on how to use Git can be found [here].

```
Git init
Git remote add origin [url_of_your_site_on_GitHub]
Git status
Git add .
Git commit -m “changes made first time”
Git push origin master
```

## Step 5 Continuous Deployment via Netlify

Publish your site using Netlify by following the simple steps presented on the Netlify page. Essentially it links the Github repos of your hugo site and makes a continuos deployment out of it. Everytime you make changes in your code editor, just make sure to always add, commit and push (using `git`) all the changes to the Github repo.

### Have fun!

[GitHub account]: https://github.com/
[Git]: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
[Netlify account]: https://www.netlify.com/
[Hugo]:https://gohugo.io/documentation/
[Homebrew]: https://brew.sh/
[hugo theme]: https://themes.gohugo.io/
[post]:https://stackoverflow.com/questions/53625208/failing-to-deploy-website-on-netlify-when-trying-to-use-alternate-hexo-theme
[here]: https://www.earthdatascience.org/workshops/intro-version-control-git/basic-git-commands/