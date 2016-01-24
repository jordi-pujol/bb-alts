# bb-alts
Debian package that installs alternatives to busybox applets

Description

*bb-alts* is a package that installs alternatives to busybox 
internal applets, adding some useful utilities to the system.

Detects existing Debian alternatives from other packages and installs 
the corresponding busybox applet as another alternative, installing 
also man pages for each one; man pages are linked to the *busybox* 
man page.

Before installing alternatives, *bb-alts* removes all alternatives that 
point to busybox and the helper programs installed by bb-alts.

The file /etc/bb-alts.conf lists the busybox applet names that 
*bb-alts* will consider as candidates for installing an alternative.

It's recommended to install only alternatives that are also installed 
as alternatives by the other packages. However *bb-alts* can install 
alternatives for any busybox applet, so we are able to install as 
Debian alternatives a lot of useful busybox utilities.

Some packages do not install Debian alternatives for some utilities 
that are also provided by busybox, in this case the alternatives 
installed by *bb-alts* may conflict with other files; 
therefore some problems may arise and the superuser must be aware of 
that.

*bb-alts* will not install an utility when there is already another 
file in the corresponding location.

Before installing a new package that provides an executable file on the 
same location that a busybox alternative, the superuser must remove the 
alternatives installed by *bb-alts*, let's execute: 
*bb-alts* --deconfigure ; therefore install the new package and 
reconfigure *bb-alts*.

On the other side, after removing a package that provides some utility 
that is also in busybox we must reconfigure *bb-alts*, that will 
install the corresponding alternatives activating the utility from the 
*busybox* internal applet.

*****************************************************
main procedures:

_remove_alternatives :
	Removes all the alternatives that point to /bin/busybox
and the alternative named "editor" pointing to /usr/bin/vi-busybox.

_busybox_utilities :
	Installs alternatives for some busybox utilities,
detects existing alternatives from other packages
and avoids conflicts with already installed packages.

*****************************************************
Comments:

Some of the Busybox utilities are already known Debian alternatives,
"awk,mawk pager lzma,lzcat,unlzma mt telnet traceroute traceroute6 vi editor"
other may be executable files installed by other packages.

Some alternatives have needed some additional coding due to the special 
use of "nawk", "editor" and "pager".

In the near future the packages that conflict with the most useful 
busybox utilities may be modified to install alternatives. When the 
functionality of the busybox applets is enough to make the work 
successfully we should modify *bb-alts* to install the 
corresponding alternative.

Can not install alternatives over existing executable files; we may 
create a diversion for the original executable file and install in that 
location an alternative for a busybox utility but it is difficult and 
not reliable.

aptitude search '?provides(lzma)'
Provides: awk
Provides: mt, from cpio package
Provides: telnet-client
Provides: traceroute
Provides: editor, vi
Provides: lzma

ftpget and ftpput are bonus utilities, not provided by other packages
***********************************
bb-alts.conf
