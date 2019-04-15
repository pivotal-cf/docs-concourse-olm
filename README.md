# Pivotal Concourse Documentation

This repository contains documentation for Pivotal Concourse, the Pivotal supported
version of OSS Concourse. It is a CI/CD tool that is also effective for
continuously deploying and managing Pivotal Cloud Foundry (PCF).

# Book Repo

https://github.com/pivotal-cf/docs-book-concourse-olm

# Branches

| Branch name | Use for… | Currently lives… |
|-------------| ------| ------|
| master      | Next version in development (5.x) | https://docs-pcf-staging.cfapps.io/p-concourse/5-n/ |
| 4.x      | Current published branch (4.0.0) | https://docs.pivotal.io/p-concourse/4-x/ |
| 3.x         | Current published branch | https://docs.pivotal.io/p-concourse/3-x/ |

# Pipeline

There are two pipelines for this doc at the moment: 
Edge (Staging):https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=concourse-edge

Production (Public): https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=concourse-olm

# Staging and Production Sites

Changes to the **master** branch in this repo appear here:
Staging: http://docs-pcf-staging.cfapps.io/p-concourse/4-0/index.html

Production (public): https://docs.pivotal.io/p-concourse/3-0/index.html - Making changes public requires a manual push to production.

# How to do a Pull Request (PR)

If you are not on the docs team, please make edits to this repo through PR's. Follow the instructions in this document: https://docs.google.com/document/d/14Go0uCj20BFMBzL2ddEKsZp-GONhVp0yr2cEFSskWnQ/edit?usp=sharing

# How to view your doc changes using Bookbinder

### <a id='bookbinder'></a>How To Use Bookbinder To View Your Docs

[Bookbinder](https://github.com/pivotal-cf/bookbinder/blob/master/README.md) is a command-line utility for stitching Markdown docs into a hostable web app. The PCF Docs Team uses Bookbinder to publish our docs site, but you can also use Bookbinder to view a live version of your documentation on your local machine.

Bookbinder draws the content for the site from `docs-content`, the subnav from `docs-book`, and various layout configuration and assets from `docs-layout`.

To use Bookbinder to view your documentation, perform the following steps:

1. Install Bookbinder by running `gem install bookbindery`. If you have trouble, consult the [Zero to Bookbinder](#zero-to-bookbinder) section to make sure you have the correct dependencies installed.
1. On your local machine, `cd` into `docs-book` in the cloned repo.
1. Run `bundle install` to make sure you have all the necessary gems installed.
1. Build your documentation site with `bookbinder` in one of the two following ways:
	* Run `bundle exec bookbinder watch` to build an interactive version of the docs and navigate to `localhost:4567/myservice/` in a browser. (It may take a moment for the site to load at first.) This builds a site from your content repo at `docs-content`, and then watches that repo to update the site if you make any changes to the repo.
	* Run `bundle exec bookbinder bind local` to build a Rack web-app of the book. After the bind has completed, `cd` into the `final_app` directory and run `rackup`. Then navigate to `localhost:9292/myservice/` in a browser.

### <a id='zero-to-bookbinder'></a>Zero to Bookbinder: How to Install Bookbinder and Build, View, and Edit Your Docs from Nothing

If you are reading this, Pivotal has invited you to a git repo where you can build and edit documentation in the Ruby / Markdown / HTML format that the online publishing tool [Bookbinder](https://github.com/pivotal-cf/bookbinder/blob/master/README.md) uses to build Pivotal's documentation.

Here's how to install Bookbinder and build your docs from the repo, starting from scratch, on a Mac OS X machine.

<p class="note"><strong>Note</strong>: All steps below are implicitly preceded with, "If you haven't already..." You should skip any installation steps that have already contributed to your environment.</p>

#### Install Ruby

In Terminal window:

1. Make and `cd` into a workspace directory.

    `$ mkdir workspace`

     `$ cd workspace`

1. Follow the instructions at `http://brew.sh` to install brew / homebrew

    `$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

1. Install your own (non-system) ruby.

    `$ brew install ruby`

#### Set up Git

1. Download and Install git by following the instructions at [git-scm.com](https://git-scm.com/download/).

1. Install your own (non-system) bash-completion (optional).

    `$ brew install git bash-completion`

1. If you don't already have one, generate a public/private RSA key pair, and save the key to your `~/.ssh` directory.
    ```
    $ ssh-keygen
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/pspinrad/.ssh/id_rsa): 
    ```

1. Get a [Github](http://github.com) account.

1. Add your RSA public key to your Github account / profile page.

    `$ cat ~/.ssh/id_rsa.pub # copy and paste this into Github profile page as new key`

#### Get the Correct Ruby Version for Bookbinder: Ruby 2.3.0

1. Install a Ruby manager such as chruby.

    `$ brew install chruby`

1. Add your Ruby manager to your `~/.bashrc` by appending the following line:

    `source /usr/local/opt/chruby/share/chruby/chruby.sh`

1. Install the `ruby-install` installer.

    `$ brew install ruby-install`

1. Run `ruby-install` to install Ruby 2.3.0.

    `$ ruby-install ruby 2.3.0`

1. Select the following Ruby version.

    `chruby ruby-2.3.0`

#### Install Bookbinder

1. Install `bundler`.

    `$ gem install bundler`

1. Install bookbinder (the `bookbindery` gem).

    `$ gem install bookbindery`

#### Build the Docs Locally

1. Clone the docs template repo you will be building from.

    `$ git clone git@github.com:pivotal-cf/docs-partners-template`

1. `cd` into the `book` subdirectory of the repo.

   `$ cd docs-partners-template/docs-book`

1. Run `bundle install` to install all book dependencies.

    `$ bundle install`

1. Run `bundle exec bookbinder watch` to build the book on your machine.

   `$ bundle exec bookbinder watch`
   
1. Browse to `localhost:4567` to view the book locally and "watch" any changes that you make to source `html.md.erb` files. As you make and save changes to the local source files for your site, you will see them in your browser after a slight delay.

1. After each session of writing or revising your docs source files, commit and push them to your github repo.

Happy documenting!
