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
4.  When I am happy with my new blogpost I merge the changes in the main branch of my GitHub repo
5.  A GitHub Action runs when new changes are pushed on the main branch generating the new version of the public website and deploys it to GitHub Pages

Not bad ha?

If you like it, and you are still reading, in the next section you can find out the ingredients needed for this recipe.


### First ingredient: [Hugo](https://gohugo.io/), the static site generator {#first-ingredient-hugo-the-static-site-generator}

Nothing to say about it, it just works out of the box.

Furthermore [here](https://themes.gohugo.io/) there are several free cool themes available that you can use to style your static website without too much work.


### Second ingredient: [ox-hugo](https://ox-hugo.scripter.co/), a way to produce a Hugo compatible markdown file starting from an org file {#second-ingredient-ox-hugo-a-way-to-produce-a-hugo-compatible-markdown-file-starting-from-an-org-file}

Here is where the magic happens, this emacs package allows to `org-export-dispatch` the org file into a Hugo compatible markdown file.

Nothing too complex to setup this package, here is the snippet needed (for `use-package` users), you just have to add it to your emacs configuration

```emacs-lisp
(use-package ox-hugo
    :straight t
    :after ox)
```

No other complex things to do to make these two working together, really I just followed this [Quick Start](https://ox-hugo.scripter.co/doc/quick-start/) to setup my first project and everything worked without any issue.

In any case you will end up having one or multiple org files that will contain the source text for your blog posts.


### Mixing together {#mixing-together}

We are almost there, bear with me!

Start the Hugo server within a shell with the following command

```bash
hugo server --buildDrafts --navigateToChanged
```

Edit the source files to update your blog posts.

Export the content via `org-export-dispatch` and let Hugo render the new content 🧑‍🍳😙🤌.


### The last ingredient: the GitHub Action {#the-last-ingredient-the-github-action}

If you plan to version your blog post code on GitHub serving it through GitHub Pages this might be the last piece of the puzzle.

It's fairly easy to setup a dedicated GitHub action that generates and deploys the new version of your static blog post when new changes are pushed to the main branch.
If you want to do it just follow the new workflow creation in GitHub.

A blueprint for Hugo is already available and works out of the box.

And that's it! You are all set up 🎉.

I hope that you can start blogposting from emacs too 🦾.

Cheers!
