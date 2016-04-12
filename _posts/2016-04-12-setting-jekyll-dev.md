---
layout: post
title: How to Setup a Jekyll Development Environment on OSX
summary: A guide on setting up a jekyll development environment on OSX.
---
## Introduction

When I first wanted to create a blog, I had a few requirements. I wanted...

* cheap - if not free - hosting,
* the ability to host dynamic webpage on it,
* and it to be easy to post and make changes to it.

With these requirements in mind, I set out to look for solutions that would fit them. When I arrived I was overjoyed as it met every one of my requirements. However, it only allows static HTML and - something I hadn't heard about before - Jekyll. I knew that HTML wouldn't be suitable as I would have to keep rewriting each page. That left me with the other choice, Jekyll (I explained what Jekyll is in my [first](https://blog.koga.tech/2016/03/29/up-and-running/) blog post). The guide below tell you how to set one up for yourself on OSX.


## Installing Dependencies

Jekyll requires several dependencies to run so before we can do anything, we will have to install them. In fact, setting up the dependencies makes up for most of this tutorial! The first thing you will need to do is ensure that __Xcode Command Line Tools__ is installed. 

{% highlight shell%}
xcode-select --install
{% endhighlight %}

Ruby should be preinstalled on OSX systems but we want to update it. To do that we first need to install [Brew](http://brew.sh/).

{% highlight shell%}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Now we use brew to install rbenv - a ruby environment manager - which we will finally use to update Ruby.

{% highlight shell%}
brew install rbenv ruby-build
{% endhighlight%}

We will have to add rbenv to our `.bash_profile` so it loads every time a terminal is opened. The `source ~/.bash_profile` command executes your ~/.bash_profile so you won't have to open a new window.

{% highlight shell%}
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile
{% endhighlight%}

Now we can finally install ruby itself. I have commented on the commands to help you understand what each one is doing.

{% highlight shell%}
rbenv install 2.3.0 # Install the latest version of ruby at the time of writing
rbenv global 2.3.0  # Change the global ruby version to the one we just installed
ruby -v             # Check the version of ruby just in case
{% endhighlight%}

We will need RubyGems - ruby's package manager which was installed automatically by rubyenv - to be updated. In the event it wasn't, you can manually install it [here](https://rubygems.org/pages/download).

{% highlight shell%}
sudo gem update --system
{% endhighlight%}

Some guides suggest installing bundler but I haven't really needed it so far. If you want to though, it is fairly straightforward.

{% highlight shell%}
sudo gem install bundler
{% endhighlight%}

Finally, we have to install node.js - an open source, cross-platform runtime environment for developing server-side and networking applications - using brew, then we can move on to install Jekyll itself.

{% highlight shell%}
brew install node
{% endhighlight%}

## Install Jekyll

Installing Jekyll is actually a very simple process now that we have all our dependencies setup.

{% highlight shell%}
sudo gem install jekyll
{% endhighlight%}

You can verify the Jekyll has been installed successfully easily.

{% highlight shell%}
jekyll --help
{% endhighlight%}

## Creating a project

Now we are going to create a blank Jekyll template to work with, this can be done in any directory of your choosing though I chose to do mine in my Desktop. The project which will be created is called my-new-blog in this tutorial though you can choose any name you want.

{% highlight shell%}
cd ~/Desktop
jekyll new my-new-blog
{% endhighlight%}

Lets `cd` into our new project and serve it up. What this means is that we will use the `jekyll serve` command to start Jekyll's builtin development server.

{% highlight shell%}
cd my-new-blog
jekyll serve
{% endhighlight%}

Our project can now be viewed from the device where you installed Jekyll at [http://localhost:4000](http://localhost:4000).

![img-1](/images/posts/setting-jekyll-dev/img-1.png)

## File Explaination

`config.yml` is the configuration file in your jekyll build.

`_include/` is the folder that contains the parts of your pages (Jekyll pages are usually made up of snippets of html).

`_layouts/` is the folder that contains your page layouts (note you have to create them). For example, `index.html` uses the layout `default`.

`_posts/` is the folder that contains your posts. It uses the layout `post`.

`_sass/` is the folder that contains the SASS stylesheets.

`_site/` is the folder into which Jekyll builds.

`about.md` is an example about page included by Jekyll. Note that pages in Jekyll can be markdown or HTML.

`css/` is the folder that contains the css.

`feed.xml` is an example post feed.

`index.html` is an example... _index.html_.

## Going further

This post just skims the surface of what Jekyll can do. I included a list of websites which explain everything in greater detail and can hopefully help you more. As always, if you have any trouble just email me at [therealkoga@gmail.com](mailto:therealkoga@gmail.com)!

* [https://jekyllrb.com/docs/home/](https://jekyllrb.com/docs/home/)
* [https://scotch.io/tutorials/getting-started-with-jekyll-plus-a-free-bootstrap-3-starter-theme](https://scotch.io/tutorials/getting-started-with-jekyll-plus-a-free-bootstrap-3-starter-theme)
* [https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)