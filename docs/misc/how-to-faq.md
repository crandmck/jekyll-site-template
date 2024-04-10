---
title: How to add a new FAQ
permalink: /how-to-faq/
---
## Procedure

To add a new FAQ, follow these steps:

1. Create a new fork or branch for your contribution.
1. In your fork/branch, create a new file in the `docs/_faqs` directory. Name the file `faqNN.md` where `NN` is a number that is one greater than the largest number of the existing files.  For example, if the last file in `docs/_faqs` is `faq82.md`, then create `faq83.md`.  If the FAQ is specific to devboxes, use `dbfaqNN.md` or if specific to Run:ai, use `runai_faqNN.md`.
1. Copy and paste this front-matter (with placeholder values) to the beginning of the file:
  ```
  ---
  title: "Add your title here"
  tags: []
  ---
  ```
1. Replace the placeholder `title` with your question.
1. Add comma-delimited tags to the `tags` property array. Select the tags from the list below.  NOTE: Put the actual tag value, NOT the display name in the array.
1. Add the answer/resolution of the question to the body of the file.
1. Commit your changes to your fork/branch and open a pull request (PR).  Assign the PR to Rand.

The URL (permalink) of an FAQ is automatically set to `/faqs/<filename>`, based on the file name. Every FAQ is also automatically added to the [list of FAQs](faqs-by-topic.html) and to topic-specific FAQs such as devboxes and Run:ai.
{: .note}

## Tags

These are the existing tags.

If you need to add a new tag, update `_data/tags.yml`.

| Tag | Dsiplay Name |
|-----|-----------|
{% for tag in site.data.tags %} | {{tag.tag}} | {{tag.tag_name}} |
{% endfor %}
