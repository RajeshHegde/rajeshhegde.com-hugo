+++
title = "Set up Hugo with GitHub pages"
date = 2016-09-08T08:03:00Z
updated = 2016-09-08T08:03:00Z
blogimport = true 
type = "post"
[author]
	name = "Rajesh Hegde"
	uri = ""
+++

This post briefly describes how to host Hugo blog on GitHub pages.

### What is Hugo?
Hugo is a fast &amp; modern static website engine. Hugo will break the barrier of setting up a web server to create a simple blog.

### What is GitHub pages?
GitHub pages are static set of pages hosted on GitHub.

### Setting up repositories
Create 2 GitHub repository to set up blog in GitHub pages.

1. `<blog-name>-hugo` : For Hugo project
2. `<github username>.github.io` : For hosting the blog

Clone the repo to your local machine using below command
`git clone git@github.com:<username>/<blog-name>-hugo.git`

then setup `<github username>.github.io` as submodule
`git submodule add git@github.com:<username>/<username>.github.io.git`. Whatever the thing goes here can be accessed through `http://<github username>.github.io`.


### Install Hugo
Mac OS X: `brew install hugo`

Linux &amp; Windows : Download binary file and install. https://github.com/spf13/hugo/releases. Hugo includes all dependencies.

### Create blog with Hugo
Lets create a new site for your blog
```
hugo new site <site name>
cd <site name>
```

After creating the new site, you need to edit config.toml configuration file according to your need. My configuration file looks like this.
```
baseurl = "http://rajeshhegde.com"
languageCode = "en-us"
title = "RH.io"
theme = "hyde"
copyright = "Rajesh Hegde"
publishdir = "rajeshhegde.github.io"

[Author]
	name = "Rajesh Hegde"

[Permalinks]
	blog = "/:year/:month/:filename/"
	code = "/:filename/"

[Taxonomies]
	tag = "tags"
	series = "series"
	series-desc = "series-desc"

[params]
	description = "extravaganza of Rajesh Hegde"
	twitter = "https://twitter.com/rajeshphegde"
	github = "https://github.com/RajeshHegde"
	disqus = "rajeshhegde.com"
```
In the above configuration, change `publishdir` to `<github username>.github.io`. Generated HTML will go here. And change the `baseurl` to your site name(`http://<github username>.github.io`).

### Create first page
`hugo new about.md` will create a page in `content/` directory

### Run site locally
`hugo server` will host your blog on `http://localhost:1313`. Content of `about.md` will be available at `http://localhost:1313/about`.

### Deploy site
Let us generate the site using `hugo` which will generate all HTMLs in `<github username>.github.io` directory. This directory need to be pushed to github to be able to access on `http://<github username>.github.io`. 
Since `<github username>.github.io` is a submodule, while pushing any changes to blog use this command `git push --recurse-submodules=on-demand`.

Now your site is available at `http://<github username>.github.io`. Kudos...