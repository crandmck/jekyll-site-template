---
title: Authoring
permalink: /authoring/
---

This documentation site is powered by [Jekyll](https://jekyllrb.com/docs/), a static site generator, and [GitHub pages](https://help.github.com/categories/github-pages-basics/).  

Write pages in markdown, with a few additions from [Jekyll](https://jekyllrb.com/docs/).  For a brief markdown cheat sheet, see <http://commonmark.org/help/>.

## Front-matter

To make Jekyll process a markdown file, you **must** put a block of "front-matter" beginning and ending with `---` at the top of the file.  Include at least the `title` property; for example:

```
---
title: My page title
---
```

You can include the following additional optional properties:
- `permalink`: Page URI, relative to the site root.  Must match the corresponding `url` property in the sidebar. The default URI if this property is not specified is the file path, relative to the `docs` directory, with `.md` replaced with `.html`.
- `toc: false`: Include to suppress the automatically-generated table of contents.
- `excluded_in_search: true`: Include to exclude the page from site search.  For obscure reasons, this is included in every tutorial "container" page.

## Code blocks

A _code block_ is a section of code delimited by triple-backticks (<code>&#96;&#96;&#96;</code>)
This site uses [Rouge](https://github.com/jneen/rouge) to provide syntax highlighting in code blocks for a large number of languages, including Python, Java, and C++.
For a complete list, see [List of supported languages and lexers](https://github.com/jneen/rouge/wiki/List-of-supported-languages-and-lexers).

Simply add the name of the language after the initial triple-backtick, for example:

<pre class="special-codeblock"><code>&#96;&#96;&#96;python
  ... // Your Python code
&#96;&#96;&#96;</code></pre>

Here's an example of how it looks:

```python
@newrelic.agent.background_task()
@app()
def process(self, sensei_content_request, scratch_dir):
    LOG.info(scratch_dir)

    # Get paramters
    emb_hop = int(sensei_content_request.get_param("hop"))
...
```

For other programming languages, change the first line; for example, for JavaScript, use <code>&#96;&#96;&#96;js</code>.

## Images
{% assign dot="." %}

Always put image files in the `docs/images` directory.
Then use the relative path to the image, based on the URI of the page, typically  determined by the page's `permalink`.  So for all doc pages (except library API docs), the path to images is `../images/<filename>`.

To use an external image, simply use the image URL instead of the path to the image file in the repository.

The syntax to use an image in a page is standard markdown:

```
!["Alt text here"]({{dot}}{{dot}}/images/logo.png)
```

The above example yields:

!["Alt text here"](../images/logo.png)

Scale images by adding `{:height="xx" width="yy"}` where `xx` and `yy` are  absolute pixel sizes.  For example:

```
!["Alt text here"]({{dot}}{{dot}}/images/logo.png){% raw %}{:height="41" width="33"}{% endraw %}
```

Yields:

![Alt text here](../images/logo.png){:height="41" width="33"}

## Styling

Add the following after any block of text to apply a CSS style:


```
{: style="css to apply"}
```

For example:

```
Here is some green text.
{: style="color: green;"}
```
Yields:

Here is some green text.
{: style="color: green;"}

Add the following to apply a CSS class:

```
Text to style
{: .css-class-name }
```

For example:

```
Here is some styled text.
{: .example-link}
```

Yields:

Here is some styled text.
{: .example-link}

## Links

To make a link open in a new tab, add `{: target="_blank"}` after the markdown link.  For example:

```
[Adobe web site](https://www.adobe.com/){: target="_blank"}
```

Yields: [Adobe web site](https://www.adobe.com/){: target="_blank"}. When you click this link, it opens in a new tab.

## GitHub-only display

Use the `.gh-only` style for text that you want to display only when the page is viewed directly in GitHub.  The text will not be displayed in the page rendered by Jekyll.

For example:

```
Here is some text that will only be displayed in GitHub.
{: .gh-only}
```

You won't see the text below, but if when you [view it in GitHub](https://git.corp.adobe.com/pages/adobesensei/training-framework/contributing-docs/#github-only-style), you will see the text.

Here is some text that will only be displayed in GitHub.
{: .gh-only}

## Alerts

Use the following "alert" styles to call out special information.

### Tip

This markdown:

```
Here's a handy tip that may help you out.
{: .tip }
```

Yields:

Here's a handy tip that may help you out.
{: .tip }

### Info

This markdown:

```
Here's some useful information.
{: .info }
```

Yields:

Here's some useful information.
{: .info }

### Note

This markdown:

```
Take note; this is some information you need.
{: .note }
```

Yields:

Take note; this is some information you need.
{: .note }

### Warning

This markdown:

```
Danger, Will Robinson! This is a warning you should heed.
{: .warning }
```

Yields:

Danger, Will Robinson! This is a warning you should heed.
{: .warning }

### Review comment

This markdown:

```
Here's some information that needs review before publishing.
{: .review}
```

Yields:

Here's some information that needs review before publishing.
{: .review}
