# Data Working Group Website

This is the repository for our website available [here](https://health-data-working-group.github.io/). It is currently deployed on GitHub pages using the [Hugo DPSG](https://github.com/pfadfinder-konstanz/hugo-dpsg) theme.

## How to Contribute

Here are some instructions on how to deploy any newly added content to the website. There are two ways to do so: using `blogdown` (R package) or using `hugo` via Terminal.

### Using `blogdown`

1. In R or RStudio, make sure that you install the `blogdown` package using the following commands:

```{r}
install.packages("blogdown")
blogdown::install_hugo()
```

2. Any content to the website needs be added via the `/content` folder. All pages are written in Markdown and then rendered to HTML. Here is an example:

```{markdown}
---
title: Example webpage
authorbox: false
sidebar: false
---

# This is a header!

This is an example page for our amazing website.
```

To create a page which contains potentially multiple posts, you can create a directory within `/content/page_with_many_posts` and add your markdown files there.

3. Once you have added your edits, go to your local repository directory in your R console using `setwd()`. Your command should look something like `setwd("some_directory/health-data-working-group.github.io")`.

4. Run the following `blogdown` commands to build the website:

```{r}
blogdown::build_site()
```

Now your rendered site should be available in `/public`.

5. **Super sketchy step** <sub><sup>(that works...)</sup></sub> Because GitHub pages can search for a folder called `/docs` but Hugo renders files into `/public`, one method that works (but probably not what Hugo was initially designed for) entails copying and pasting files from one folder to another. You can do this using the following R commands (in the repository folder):

```{r}
unlink("docs", recursive = TRUE) # removing docs folder
dir.create("docs") # creating new docs folder
file.copy(from="public", to="docs", overwrite=TRUE, recursive=FALSE)
# ^adding everything from public to docs
```

6. Run git add, git commit and git push.

I don't know how to do this in R. @Kuan, can you write something here? You can also put a photo to show where to click in the RStudio console.

### Using Terminal

