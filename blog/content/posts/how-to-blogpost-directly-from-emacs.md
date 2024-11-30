+++
title = "how to blogpost directly from emacs"
author = ["visd0m"]
categories = ["emacs"]
draft = false
+++

## Why even do that? {#why-even-do-that}

If you like emacs and you are an emacs user at a certain point in your life you will reach that moment in which you try to do as much as you can directly from emacs.

No easy explanation on why this happens, but I give you my personal view on it.

One start using a version of emacs that is far from being the perfect version of emacs for him.

Using it day by day you start customizing it and extending it making it fit your workflows and your needs.

This create the following positive loop:

-   "I am not able to do X with emacs"
-   "I have fun customizing emacs in order to do X with emacs"
-   "I end up having a good enough workflow of doing X in emacs"
-   "I get used of doing X in emacs"

Replace X with blogposting and you have your answer.


## How to blog post from emacs {#how-to-blog-post-from-emacs}

Ok, here is my workflow.

1.  I write my post in an org file (emacs users love org files 🦄)
2.  I export my org file to a Hugo compatible markdown file
3.  The local running hugo server automagically renders the new version of the blog post
4.  When I am happy with my new blogpost I merge the changes in the master branch of my github repo
5.  A GitHub Action runs when something is pushed on master generating the new version of the public website and deploys it to GitHub Pages

Not bad ha?

If you like it, and you are still reading, in the next section you can find out what is needed in order to reach this workflow.


### A static site generator: [Hugo](https://gohugo.io/) {#a-static-site-generator-hugo}

Nothing to say about it, it just works out of the box.

Furthermore [here](https://themes.gohugo.io/) there are several free cool themes available that you can use to style your static website without too much work.


### A way to produce a Hugo compatible markdown file starting from an org file: [ox-hugo](https://ox-hugo.scripter.co/) {#a-way-to-produce-a-hugo-compatible-markdown-file-starting-from-an-org-file-ox-hugo}

Here is where the magic happens, this emacs package allows to `org-export-dispatch` the org file into a Hugo compatible markdown file.

Nothing too complex to setup this package, here is the snippet needed to add it to your emacs-configuration using `use-package`

```emacs-lisp
(use-package ox-hugo
    :ensure t
    :pin melpa
    :after ox)
```

No other complex things to do to make these two working together, really I just followed this [Quick Start](https://ox-hugo.scripter.co/doc/quick-start/) to setup my first project and everything worked without issues.

You will end up having one or multiple org files that will contain the source text for your blog posts.
You can edit the source file freely, export the content via `org-export-dispatch` so that Hugo server can render the new content.


### The last piece of the puzzle: the GitHub Action {#the-last-piece-of-the-puzzle-the-github-action}

If you plan to version you blog post code on GitHub and serve it through GitHub Pages this might be the last piece of the puzzle.

It's fairly easy to setup a dedicated GitHub action that generates and deploys the new version of your static blog post when new changes are pushed to the main branch.
If you want to do it just follow the new workflow creation in GitHub.

A blueprint for Hugo is already available and works out of the box.

And that's it! You are all set up 🎉.

I hope that you can start blogposting from emacs too 🦾.

Cheers!
