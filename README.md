# Play ARD Mediathek Livestreams on the Unix Commandline

## mediathek auto-completion:

```
$ mediathek <tab><tab>
wdr            arte           deutschewelle  mdr            phoenix        swr
alpha          bayern         hr             ndr            rbb            tagesschau
ard            bremen         3sat           one            sr
```


## no arguments displays the current broadcast titles:

```
$ mediathek
bayern:	Aufschrei der Jugend
wdr:	Shalom und Alaaf
alpha:	Weltspiegel-Reportage: Chinas neue Seidenstraﬂe
swr:	mal ehrlich ... Frauen in Not - wie stoppen wir h‰usliche Gewalt?
tagesschau:	Tagesthemen
ndr:	Groﬂstadtrevier
sr:	mal ehrlich ... Frauen in Not - wie stoppen wir h‰usliche Gewalt?
ard:	Tagesthemen
deutschewelle:	Stimme Deutschlands)
mdr:	Polizeiruf 110: Totes Rennen
hr:	Hessen lacht zur Fassenacht 2020
3sat:	Die verlorene Tochter (5/6)
phoenix:	phoenix der tag
one:	Mary Higgins Clark - Mysteriˆse Verbrechen (1)
arte:	Nanouk
bremen:	Groﬂstadtrevier
rbb:	Grenzbock
```


## Pass a channel to have it played in ffplay (press q to quit ffplay):

```
$ mediathek arte &
arte: Nanouk
<ffplay opens with a video stream>
```


## International IP Addresses

Mediathek does not play geoblocked streams. This is not completely true: some streams which are geoblocked on the ARD mediathek website are actually not geoblocked and do nicely play in mediathek.

Mediathek plays streams which the ARD mediathek website fails playing with "Dieses Video kann leider nicht abgespielt werden. Wir bitten um Ihr Verst‰ndnis. Qualit‰tsauswahl f¸r externen Player". This happens very often with my international IP address.

What probably goes without saying ist that mediathek does not play "Die derzeigte Sendung ist aus rechtlchen Gr¸nden nicht im Livestream verf¸gbar."


## Prerequisites

bash, lynx, youtube-dl, ffplay.


## Installation

> copy mediathek into your $PATH, say /opt/bin/

> copy .mediathekrc into your $HOME directory ~

> copy mediathekcompletion into /etc/bash_completion.d/

Note: the bashcompletion script is very helpful as it lists and auto-completes all stations. If it is not picked up automatically, then work around it by adding to your ~/.bashrc:

```
. /etc/bash_completion.d/mediathekcompletion
```


## Configuration

~/.mediathekrc MEDIATHEK_QUALITY_DEFAULT is setting the default video width to 960 pixels. It can be changed to higher or lower widths.

Environment variable MEDIATHEK_QUALITY overwrites the hardcoded value from ~/.mediathekrc, e.g.

```
$ MEDIATHEK_QUALITY=1280 mediathek ard
```


## Notes

The channel urls are hardcoded in ~/.mediathekrc. They are quite cryptic and may change from time to time. At the time of publishing this project, they have already been stable for one month.

Extracting the titles from the ARD mediathek website depends also very much on its cryptic html code.
