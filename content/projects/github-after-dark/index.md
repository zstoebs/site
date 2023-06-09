+++
title = "how to host a Hugo After Dark site on GitHub Pages: a saga"
date = 2021-07-09T23:36:07-05:00
categories = ["personal"]
tags = ["webdev", "html", "hugo", "js", "hack"]
description = "¡¡host fast, pretty website 4 free!!"
summary = "From knowing very little about webdev to a very small amount more, all in one place! The [Hugo hosting docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/) and [After Dark](https://vhs.codeberg.page/after-dark/) tutorial / docs are sufficient but unclear on the finer details. Here, I flesh those out to make this process as easy for prospective users as it truly should be. "
draft = false
toc = true
[schema]
  type = "project"
[[copyright]]
  owner = "Zach Stoebner"
  date = "2021"
  license = "cc-by-nd-4.0"
[[resources]]
 src = "image/thomas-jensen-QABDpFYhNpk-unsplash.jpg"
 name = "thumbnail"
 title = "hugo code"
 [resources.params.meta]
   description = "Hugo template code"
   creator = "Thomas Jensen"
   sameAs = "https://unsplash.com/photos/QABDpFYhNpk" 
   license = "https://unsplash.com/license" 
+++

**tl;dr** From knowing very little about webdev to the bare minimum that you need to know, all in one place! The [Hugo hosting docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/) and [After Dark](https://vhs.codeberg.page/after-dark/) tutorial / docs are sufficient but unclear on the finer details. Here, I flesh those out to make this process as easy for prospective users as it truly should be. 

# Links
[Site source](https://github.com/zstoebs/site)

[Generated source](https://github.com/zstoebs/zstoebs.github.io)

[This site](https://motherfuckingwebsite.com) justifies my <i>perfect</i> website build. 


# How to [Host Hugo](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

Steps to host a Hugo After Dark site on GitHub pages: 
1. Download the quick start code locally from the [After Dark](https://vhs.codeberg.page/after-dark/) website. 
2. Run `hugo` to generate website files in `public/`. 
3. Host the generated files in `public/` on the GitHub pages repo, i.e., a repo named [your username].github.io. 
4. Host the source files in the parent directory in a separate repo, with `public/` ignored. 
	- These are the files at the highest level, mainly Markdown files, that Hugo uses to build the static site. 
5. Create a GitHub action or workflow in the source file repo. **(optional)** 
  	- Modifying source files and then pushing to source repo will trigger a rebuild and push of the `public/` repo.
 	 - Hugo offers a copy&paste workflow for this purpose in the [docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/).

Steps 3-4, in particular, are not clear on the Hugo docs for GitHub hosting. Fortunately, of the only two other people that I found online that specifically host After Dark on Github, one of them wrote an enlightening [note](https://cedricleroy.github.io/posts/this-website/) that clarified the distinction between the two different directories. Hope that saves you some time!


# How to [After Dark](https://vhs.codeberg.page/after-dark/)

Most Hugo sites are run by themes, which define the site's style, layout, <i>and sometimes useful theme-specific shortcodes and advanced automatic features</i>. However, not all themes are created equal and some will require a more advanced knowledge of Hugo to function. Thankfully, After Dark is one of the good ones if you're a web novice. 

## What to Know
- shortcodes: In Hugo, shortcodes are akin to functions that you can put in your Markdown files to improve them in some way, such as info blocks, buttons, and optimized images. 
- list page vs. single page: after trial & error, I recommend creating directories for each single page and use _index.md to correspond to (non-leaf) list page directories, aka "sections", and index.md for (leaf) single pages, aka "posts". 
- **tip**: for After Dark's automatic features to kick in, you need content -- at least two posts in a section. 

With After Dark, you technically only have to spend time in the parent directory writing in Markdown or slightly tweaking the config. However, since After Dark handles many neat features automatically, it can be too rigid and After Dark also requires some debugging. If you want to be all-powerful you need to understand Hugo ... and at least be able to read HTML and edit at the right place. 

## Bend To My Will!
**Disclaimer**: Some of these workarounds may not be truly necessary and could simply be my misunderstanding the After Dark docs. Nonetheless, they work for me. 

- Copy the `/themes/after-dark/layouts/post/` directory to the parent directory's `/layouts/` folder. In the parent directory's `/layouts/` folder, create a `_default/` directory and copy the `single.html` file from the `post/` into `_default/`. 

<i>This overrides the default `single.html` for After Dark which, if you compare it to this new one, is rudimentary and doesn't incorporate some of the interesting After Dark features. To me so far, it seems After Dark has a bug in it's default handling of single-page, post-type content from schemas. I definitely suggest overriding the default layout files because it seems to solve the problem.</i>

- Duplicate and rename the `post/` directory from the above hack to the type of post for each section, e.g., `project/` and `note/` corresponding to the `projects/` and `notes/` section in my content. 

<i>This creates schemas for each section. No need to edit the HTML because After Dark's post schema has the necessary components. This step doesn't cause much change to section list / single page structure. Any post that specifies this schema in its front matter will apply the appropriate layout; this is preemptively useful if you plan to heavily customize specific sections.

Supposedly, if you want to have a featured list of posts for each section displayed at the top of section lsit pages and the bottom of a section's single pages, then you need these schemas. Then, you need to add the correct <s>blocks</s> for each section to the config. <s>However, I still have yet to get After Dark's featured lists to work.</s> Featured lists begin to work once you have multiple posts with similar tags. </i>

- Copy a `list.html` file from each of the schemas and paste into `_default/`. Rename them to the name of the section that the schema corresponds to, e.g., `projects.html` and `notes.html`.

<i>I used this to hack the `_index.md` files for each section. Hugo natively won't display any content in `_index.md` files which reside in non-leaf directories, but will for `index.md` which are leaf directories being the post-content of the site. However, you can override this by adding `{{ .Content }}` into the above HTML files below the header block. I hacked this to add alert blocks with the categories the following list of posts fall into; that way, readers can quicky jump to the [taxonomy page](https://vhs.codeberg.page/after-dark/feature/taxonomy-pages/) for the content that they're interested in.</i>

- Partially copy the `/themes/after-dark/layouts/partials/` directory, taking `page-summary.html`, `toc-maybe.html`, and `post/meta.html`. Modify `page-summary.html` by deleting lines 30 and 32. 

<i>Since the overridden default layouts call these, it's easier to put them here and keep the relative paths. Randomly, there is a conditional block preventing the display of post metadata unless `type = "post"` in the front matter. To my knowledge, this doesn't occur elsewhere in other After Dark source files and removing it immediately allowed for post metadata in listings.</i>

- Copy `/themes/after-dark/layouts/_default/baseof.html` into `/layouts/_default/` and add `{{ template "_internal/google_analytics.html" . }}` and `{{ template "_internal/google_analytics_async.html" . }}` into the `<head>` block. In config.toml, add the line `googleAnalytics = <YOUR_MEASUREMENT_ID>`. 

<i>I started reading about SEO because I want this site to be ranked as the top search result under my name. According to this [academic personal website  tutorial](https://www.elsevier.com/connect/creating-a-simple-and-effective-academic-personal-website), Google Analytics categorizes the best keywords for achieving your SEO goals. Naturally, I am also interested in my site's analytics so I linked up the site using Hugo's Google Analytics templates, following [this procedure](https://gideonwolfe.com/posts/sysadmin/hugo/hugogoogleanalytics/).</i>


# References
[Cedric LeRoy](https://cedricleroy.github.io)

[Sam Bateman](https://bateman.io)

[Mike Dane's Hugo tutorial vids](https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)
