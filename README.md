# Outrun Everything

## Original Description

> This is a small (growing?) collection of user-stylesheets based upon the
[Solarized](http://ethanschoonover.com/solarized) theme
([repo](https://github.com/altercation/solarized)). It uses
[Stylus](http://learnboost.github.com/stylus/) to generate the CSS. The
home of this stylesheet is at
<https://github.com/alphapapa/solarized-everything-css>.

Wouldn\'t it be nice if (almost) every web site looked Solarized? I
thought so. So here is a start. :)

## Contents [[TOC]{.smallcaps}]{.tag tag-name="TOC"} {#contents}

-   [Solarized...Everything?](#solarizedeverything)
    -   [Screenshots](#screenshots)
        -   [GitHub](#github)
            -   [Dark](#dark)
            -   [Light](#light)
        -   [Wikipedia](#wikipedia)
            -   [Dark](#dark-1)
            -   [Light](#light-1)
    -   [Installation](#installation)
    -   [Development](#development)
    -   [Credits](#credits)
    -   [License](#license)

## Screenshots

### GitHub

1.  Dark

    ![](https://raw.githubusercontent.com/alphapapa/solarized-everything-css/screenshots/solarized-dark/github.png)

2.  Light

    ![](https://raw.githubusercontent.com/alphapapa/solarized-everything-css/screenshots/solarized-light/github.png)

### Wikipedia

1.  Dark

    ![](https://raw.githubusercontent.com/alphapapa/solarized-everything-css/screenshots/solarized-dark/mediawiki.org.png)

2.  Light

    ![](https://raw.githubusercontent.com/alphapapa/solarized-everything-css/screenshots/solarized-light/mediawiki.org.png)

## Installation [[noexport_1]{.smallcaps}]{.tag tag-name="noexport_1"} {#installation}

### From userstyles.org

You may install some of the stylesheets directly in your browser from
[userstyles.org](http://userstyles.org):

-   [Solarized Everything:
    GitHub](https://userstyles.org/styles/127328/solarized-everything-github)
-   [Solarized Everything:
    Wikipedia](https://userstyles.org/styles/140962/solarized-everything-wikipedia)

### Manual

Install the stylesheet of your choice according to your browser\'s
method (e.g. using the Stylish extension in Firefox).

CSS files for each theme are in the `css`{.verbatim} directory.

1.  Files

    -   `theme-all-sites-*.css` These have all the sites\' styles
        smushed into one big file. Might work pretty well for most
        sites. If the collection grows, it might begin to have
        conflicts--but it still might work pretty well. It might be a
        lot better than adding a separate stylesheet for every site you
        visit...
    -   `theme-generic-*.css` These are intended to be generic, suitable
        for many simple sites. They probably won\'t do much for fancy,
        popular sites with lots of custom CSS, but for simple, mostly
        unstyled sites, they might work okay.
    -   `theme-mediawiki-*.css` For MediaWiki sites, like Wikipedia
    -   `theme-disqus-*.css` For Disqus comments
    -   `theme-github-*.css` For GitHub
    -   `theme-google-*.css` For Google
    -   `theme-hackernews-*.css` For Hacker News
    -   `theme-planet.emacsen.org-*.css` For [Planet
        Emacsen](http://planet.emacsen.org)
    -   `theme-stackexchange-*.css` For StackExchange sites. Not all
        sites are covered, but some of the main ones are. Patches
        welcome.
    -   `theme-sakai-*.css` For sites hosted by
        [sakai](https://sakaiproject.org/), a popular course management
        program.

## Development [[noexport_1]{.smallcaps}]{.tag tag-name="noexport_1"} {#development}

To make changes, just edit the `.styl`{.verbatim} files and run
`make`{.verbatim}. (You need to have Stylus installed, of course.)

Basically, nearly the only things that should be in
`themes/*/*.styl`{.verbatim} should be theme specific colors. Everything
else should go in `sites/*.styl`{.verbatim}. Colors are defined as
`color-`{.verbatim} variables, and mixins are used to insert common CSS
properties (like `color`{.verbatim}, `background`{.verbatim}, etc) with
`!important`{.verbatim}. Most changes can be made without inserting CSS
properties directly into the selectors.

I highly recommend using Emacs with `stylus-mode`{.verbatim} and
`outline-minor-mode`{.verbatim}, but, of course, you can use whatever
you like. :)

It\'s a good idea to avoid the use of `*`{.verbatim} selectors wherever
possible. They tend to have unanticipated side-effects which can take
time to track down.

### Require tree

Stylus can be very confusing when it comes to importing/requiring sheets
into other sheets. Unfortunately, the order in which they are imported
*does* matter, as each one seems to be parsed and executed in-order,
rather than importing them all at once and then having a global
namespace.

This is how the sheets `require` in this project:

-   `Makefile`{.verbatim}
    -   `theme`{.verbatim}: contains custom theme files. Each theme
        corresponds to a group of css files.
        -   `*/{dark,light}.styl`{.verbatim} (in Makefile syntax:
            `$$color.styl`)
            -   `colors`{.verbatim}
            -   Contents of `{dark,light}.styl`{.verbatim}
    -   `styl`{.verbatim} (which loads `styl/index.styl`{.verbatim})
        -   `mixins`{.verbatim}
    -   `sites/*.styl`{.verbatim}: The site-specific sheets, as well as
        `generic.styl`{.verbatim}, which applies to all of them, and
        also builds as a separate sheet for non-specific sites.
        `all-sites.styl`{.verbatim} puts all of the site-specific sheets
        into one big CSS file, which some people may prefer over setting
        up custom CSS for each site in their browser. Styles starting
        with `_`{.verbatim} will not be included in
        `all-sites.styl`{.verbatim}

This way, the color value-name mappings are loaded first, after which
those friendly names can be used in the files that actually style
elements and pages.

### New Themes

It\'s easy to add your own themes:

1.  Copy an existing theme directory in the `themes/`{.verbatim}
    directory, giving it a new name.
2.  Modify it as required.
3.  Run `make`{.verbatim} in the project root directory to build the CSS
    files.

## Credits

-   Thanks to [Florian Bruhin](https://github.com/The-Compiler) for
    contributing the Reddit and DuckDuckGo sheets, as well as several
    fixes and improvements.
-   Thanks to [Jay Kamat](https://github.com/jgkamat) for contributing
    the Sakai stylesheet and several fixes and improvements.
-   Thanks to [Cal Martin](https://github.com/cal2195) for the gruvbox
    theme.
-   Thanks to [Adam Beckmeyer](https://github.com/non-Jedi) for adapting
    [Romain Lafourcade\'s Apprentice
    theme](https://github.com/romainl/Apprentice).

## License

This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
Public License for more details.

You should have received a copy of the GNU General Public License along
with this program. If not, see
<https://www.gnu.org/licenses/gpl-3.0.txt>.
