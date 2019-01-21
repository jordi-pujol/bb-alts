# bb-alts
Debian package that installs alternatives for busybox applets

Description

*bb-alts* is a package that installs alternatives for busybox 
internal applets, allowing easy use of this applets in the system.
When enabled, *bb-alts* also installs alternatives for commands
that are not Busybox applets

Detects existing Debian alternatives from other packages and installs 
the corresponding busybox applet as another alternative, also installs
man pages for each one; man pages are linked to the *busybox* man page.

The file /etc/bb-alts.conf configures the candidate alternatives that 
*bb-alts* will consider for installing.

It's recommended to install only alternatives that are also installed 
as alternatives by the other packages. However *bb-alts* can install 
alternatives for any busybox applet, so we are able to install as 
Debian alternatives a lot of useful busybox utilities.

Some packages do not install Debian alternatives for those utilities 
that are also provided by busybox, in this case the alternatives 
installed by *bb-alts* may conflict with other files; some problems
may arise and the superuser must be aware of that.

*bb-alts* will not install an utility when there is already another 
file in the corresponding location.

Before installing a new package that provides an executable file on the 
same location that a busybox alternative, the superuser must remove the 
conflicting alternatives.

On the other side, after removing a package that provides an utility 
that is also in busybox we must reconfigure *bb-alts* and install
the corresponding alternatives activating the utility from the 
*busybox* internal applet.

*****************************************************
Comments:

Some of the Busybox utilities are already known Debian alternatives,
"awk,mawk pager lzma,lzcat,unlzma mt telnet traceroute traceroute6 vi editor"

Some alternatives have needed additional coding due to the special use of
"nawk", "editor" and "pager".
