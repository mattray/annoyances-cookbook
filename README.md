Description
===========

Removes a number of operating system based annoyances. There are
recipes RHEL and Debian platform families.

Feel free to fork and submit your own patches.

Requirements
============

## Platform

Supports `rhel`, `debian`, and `omnios` platform families.

* Debian, Ubuntu
* Red Hat, CentOS, Scientific, Oracle, Amazon, Fedora
* OmniOS

If your Chef/Ohai version aren't new enough for the
`node['platform_family']` attribute, then simply include the
platform-specific recipe.

Recipes
=======

## default

Looks at the node's `platform_family` and includes the proper recipe.

If the node's `platform_family` is not found, an exception will be
raised.

## rhel

Removes any preexisting firewall rules, turns off SELinux, uninstalls
httpd if it's on for some reason and removes /root/.bash_logout if it
exists. Turns off desktop services autofs, avahi-daemon, bluetooth,
puspeed, cups, gpm, haldaemon and messagebus.

If the `apache2` recipe is on the node, the httpd package will not be
removed.

## fedora

Includes `annoyances::rhel`.

## debian

Does an "apt-get update" and turns off apparmor and byobu (unless you
want it). Removes whoopsie, popularity-contest and unity-lens-shopping
if this ever got on a server.

## ubuntu

Includes `annoyances::debian`.

## omnios

Includes `annoyances::omnios`, which refreshes the package list and
publisher metadata.

Usage
=====

Include the `annoyances` recipe in your run list and it will make the
various changes based on the node's platform family. You can also
include the platform specific recipe directly.

License and Author
==================

Author:: Matt Ray (<matt@getchef.com>)
Author:: Joshua Timberman (<joshua@getchef.com>)

Copyright 2012-2013 Opscode, Inc.
Copyright 2013-2014 Chef Software, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
