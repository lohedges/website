# lesterhedges.net

Copyright &copy; 2013, 2014 Lester Hedges.

Released under the [GPL](http://www.gnu.org/copyleft/gpl.html).

## About
This is the repo for my personal website, [lesterhedges.net](http://lesterhedges.net).

A simple Bash script is used to build the site. The script generates a
lightweight static website from a set of configuration, template, and
content files. This allows for easy content management and deployment.
While there are plenty of static website generators out in the wild
(e.g. [hackyll](http://jaspervdj.be/hakyll/index.html), [jekyll](http://jekyllrb.com/),
[nanoc](http://nanoc.ws/), [stacey](http://www.staceyapp.com/),
[yst](http://github.com/jgm/yst)) nothing did quite what I wanted, hence the
hacky Bash script.

## Content management
Content is managed through a series of simple files and folders. The basic set
up is as follows:

### `config.txt`
This is the main configuration file which contains a bunch of variables that
are sourced by the `makesite` script on startup. Have a look at the file for
details.

### `templates/`

This directory contains all of the html/css templates needed to build the
site. These are:

* `header.html`
* `footer.html`
* `banner.html`
* `analytics.html` (optional)
* `style.css`

Take a look at the files to see what they contain.

### `content/`

This is the directory in which all of the website content is located. The
root directory contains the html for the homepage, `homepage.html`,
its configuration file, `homepage.config`, and folders for all of the top
level pages.

These folders should be labeled with a numeric prefix that indicates the
desired order of appearance in the side menu and site map of the website,
e.g `0.folder`, `1.folder`, etc. The numbers run from 0-9, i.e. there is
the assumption that there will be no more than 10 pages. Each folder contains
its own html and configuration file,
`folder/folder.html` and `folder/folder.config`.

A folder can also contain subpages (again up to 10) which should be
organized in the same manner. The site currently doesn't support any
further nesting of subpages.

Any directory can also contain an `assets` folder for storing additional
files for the page (scripts, images, etc.).

## Usage
The `makesite` script can be used to build the static webpages for deployment
on both the `local` or `remote` hosts specified in the configuration file.

``` sh
	./makesite local|remote
```

The resulting website can be found in the `build/local`, or `build/remote`
directory.

While building the website the script also creates a site map and side bar
links using the hierarchy of the `content` directory as its guide.

Note that `makesite` requires version 4+ of Bash.
