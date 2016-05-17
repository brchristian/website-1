# Certbot Website

Website for EFF's Certbot project. Uses Jekyll for static site generation.

[![Build Status](https://travis-ci.org/certbot/website.svg?branch=master)](https://travis-ci.org/vbrown608/website)

## Getting Started

### Install
1. Install `ruby 2.0+`, `node`, and `npm 2.0+`.
2. `gem install jekyll` (requires v3.0 or higher)
3. `sudo npm install gulp -g`
4. `npm install`

If you want to build a copy of the documentation for your local mirror of the
Cerbot website, also do:

5. `git submodule init`
6. `git submodule update`
7. `sudo ./_docs.sh depend`
8. Install `pdflatex` e.g. via `sudo apt install texlive texlive-latex-extra`

### Run
To *watch* for changes and reload assets as needed via BrowserSync:
`gulp watch`

To *build* the site once:
`gulp build`

To build for production (minified javascript, no source maps):
`gulp build --env production`
The environment can also be set in the NODE_ENV environment variable. See https://github.com/gunpowderlabs/gulp-environments.

## Editing content

### Basic pages
Most pages can be edited as markdown files.

Use `/index.html` to edit the homepage.
Use `/[RELATIVE_URL]/index.html` to edit internal pages.

### Installation instructions

Are generated by JavaScript with
[Mustache](https://mustache.github.io/mustache.5.html), and can be edited in
`_scripts/instruction-widget`.

### FAQ
FAQ entries are a Jekyll collection. Add FAQ entries (question and answer pairs) as markdown files to the `_faq_entries` directory.

FAQ entries require two variables to be set in the [front matter](https://jekyllrb.com/docs/frontmatter/):

* title: the "Question" the FAQ entry answers
* weight: the position of this entry on the page - lighter FAQ entries will float to the top.

## Testing
Certbot/website uses [html-proofer](https://github.com/gjtorikian/html-proofer) to validate the html output of the build.

To install:
```
gem install html-proofer
```

To run the tests:
```
npm test
```
(Files with known issues are ignored.)