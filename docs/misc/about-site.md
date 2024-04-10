---
title: About this documentation site
permalink: /about-this-site/
---

This documentation site is powered by [Jekyll](https://jekyllrb.com/docs/), a static site generator, and [GitHub pages](https://help.github.com/categories/github-pages-basics/).  

## About the documentation

The documentation source files are in the `/docs` directory (and sub-directories).

The documentation has three parts:

- [General documentation](#general-documentation), the vast majority of the information, including
- [FAQs](#faqs), which are managed a bit differently from regular documentation.

### General documentation

The general documentation is in the `docs` folders. Generally, you will want to create
sub-folders within this folder to organize your content.

### FAQs

Frequently-asked questions (FAQs) have a special format: Each FAQ is in a single `.md` file in the `_faqs` directory. The file name is not significant, but by convention, it should be `faq_NN.md`, where NN is a unique number in sequence with the existing files.

For instructions to add a new FAQ, see [How to add a new FAQ](../contributing-faqs/).

The `tags` property is an array of one or more of the tags in `_data/tags.yml`.  Use the `tag` value, not the `tag_name` value, which is the corresponding display name.  Tags are used to categorize FAQs.

## Contributing

To contribute documentation updates, use a pull request, just as you would for code.  

There are two ways to make a docs PR:
- **Use a branch** for small corrections such as typos, or other minor changes.  You won't be able to preview the Jekyll-rendered changes, i.e. how they will actually look in the site.   You will only be able view the markdown, but in many cases that's sufficient.
- **Use a fork** for more extensive changes, where you want to see how the site will look as rendered.  For example, if you're adding a new page, changing the sidebar navigation order, or adding a page with more sophisticated formatting.

### Updating docs using a fork

To use a fork, follow these steps:

1. Fork the repository. Generally, you should fork it into your own "user org".
1. **If your edits involve more than one page**, to ensure the links in the sidebar navigation work properly, edit `/docs/_config.yml` and change the `url` to be the URL of your forked site.  So, change:
  ```
  url: https://github.com/org-name/site-name
  ```
  to
  ```
  url: https://github.com/<USERNAME>/site-name
  ```
  - **YOU MUST CHANGE THIS BACK TO ITS ORIGINAL VALUE BEFORE YOU CHECK IN YOUR CHANGES**.  If you don't, it will break the site!
  - You don't need to make this change if you are editing only one page, but be aware that in your fork, the links in the sidebar nav will go to the template, not your fork.
1. To make the site display an "overlay" with a prominent warning that these are draft prerelease docs, add `draft: true` to `/docs/_config.yml`.  Be sure to remove this before you land the PR from the fork.
3. Enable GitHub Pages for your fork:
   - On the page for your GitHub fork, click **Settings**
   - Scroll down to **GitHub Pages**.
   - Under **Source** choose `master branch /docs folder`.
   - Click on the link shown in the green box with the text "Your site is published at ...."  It may take a short time for the site to come up.
   - Now any changes you commit to the master branch of your fork will be reflected at your forked site.
4. To merge your changes with the published site, open a pull request.  

   If you edited `_config.yml`, be sure to change it back to its original state before merging your PR.
   {: .warning}

### Checking site status

It's possible to make a change to a page (such as a malformed Liquid directive) that will cause an error, and prevent the site from building.  If this occurs, the existing site will be unaffected, and the site will just show the last working version. However, **none of the changes in your commit/PR will be visible**.  You cannot cause such an error with basic markdown, only with Liquid tags or the sidebar navigation file (`docs/_data/sidebar.yml`).

To check site status, go to the repo settings **GitHub Pages**.  

If you see this:

<div markdown="1" style="color: #2c5a2c; background-color: #e3fee6; border: 1px solid #d2d5d9; padding: 7px 0 0 15px; width: 600px; font-size: 80%;">
Your site is published at <url.whaterver.com>
</div>

Then everything's good!

However, if you see a yellow box that says "There is a problem with the site" and an error message, then you need to figure out what's wrong and fix it before _any_ changes to the site will take effect.
