# Slides of Irresponsible AI paper

The slide deck is made using [remark](https://remarkjs.com), "a simple, in-browser, markdown-driven slide-show tool targeted at people who know their way around HTML and CSS" ([reference](https://github.com/gnab/remark)). Even if you don't know your way around HTML and CSS, if you are comfortable with the basics, and you're familiar with markdown, then it should not be too hard to get up to speed.

The slides of our ICML presentation are publicly available on [irresponsibleai.github.io/slides-icml26](https://irresponsibleai.github.io/slides-icml26). The main (markdown) file with the content of the slides is `slides-icml26.md`. If you change the file, commit the changes and push to the remote GitHub repository, after a few seconds or minutes, you would be able to see the changes on the website, provided the changes did not break anything. However, this is not convenient at all. The real way to edit the slides is by building the website locally.

## How to build the slides locally

This website relies on [Jekyll](https://jekyllrb.com/), which is a static site generator. Jekyll makes it quite easy to create web content written on markdown, for example.

If it is the first time you use Jekyll, it is recommended to follow to [Quickstart guide](https://jekyllrb.com/docs/). You will see that you need to install some required tools, including Ruby, RubyGems, GCC and Make. You can find [more information here](https://jekyllrb.com/docs/installation/). You will find guides for Ubuntu as well as Windows and Apple laptops.

If everything is correctly installed, all you need to do is:

1. Open a terminal
2. Clone this repository
3. Change directory into the root of the repository
4. Run `bundle exec jekyll serve`
5. Go to http://localhost:4000 or http://localhost:4000/slides-icml26 for the slides. It may be `http://127.0.0.1:4000/` too/instead.

The command in the fourth step builds the website locally and starts a local server to visualise it in the browser. It will also watch for changes in any files and re-build the website. So if you edit the markdown file of the slides, after you save it, you can go to the browser, refresh the page and voilà. Note that it may take a few seconds to re-build the site.

If you are curious about how to make all this from scratch, you can take a look at the section [How to reproduce this website](#how-to-reproduce-this-website).

## How to reproduce this website

Important note: the following instructions are not necessary to build the slides locally. These are here only for completeness, to document all the steps needed in case you wanted to make this from scratch, for example for a different project.

1. Create a new repository and clone it

2. Assuming the [requirements to use Jekyll](https://jekyllrb.com/docs/installation/#requirements) are installed, initialise a new jekyll site from the root of the local repo:

```
jekyll new .
```

Alternatively, one could do `jekyll new /path/of/the/root/dir/` and then initialise a repository from there.

3. Create `_layouts/slides_starling.html` as a copy of [alexhernandezgarcia.github.io/_layouts/slides_mila_starling.html](https://github.com/alexhernandezgarcia/alexhernandezgarcia.github.io/_layouts/slides_starling.html), simply because that is a commonly used (by Alex HG) style file for remarkjs slides. It will be modified later.

4. Start a slides markdown file, for example `slides-icml26.md` with `layout: slides_starling` in the preamble. This should already enable building a slide deck with remarkjs.

5. To build the site (and the slides) locally, we just need to:

- Run `bundle exec jekyll serve` from the root directory
- Visit `http://127.0.0.1:4000/slides-icml26` from the browser

## How to change the style of the slides

The appearance of the slides is governed by the file `[_layout/slides_starling.html](_layout/slides_starling.html)`, provided its name is used in the preamble of the markdown file with the content of the slides. `slides_starling.html` is an HTML file with two relevant sections:

- The `<body>` section at the bottom inserts the markdown content from the slides file, and it defines a series of scripts that are important for remarkjs to work as expected. There is also some javascript code to improve the rendering of math LaTeX expressions.
- The `<style>` section of the header, containing the CSS code that defines the style or appearance of the slides, such as colours and formatting elements.

### Colour

The colours of the various elements of the slides (background, titles, hyperlinks, etc.) has been changed with respect to the source file referenced above. To see the specific changes of the various elements, check the commits whose message starts with "Slides layout colours:".
