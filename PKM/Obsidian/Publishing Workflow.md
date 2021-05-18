---
creation date: 2021-05-02 15:42
modification date: Sunday 2nd May 2021 15:42:09
tags: ["#note"]
author: Jimmy Briggs
---

# Publishing Workflow

Instead of paying for the built-in [Obsidian Publish Feature](https://obsidian.md/publish) this workflow utilizes the fast, simple, and nice looking [MkDocs](https://www.mkdocs.org/) static sit generator to publish an Obsidian Vault.

## Initial Setup

1. Fork the Obsidian-MkDocs Github repo template from [jobindj/obsidian-mkdocs](https://github.com/jobindj/obsidian-mkdocs)
	- Note: if your obsidian vault is already a git repository you may want to utilize `git submodules` instead of nesting git repo's.
2. Clone the newly forked repo into your local obsidian vault
3. Move any notes you want published into the `<repo-name>/docs` folder
4. Commit and push changes to trigger the [Github Action](https://github.com/jobindj/obsidian-mkdocs/blob/main/.github/workflows/ci.yml) to publish your notes

Example Code:

```powershell
# navigate to obsidian vault's directory
cd <path/to/obsidian/vault>

# add a git submodule for the mkdocs repo under a folder named '_published'
git submodule add git@github.com:jimbrig/obsidian_published.git _published

# move some notes into the _published/docs folder
```

## Configuration

Configure the published site's [mkdocs.yml]() configuration file located in the root level of the MkDocs folder.

*See [MkDocs Configuration Documentation]() for more details*

https://www.mkdocs.org/#adding-pages

***
Links: 
Source:

