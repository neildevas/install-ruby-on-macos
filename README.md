# Install Ruby on macOS

`install-ruby` is a script that reliably configures your Mac so you can install
Ruby gems (like Bundler, Jekyll, Rails), and switch between multiple versions of
Ruby.

It can be run multiple times on the same machine safely. It installs, upgrades,
or skips packages based on what is already installed on the machine.

Why
---
Installing Ruby and/or gems is a common source of confusion and frustration.
Search for `You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory`
in your favorite search engine, and you will see pages and pages of results.

To make matters worse, the vast majority of suggestions are bad advice and
incomplete. The reason for the error message above is because people are trying
to install gems using the version of Ruby that comes pre-installed by Apple.
That error message is there for a reason: you should not modify macOS system
files. A common suggestion is to bypass that security protection by using
`sudo`, which is not safe and can cause issues down the line that are hard to
undo.

The recommended way of using Ruby on a Mac is to install a newer (the
macOS version is often outdated and is only updated during a major release),
separate version in a different folder than the one that comes by default on
macOS. The best and most flexible way to do that is with a Ruby manager. The
most popular ones are: RVM, rbenv, and chruby. There are different ways to
install these tools, and they all require additional configuration in your shell startup file, such as `.bash_profile` or `.zshrc`.

When attempting to install and configure a Ruby manager manually, it's easy to
miss or fumble a step due to human error or incomplete or outdated instructions. Since all of the steps are automatable, the best and most reliable way to set up Ruby on a Mac is to run a script like the one I've written. It has been tested many times on many computers and rarely fails.

## Why chruby and not RVM or rbenv?

It is the smallest, most reliable, and easiest to understand. I like that it does not do some of the things that other tools do:

* Does not hook `cd`.
* Does not install executable shims.
* Does not require Rubies to be installed into your home directory.
* Does not automatically switch Rubies by default.
* Does not require write-access to the Ruby directory in order to install gems.

Other folks who prefer `chruby`:

* <https://kgrz.io/programmers-guide-to-choosing-ruby-version-manager.html>
* <https://stevemarshall.com/journal/why-i-use-chruby/>
* <https://linhmtran168.github.io/blog/2014/02/27/moving-from-rbenv-to-chruby/>

What it sets up
---------------

* [Bundler] for managing Ruby gems
* [chruby] for managing [Ruby] versions (recommended over RVM and rbenv)
* [Homebrew] for managing operating system libraries
* [ruby-install] for installing different versions of Ruby

[Bundler]: http://bundler.io/
[chruby]: https://github.com/postmodern/chruby
[Homebrew]: http://brew.sh/
[Ruby]: https://www.ruby-lang.org/en/
[ruby-install]: https://github.com/postmodern/ruby-install

## Supported macOS versions
* macOS Mojave (10.14)
* macOS High Sierra (10.13)
* macOS Sierra (10.12)
* OS X El Capitan (10.11)
* OS X Yosemite (10.10)
* OS X Mavericks (10.9)

Install
-------

Begin by opening the `Terminal` or `iTerm` application on your Mac. The easiest
way to open an application in macOS is to search for it via [Spotlight]. The
default keyboard shortcut for invoking Spotlight is `command-Space`. Once
Spotlight is up, start typing the first few letters of the app you are looking
for, and once it appears, press `return` to launch it.

In your Terminal window, run the following commands:

```sh
cd ~
curl --remote-name https://raw.githubusercontent.com/monfresh/install-ruby-on-macos/master/install-ruby
/usr/bin/env bash install-ruby 2>&1 | tee ~/laptop.log
```

The [script](./install-ruby) itself is available in this repo for you to review
if you want to see what it does and how it works.

Note that the script will ask you to enter your macOS password at various
points. This is the same password that you use to log in to your Mac.

**Once the script is done, quit and relaunch Terminal.**

[Spotlight]: https://support.apple.com/en-us/HT204014

Debugging
---------

Your last run of the script will be saved to a file called `laptop.log` in your
home folder. Read through it to see if you can debug the issue yourself. If not,
copy the entire contents of `laptop.log` into a
[new GitHub Issue](https://github.com/monfresh/install-ruby-on-macos/issues/new).
Or, attach the whole log file as an attachment.
