# Install Ruby on macOS

`install-ruby` is a script that installs and configures the tools necessary to
manage multiple versions of Ruby on your Mac.

It can be run multiple times on the same machine safely. It installs, upgrades,
or skips packages based on what is already installed on the machine.

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
