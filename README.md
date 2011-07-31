# Heroku Builder #

This private Gist shows how to build any type of native app to run on
Heroku's current Cedar stack (as long as their server version remains at
Ubuntu 10.04). As of 10/21/2011 Heroku still uses Ubuntu 10.04.

To start out clone this Gist's git repository locally. Now download the
Heroku Builder Vagrant box that I prepared.

## Where to obtain Heroku Builder Vagrant Box image? ##

Download from my public DropBox area. It is "public" in the sense that it
doesn't require a password, but I have not publicized it outside of
Salesforce.com/Assistly:
http://dl.dropbox.com/u/43329068/heroku-builder.box

## What next? ##

* Make sure you have a recent version of Ruby installed (i.e. 1.8.7+) and a
somewhat recent RubyGems version. This depends on your OS, so go google how
to do that if you don't have this on your system.

* You also need to install VirtualBox. Yes, I know. It is an Oracle product
now. Deal with it, even I am attempting to. Install from:
http://virtualbox.org

* Now install the `vagrant` gem: `[sudo] gem install vagrant`. Note: sudo
may or may not be necessary depends on your OS and Ruby setup. You are
smart, figure it out for your environment.

* Now that you are armed with `vagrant`, at the root of the clone of this
repo import the vagrant box you downloaded from my DropBox public area, like
so:
`vagrant box add heroku-builder /path/to/your/downloaded/heroku-builder.box`

* Copy the apps.yml.example file to apps.yml and edit to specify all native
Heroku apps that need building in the Heroku Builder VM.

* Now launch the vagrant box VM like so: `vagrant up`

* Now you can SSH into this headless VM running in VirtualBox's non-GUI mode
by executing: `vagrant ssh builder`

* Now build, build, build. Your current host directory is loaded at
`/var/$APPNAME`.

## How to contact me? ##

* Email me at salesforce: spotter@salesforce.com
* Email me on my personal account: me@susanpotter.net
* Find me on GUS Chatter (Susan Potter, LTMS @ Assistly)
* Find me on Twitter: @SusanPotter
