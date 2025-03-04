# jekyll-theme-eclipsefdn

[![Gem Version](https://badge.fury.io/rb/jekyll-theme-eclipsefdn.svg)](https://badge.fury.io/rb/jekyll-theme-eclipsefdn)

This theme is currently experimental, but intended to provide the branding for Eclipse projects using GitHub pages for their documentation.
This Jekyll theme is intended to copy the theme of the main https://www.eclipse.org website so the projects use branding that is consistent with the main website.


![Screenshot](https://raw.githubusercontent.com/eclipsefdn/jekyll-theme-eclipsefdn/master/screenshot.png)

# Using the theme on your GitHub pages site

Eclipse projects typically publish their documentation using the GitHub pages functionality of the source code repository on GitHub. 
This involves pushing the documentation materials to the `gh-pages` branch in the repository. Once content has been pushed to this branch
it is publish statically at `https://eclipse-ee4j.github.io/<projectname>`. Without a theme, the site will be published using a default
theme.

To use this theme in GitHub pages, simply specify:

`remote_theme: eclipsefdn/jekyll-theme-eclipsefdn` in `_config.yml` at the root of the `gh-pages` branch.

Once the project has been set to use the theme, the project team should review each page on the site to ensure it renders correctly.
Any problems with the theme should be raised as an issue on this project, and pull requests are most welcome.

If you are publishing html files directly from `gh-pages`, please note that these are likely to require some additional work to ensure
the correct CSS and Javascipt is pulled in.

# Configuring the project page

The `_config.yml` file can contain variables to control the content in the
Project Resources box on the right side of the page:

* `links.source` - a URL to the source code
* `links.javadocs` - a URL to the javadocs
* `links.docs` - a URL to other documentation
* `links.faq` - a URL to Frequently Asked Questions
* `links.download` - a URL to a download page
* `links.hide_issuetracker` - set to true to disable the default link to the project's Issue Tracker page
* `links.mailinglist` - a URL to the project's mailing list

For example, the configuration for the JavaMail project page sets these links:

```
links:
  source: https://github.com/eclipse-ee4j/javamail
  javadocs: docs/api/
  download: https://github.com/eclipse-ee4j/javamail/releases
  mailinglist: https://accounts.eclipse.org/mailing-list/javamail-dev
  faq: FAQ
```

Note that some of the links are relative references to other pages in the
`gh-pages` branch.

# Converting a javaee GitHub pages site

Some of the javaee GitHub organization projects have existing `gh-pages`
web sites that are being contributed to Eclipse.
These sites can be converted to the new scheme by replacing the `theme`
entry with the `remote_theme` entry specified above, and by changing the
links in the `_config.yml` file.

The `_layouts` directory can be removed.

The `assets` directory can most likely be removed, unless it contains
assets (e.g., images, css) used by pages in the web site.

# Running the site locally

Follow these steps to run and check your project's site locally on your machine. Further instructions for Jekyll and GitHub pages can be
found here:

Pre-requisites:

* Ruby 2.1.0 or greater (check with `ruby --version`)

Instructions:

* (1 time only) Ensure you have a Gemfile in the root of your project with the following content:

````
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
gem 'jekyll-theme-eclipsefdn'
````

* (1 time only) Install the `bundler` gem: `gem install bundler`

* Install Jekyll and other dependencies: `bundle install`

* Switch the theme in `_config.yml`. Change this
````
remote_theme: eclipsefdn/jekyll-theme-eclipsefdn
````

to

````
theme: jekyll-theme-eclipsefdn
````

This will make sure the locally installed Gem will be used to render the site.

* Run the Jekyll site locally: `bundle exec jekyll serve`

# Building the theme (only necessary if you wish to make changes)

To build the theme itself, clone this repository (or your own fork of it), and do the following:

Pre-requisites:

* Ruby 2.1.0 or greater (check with `ruby --version`)

* Install the `bundler` gem: `gem install bundler`

* Install the dependencies: `bundle install`

* Build the Gem: `gem build jekyll-theme-eclipsefdn.gemspec`

Pushing the Gem to RubyGems

* Update the version number in `jekyll-theme-eclipsefdn.gemspec`
* Create a tag with the new version number
* Push commit and tag to github `git push origin master --tags`

