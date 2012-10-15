# Megalodon

The goal of megalodon to provide a simple, repeatable, and extendable way to setup a modern php development environment on Mac OS X. It consists of a collection of [homebrew](http://mxcl.github.com/homebrew) formulas and [chef](http://www.opscode.com/chef/) recipies. It's pretty awesome.

This project is heavily influenced by [cider/cinderella](https://github.com/atmos/cinderella), which is aimed at providing an environment for ruby/python/node. Megalodon started as a fork of [smeagol](https://github.com/atmos/smeagol) (the chef bits of cinderella), but has since taken a different approach.

## Installation

Install [homebrew](http://mxcl.github.com/homebrew/).

Install megalodon:

    brew install https://raw.github.com/msonnabaum/megalodon/master/formulas/megalodon.rb

Run megalodon:

    megalodon install

## Usage

### General

Megalodon uses OSX's built in apache, so you can restart apache like so:

    sudo /usr/sbin/apachectl restart

Everything else that's installed with homebrew should have a plist in ~/Library/LaunchAgents (OSX's equivalent to /etc/init.d), which can be managed with lunchy. It will soon be included in megalodon, but for now just do `gem install lunchy`.

For example, you'd restart mysql like so:

    lunchy restart mysql

### Managing virtual hosts

You will need to edit /etc/hosts as per usual; To add a new virtual host, add a new .json file in:

    ~/.megalodon/data_bags/vhosts

To re-generate the apache confs after modifying/adding vhosts:

    megalodon update_vhosts

To add an SSL version (with self-signed cert) of a virtual host, add the following line to a host's json file.

    "SSL": true

To add server aliases to a virtual host, add the following line to a host's json file.

    "server_aliases": [ "alias1.example.com", "alias2.example.com"],

Then restart apache as above.

## Other notes

mysql default username is root, no password
