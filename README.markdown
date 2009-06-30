BOXSTRAP
========

An automated bootstrapping script to configure/install an environment located on a Dropbox.
by Camron Flanders <camron[dot]flanders[squiggly-at-symbol]gmail[dot]com>

I keep all my dot-configs, unix utilities and a set of crontab entries on my dropbox so that it's always backed up if I ever need it on another machine, or if (knock on wood) something happens and I need to re-install the OS on my laptop. All files are saved as human-readable and non-hidden. I have been using this naming convention for quite a long time now and decided to use that to my advantage. 

Here is some sample output to help describe what I'm talking about:

    camron@styx Dropbox $> ./boxstrap
    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotvim]
                                   to: [/Users/camron/.vim]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotvim/dotvimrc]
                                   to: [/Users/camron/.vimrc]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-bash_profile]
                                   to: [/Users/camron/.bash_profile]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-bashrc]
                                   to: [/Users/camron/.bashrc]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-gitconfig]
                                   to: [/Users/camron/.gitconfig]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-gitignore]
                                   to: [/Users/camron/.gitignore]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-inputrc]
                                   to: [/Users/camron/.inputrc]
    [boxStrap | INFO]: ---

    [boxStrap | INFO]: Will link from: [/Users/camron/Dropbox/dotfiles/dot-ssh-slash-config]
                                   to: [/Users/camron/.ssh/config]
    [boxStrap | INFO]: [config] already exists, REPLACE_EXISTING is currently set to [False].
    [boxStrap | INFO]: If you DO want to replace [config], set REPLACE_EXISTING to True
    [boxStrap | INFO]: ---
    [boxStrap | ERROR]: 

    [boxStrap | INFO]: will add to crontab:

    30	*	*	*	*	sh $HOME/Dropbox/cron/process_pics.sh >/dev/null 2>&1

As you can see, some of this scripts actions (and it's output reflects this) was modified from our defaults by the use of some configuration files placed in the directories that I want to process. Here is the config file in my dotvim directory:

    #dotvim configuration file
    link_dir=true
    link_only=dotvimrc

And here is the config file for my dotfiles directory:

    #dotfiles configuration file
    excludes=opensim.sh, old-dot-virtualenvwrapper_bashrc
    recurse=false

There are also a few command line options available, `boxstrap -h` will display them. You can ask it to be verbose `-v`, tell it to shut up `-q`, or even use it to generate a configuration file for you `-g`.

I have done my best to document the script as thouroghly as possible -- please read it for further information regarding the settings beyond what is in this quick readme. I have also done my best to note where I feel there are improvements to be made, the script was created, tested, and finished in under an hour - not including this documentation. If you have any additions, improvements, bugs, or anything else please feel free to report, fix, or fork this project.

TO_USE
======

Is this script at the root of your dropbox?
-------------------------------------------

**Yes?** Add your paths to `PATHS_TO_PROCESS` list in the script and run with `DRY_RUN` set to *True*.
**No?** Tell us where your dropbox is located using `DROPBOX_LOCATION`

Is the output correct?
----------------------

**Yes?** *Sweet!* Set `DRY_RUN` to *False* and run it again!

**No?** Setup some configuration files for directory-level override of defaults *OR* maybe you need to change the defaults?

Do you have a custom crontab?
-----------------------------

If you do, add it's path to `CRONTAB_LOCATION`, flip on `INSTALL_CUSTOM_CRONTAB` and we'll add it to your system crontab.

CONFIGURATION
=============

At the folder level, you can define a local configuration. We have a convenience method in the script that will generate this for you: `boxstrap -g DIR`. 

Here are the options available in the directory-local configs:

link_dir **(BOOL)**
-------------------

**Example:** `link_dir=True`

**Default:** `False`

Set this to *True* so that the containing directory is linked in it's entirety to the destination. So, instead of linking all the files in this directory, the directory itself will be linked. 

**NOTE:** If this is True, then only `destination` and `link_only` will be used.

link_only **(comma-separated paths)**
-------------------------------------

**Example:** `link_only=dot-vimrc`

**Default:** `None`

This is only honored if you have link_dir set to *True*. This will allow you to set a series of paths to link outside of the linked directory. 

**Example:** you have your dot-vim directory that needs linked to `$HOME/.vim` but you need your `dot-vimrc` (contained in your `dot-vim` directory) to be linked to `$HOME/.vimrc` also, so set this to `dot-vimrc`.

excludes **(comma-separated paths)**
-------------------------------------

**Example:** `excludes=foo.py, bar.txt, boo.c`

**Default:** `None`

This is a series of paths that you don't want to link. Say you have a couple of files that you don't need linked elsewhere, you just want to keep them where they are -- add them here.

recurse **(BOOL)**
------------------

**Example:** `recurse=False`

**Default:** `True`

If this is *False*, we won't burrow down into the subdirectories of the current path.

destination **(string)**
------------------------

**Example:** `destination=/usr/local/bin/`

**Default:** `$HOME`

This is the root destination of the current directories contents. Our default is `$HOME`, but say you have some unix utilities that you want in `/usr/local/bin/`, just set this to that!

LICENSE
=======

This is a bootstrapping script to help setup a new environment using your dropbox.

Copyright (c) 2009, Camron Flanders
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the developer nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY Camron Flanders ''AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL Camron Flanders BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
