# Play ARD Mediathek Livestreams on the Unix Commandline

## mediathek auto-completion:

```
$ mediathek <tab><tab>
wdr            arte           deutschewelle  mdr            phoenix        swr
alpha          bayern         hr             ndr            rbb            tagesschau
ard            bremen         3sat           one            sr
```


## Invocation with no arguments displays stations and current titles:

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


## Pass a channel to have it played in ffplay:

```
$ mediathek arte &
arte: Nanouk
<ffplay opens with a video stream>
```

In ffplay, press 'q' to quit and 'f' to enter or leave fullscreen mode.


## International IP Addresses

Mediathek does not play geoblocked streams. This is not completely true: some streams which are geoblocked on the ARD mediathek website are actually not geoblocked and do nicely play in mediathek.

Mediathek plays streams which the ARD mediathek website fails playing with "Dieses Video kann leider nicht abgespielt werden. Wir bitten um Ihr Verst‰ndnis. Qualit‰tsauswahl f¸r externen Player". This happens very often with my international IP address and is main reason why this project exist.

What probably goes without saying ist that mediathek does not play "Die derzeigte Sendung ist aus rechtlichen Gr¸nden nicht im Livestream verf¸gbar."


## Prerequisites

bash (for autocompletion), lynx (for downloading broadcast titles), youtube-dl (for downloading video streams), ffplay (for displaying video streams).


## Installation

> install all prerequisites

> copy mediathek into your $PATH, say /opt/bin/

> copy .mediathekrc into your $HOME directory

> copy mediathekcompletion into /etc/bash_completion.d/

Alternatively, link these files from the cloned git repo into these three directories.

Note: the bashcompletion script is very helpful as it lists and auto-completes all stations. If it is not picked up automatically, then work around it by adding to your ~/.bashrc:

```
. /etc/bash_completion.d/mediathekcompletion
```


## Configuration

In ~/.mediathekrc, variable MEDIATHEK_QUALITY_DEFAULT sets the video width to 960 pixels. This variable is user changeable and can be set to higher or lower widths.

Environment variable MEDIATHEK_QUALITY temporarily overwrites the hardcoded value from ~/.mediathekrc, e.g.

```
$ MEDIATHEK_QUALITY=1280 mediathek ard
```


## Contributing

For contribution guidelines, see [CONTRIBUTING.md](./CONTRIBUTING.md).


## Notes

The channel urls are hardcoded in ~/.mediathekrc. They are quite cryptic and may change from time to time. At the time of publishing this project, they have already been stable for one month.

Extracting the titles from the ARD mediathek website depends also very much on its cryptic html code.
