# just-the-docs-template

This is a *bare-minimum* template to create a documentation website that:

- Use the static-site generator [Jekyll];
- uses the [Just the Docs] theme;
- can be built and published on [GitHub Pages] using a [GitHub Actions workflow];

See [a deployed version of this template here].

To get started with creating a site, just fork this repository.

After forking the repository, update it as needed:

## Invite Others to Collaborate with you on this Project

Only one team member needs to clone the repository. They can then give their team members access under the repo's `Settings => Collaborators` page.

The team should then collaboratively work on building out this site according to the assignment instructions.

## Replace the Content of the Template Pages

Update the following files to your own content:

- `index.md` (Your new home page.)
- `README.md` (Replace this readme with some information about your team and team members.)
- `docs\first-doc.md` (Sample nested page. All pages other than home should go in `docs`.)

Remember that you will be using [Markdown Syntax] rather than raw HTML to format the content of your pages.

## Publish your site on GitHub Pages

The following should be done by the team member who owns the repo.

1.  If your created repositor is `YOUR-USERNAME/YOUR-REPO-NAME`, update `_config.yml` to:

    ```yaml
    title: YOUR TITLE
    description: YOUR DESCRIPTION
    theme: just-the-docs

    url: https://YOUR-USERNAME.github.io/YOUR-REPO-NAME

    aux_links: # remove if you don't want this link to appear on your pages
      Template Repository: https://github.com/YOUR-USERNAME/YOUR-REPO-NAME
    ```

2.  Push your updated `_config.yml` to your site on GitHub.

3.  In your newly forked version of this repo on GitHub:
    - Go to the `Actions` tab and enable the repository actions.
    - Go to the `Settings` tab -> `Pages` -> `Build and deployment`, then select `Source`: `GitHub Actions`.
    - If there were any failed Actions, go to the `Actions` tab and click on `Re-run jobs`.
    - Test if deployment worked by visiting the `url:` you set in the `_config.yml` file.

## Quick Overview Of How This Repo Works

- This repo can generate a documentation website similar to your [Applied Math course notes](https://stungeye.github.io/Applied-Math-For-Games-1/).
- The docs are written using Markdown syntax and converted to a website using Jekyll with the Just the Docs theme.
- The notes consist of modules written as `.md` files in the `docs` folder.
- The sidebar menu and the module table of contents are auto-generated.

Each of these topics is covered below.

## Jekyll and Just the Docs

[Jekyll](https://jekyllrb.com/) is a tool that takes plain text documents and turns them into static HTML websites.

Jekyll sites can be hosted for free on [GitHub Pages](https://pages.github.com/). GitHub Pages publishing instructions for this repo are described above.

The look and feel of a Jekyll generated website can be changed using a Jekyll theme. These notes use the [Just the Docs theme](https://just-the-docs.github.io/just-the-docs/). The following sections are provided as a quick start guide, but you should reference the [official documentation](https://just-the-docs.github.io/just-the-docs/) for the nitty-gritty details on how to work with the theme.

## Writing Notes in Markdown and Editing Notes Online

The notes are written using the [Kramdown-variant of Markdown Syntax](https://kramdown.gettalong.org/quickref.html). This means the notes are stored as plain text in this repository and converted into an HTML website by Jekyll. There is a small amount of meta-data at the top of each markdown file that [Jekyll calls front matter](https://jekyllrb.com/docs/front-matter/).

Markdown allows us to easily add typographic formatting, links, images, and tables to the notes. Everything you need to know about Markdown can be seen at [the Kramdown Quick Reference](https://kramdown.gettalong.org/quickref.html).

Some example Markdown:

````markdown
# This is a Heading

## And a Sub-Heading

This paragraph includes **bold**, _italized_, and `monospaced` text, plus a [link](http://stungeye.com).

- Item
- List

```
This is a code block
that spans multiple lines.
```
````

Which outputs:

> # This is a Heading
>
> ## And a Sub-Heading
>
> This paragraph includes **bold**, _italized_, and `monospaced` text, plus a [link](http://stungeye.com).
>
> - Item
> - List
> 
> ```
> This is a code block
> that spans multiple lines.
> ```

## The File and Folder Structure of the Repository

All of your documentation modules will be found in the `docs` folder as Markdown files with `.md` file extensions.

The `docs` folder is currently structured like this:

```
- docs
  - first_doc.md
```

Feel free to create sub-folders within docs to better organize your `*.md` files. Your markdown files will be automatically discovered, even if they are in sub-folder.

## Organizing Modules in the Sidebar Menu

The sidebar menu is automatically generated. The order in which modules are listed in the sidebar menu is controlled using the [Jekyll front matter](https://jekyllrb.com/docs/front-matter/) found at the top of each markdown file. The front-matter looks like this:

```
---
title: Module Title
nav_order: 5
---
```

The `title` specified will be the link title used in the sidebar menu. The `nav_order` controls the order in which modules appear in the sidebar menu.

## Adding an Autogenerated Table of Contents to a Module

You can add an auto-generated Table of Contents to any module. This only works well if you break your module into sections and sub-section using level 2 and level 3 headers (created in markdown with two or three hash `#` marks preceeding your headings).

The code used to add the table of contents is as follows. This should go directly after the front matter:

```markdown
<!-- prettier-ignore-start -->
# Main Title for Module 
{: .no_toc }

A short introductory paragraph for the module to come before the table of contents.

## Table of Contents
{: .no_toc }

1. TOC
{:toc}

<!-- prettier-ignore-end -->
```

The generated table of contents will replace the two lines that read `1. TOC` and `{:toc}`.

The `{: .no_toc }` statement marks headings that shouldn't be included in the table of contents.

The `<!-- pettier... -->` start and end tags prevents this code from being broken by the Prettier code formatting plugin for VS Code. The blank line above the prettier-ignore-end tag is crucial.

## Licensing and Attribution

This repository is licensed under the [MIT License]. You are generally free to reuse or extend upon this code as you see fit; just include the original copy of the license (which is preserved when you fork this repo). While it's not necessary, we'd love to hear from you if you do use this template, and how we can improve it for future use!

The deployment GitHub Actions workflow is heavily based on GitHub's mixed-party [starter workflows]. A copy of their MIT License is available in [actions/starter-workflows].

----

[Jekyll]: https://jekyllrb.com
[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[GitHub Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[a deployed version of this template here]: https://stungeye-rrc.github.io/Just-The-Docs-Template/
[Markdown Syntax]: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
[MIT License]: https://en.wikipedia.org/wiki/MIT_License
[starter workflows]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml
[actions/starter-workflows]: https://github.com/actions/starter-workflows/blob/main/LICENSE
