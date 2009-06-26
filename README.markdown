BOXSTRAP
========

An automated bootstrapping script to configure/install an environment located on a Dropbox.
by Camron Flanders <camron[dot]flanders[squiggly-at-symbol]gmail[dot]com>

A bootstrap script used to automate the install a set of environment configurations, apps, and crontab entries.

I have done my best to document the script as thouroghly as possible -- please read it for further information regarding the settings beyond what is in this quick readme. I have also done my best to note where I feel there are improvements to be made, the script was created, tested, and finished in under an hour - not including this documentation. If you have any additions, improvements, bugs, or anything else please feel free to report, fix, or fork this project.

TO_USE
======

Is this script at the root of your dropbox?
-------------------------------------------

Add your paths to `PATHS_TO_PROCESS` list in the script and run with `DRY_RUN` set to *True*.

Is the output correct?
----------------------

**YES?** *Sweet!* Set `DRY_RUN` to *False* and run it again!

**No?** Setup some configuration files for directory-level override of defaults *OR* maybe you need to change the defaults?

Do you have a custom crontab?
-----------------------------

If you do, add it's path to `CRONTAB` and we'll add it to your system crontab.

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
