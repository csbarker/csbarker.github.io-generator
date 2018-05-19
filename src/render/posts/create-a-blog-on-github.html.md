---
title: "Create a blog on Github Pages"
cover: '/img/hello-masthead.jpg'
isPost: true
active: true
excerptOther: 'A test post. Vivamus sed laoreet ante, sed pretium justo. Nunc magna nulla, tempus ut felis non, venenatis lobortis lacus. Donec vulputate purus feugiat sapien laoreet, eu placerat est dapibus.'
postDate: 'Fri Jun 05 2015 12:50:54 GMT-0600 (Mountain Daylight Time)'
tags:
 - first post
 - world
 - test
---

One of the cool features of Github is the ability to host static files (html, css, js, images) using [Github Pages](https://pages.github.com/). I have previously used this functionality to host my mini productivity tool [Balance](https://csbarker.github.io/balance/) but I'm eager to use it a more substantial way. 

So lets make a blog!

### Step 1: Setup and validate your work directory

Gotta start somewhere...

```
mkdir my-blog-generator
cd my-blog-generator

npm -v # confirm we have node
git --version # confirm we have git
```

### Step 2: Install your blog generator

Github pages recommends [Jekyll](https://jekyllrb.com/) which is ruby based but I will be using [Docpad](https://docpad.org/) which is node based.

```
npm install -g docpad
docpad init
```

### Step 3: Import a skin (skeleton)

We could start making pages and posts and manually styling/linking everything together but an easier way is to use a pre-built bundle which Docpad calls a [skeleton](https://docpad.org/docs/showcase/#skeletons). I will be using [Casper](https://github.com/docpad/docpad-skeleton-casper).

```
git clone https://github.com/docpad/docpad-skeleton-casper.git
```

This will copy the repos contents into a folder named "docpad-skeleton-casper". Copy the contents of "docpad-skeleton-casper" (excluding the .git folder) into your root working directory (my-blog-generator) and delete the "docpad-skeleton-casper" folder.

Since our skin uses packages that were not in the initial blog generator we will need to install them.

```
npm install
```

Now we can run our blog using the skin/skeleton 

```
docpad run --skeleton casper
```

...and we can see our newly created blog at http://127.0.0.1:9778, woohoo!

### Step 4: Making some changes

The Ghost skeleton bundle is nice but it will  require some changes before we can deploy the blog to production. 

**Config:** Your site and author settings are set in `./docpad.coffee` so you'll definently want to update this file first.

**Posts:** Several placeholder posts are generated in `./src/render/posts` which you'll likely want to remove before deploying. You'll also want to add some i imagine :) PS: Make sure you name your files with `.html.md` and not just `.md `

Note: The docpad run command also starts a file watcher which will regenerate the blogs html so you dont have to keep stopping/starting the generation process.

### Step 5: Deploying 

When you are happy with your blog, stop the run command from your terminal using ctrl+c and push the contents of `./out` to github (making sure the repos name is my-username.github.io where "my-username" is your actual username).
