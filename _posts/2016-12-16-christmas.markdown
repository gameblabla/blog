---
layout: post
title:  "DellardOS 1.0 Rainbow Dash - Some history"
date:   2016-12-16 22:00:00
categories: dellardos linux
---
<p><img src="/images/dellardosscr1_0_o.png" width="480" />
DellardOS, the systemd-free Devuan distribution, is being resurrected !<br />
After so many months neglecting it, i have decided to revive it and fix some of its shortcomings.<br />
Unfortunately, requirements for the Live CD version has raised again due to some unresolved issues.</p>

<p>A minimal text installer version is planned in the near future.</p>

<p><b>After DellardOS became dormant…</b></p>

<p>The Linux desktop landscape is rapidly changing :</p>
<li>The growing monster known as systemd was adopted by many major distributions</li>
<li>Mesa has already reached OpenGL 4.5 compliance</li>
<li>Geforce Kepler GPUs are the last ones that do not require any firmware blobs</li>
<p><br />
The custom distro trend seems to be dying off as well…<br />
but it’s far from dead of course.</p>

<p>Due to numerous reasons, i stopped working on DellardOS and it became dormant.<br />
However… This happened :<br />
<a href="http://betanews.com/2016/10/07/systemd-vulnerability-linux-crash/">http://betanews.com/2016/10/07/systemd-vulnerability-linux-crash/</a></p>

<p>A vulnerability in systemd allowed hackers to take down (DDOS) any linux distributions with systemd.<br />
Actually, they eventually discovered it was a local-root exploit. * facepalm *</p>

<p>As you can see, the headline seems to be suggest the culprit was Linux, rather than systemd.<br />
Yum, victim-bashing at its finest…</p>

<p>In comparison, the only huge sysvinit vulnerability i know of dates all the way back to 2003.</p>

<p>systemd has grown so much, eating everything on his way, that it has now become a single point of failure, in theory and now in practice.</p>

<p>A lot of people have raised flags at systemd, on how it tries to become many things and replace them,<br />
but sadly, they don’t seem to have learned anything, quite the opposite in fact.</p>

<p>Now Linux users have to suffer from privacy issues, arbitrary wait times, an unnecessary complex design, increasing CPU/Memory usage…<br />
all of that for “supposedly” better boot times.</p>

<p>I actually measured the boot times on Ubuntu comparing Upstart and Systemd :
<b>Turns out systemd was much slower, especially with that stupid arbitrary wait delay on encrypted disks.</b> (1m and 30s !!!)</p>

<p>This isn’t progress, it’s worse than a giant step backward : it’s atrocious.</p>

<p><b>My experience with systemd-distros</b></p>

<p>Before i eventually decided to pick up DellardOS again, i had to look at this systemd-situation again.<br />
Ubuntu had switched to systemd in 16.04 so i installed that on my computer.<br />
Systemd is the worst in Ubuntu, worst than it ever was on Debian…</p>

<p>I had nothing but problems and issues with it.<br />
Installing an encryption partition without a swap partition will result in the installation being aborted</p>

<p><b>WHY ALL OF THIS ?</b></p>

<p>Then after installing it, i had to suffer from horrible boot times : rather than checking if the partitions was properly<br />
unmounted, systemd instead waits for 1m and 30s.<br />
This delay is absolutely arbitrary, it does absolute nothingness while this happen!</p>

<p>Needless to say the experience was less than good so i wanted to get rid of it as fast as possible.<br />
I installed upstart-sysv and removed as much systemd as i could.<br />
In the end, i had to build my own desktop because almost everything in the repo is now dependent on systemd…</p>

<p>Right after removing systemd and switching to upstart,<br />
i rebooted my computer and i noticed the boot times were now much better.<br />
So needless to say i don’t regret removing systemd, not even a bit.</p>

<p>Another bad experience with systemd was Manjaro and this was at a time<br />
when the OpenRC version was not redistributed.</p>

<p>After installing it, i had absolutely no network and i tried it on all of my computers.<br />
To install OpenRC, i needed to have an internet connection and download the equivalent of 200Mb of packages.</p>

<p>Needless to say, this was not going to go smoothly but then i discovered systemd’s ugly face in Manjaro :<br />
Since systemd introduces a dependency on applications compiled against it,<br />
Manjaro devs were forced to distribute two versions of the same software !<br />
This results in a huge confusing mess and makes it even less “user-friendly”.</p>

<p>Manjaro is awful, i did not enjoy using it.</p>

<p><b>And now, DellardOS…</b></p>

<p>I had previously released some older versions of <b>DellardOS</b> that were already systemd-free at the time… but they had several issues.
<br />
For one, no online repo was available for it meaning that each i make an update, i had to release an ISO with my slow connection.<br />
For two, the way it was built is broken and it did not rely on deb packages at all.</p>

<p>In version 0.4 for example, there was a bug that prevented <b>DellardOS</b> from being updated.
<img src="/images/dellardosscr2_0_o.png" width="480" />
Well…<br />
I’m happy to announce that this and more are now fixed in <b>DellardOS</b> version 1.0 “<b>Rainbow Dash</b>” !<br />
This version has one aim : Be stable while being fairly minimalist.</p>

<p>You still get the fast and lightweight JWM window manager with its custom menu specific to DellardOS.
One major “feature” is that DellardOS finally has it’s own signed repository, which means that it can now<br />
update DellardOS-specific features over the internet, something i was finally was to do.</p>

<p>The menu received also some improvements and you can now access any of your debian installed apps,<br />
just like you would when you first install JWM from the debian repository.</p>

<p>Another “nice” thing introduced is Firejail support for web browsers.<br />
If you start any of the 4 web browsers from the DellardOS menu,<br />
it will launch them with firejail and i can confirm it does limit privileges for apps.</p>

<p>This should make it harder for hackers to break out of the sandbox.</p>

<p>It’s no QubesOS but it’s a nice thing have, especially for browsers.
<img src="/images/scr2_0_o.png" width="480" />
Another thing added was KSM support, which should result in theory in decreased memory usage.<br />
However, it might also be bad for security as KSM don’t go along well with ASLR. (Debian doesn’t have ASLR by default)</p>

<p>I will add the ability to disable it from the menu in the near future.</p>

<p>Not all is good though, i had to increase the minimal requirements to 160 MB of RAM because bootcd would not complete the installation if it does not have enough memory.</p>

<p>Unfortunately, the only workaround is to either install from another computer or increase the RAM available. (not always possible, granted)<br />
I might do a text-only installer version so we can work around this.</p>

<p><b>WARNING:
<br />
DELLARDOS WILL DELETE EVERYTHING ON YOUR COMPUTER.</b><br />
<b>IF YOU HAVE SEVERAL HARDDRIVES, DISCONNECT THE ONE YOU DON’T WANT DELLARDOS TO BE INSTALLED TO !</b></p>

<p>You can download DellardOS here:<br />
<a href="https://dellardos.gameblabla.nl/downloads.htm">https://dellardos.gameblabla.nl/downloads.htm</a></p>
