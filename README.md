# Play ARD Mediathek Livestreams on the Unix Commandline

## Invocation with no arguments displays stations and current titles

```
$ mediathek
3sat          Der Kameramörder
alpha         Space Night
ard           Afrobeats - Rhythmus für die Metropolen der Welt
arte          28 Minuten
bayern        Sex
bremen        buten un binnen | regionalmagazin
deutschewelle Stimme Deutschlands)
hr            Wunderschön! Urlaub in Nordholland
mdr           MDR SACHSEN-ANHALT HEUTE
ndr           buten un binnen | regionalmagazin
one           Agatha Christie - Mörderische Spiele
phoenix       Die Gesten der Mächtigen
rbb           Donna Leon - Verschwiegene Kanäle
sr            Ein Fall von Liebe - Saubermänner
swr           Ein Fall von Liebe - Saubermänner
tagesschau    daten der woche
wdr           Wunderschön! Slowenien - Alpen mit Meerblick
```


## A passed channel is played in mpv multimedia player

```
$ mediathek arte &
arte           28 Minuten
<mpv opens with a video stream>
```

In mpv, press 'q' to quit and 'f' to enter or leave fullscreen mode.


## mediathek auto-completion

```
$ mediathek <tab><tab>
wdr            arte           deutschewelle  mdr            phoenix        swr
alpha          bayern         hr             ndr            rbb            tagesschau
ard            bremen         3sat           one            sr

$ mediathek b<tab><tab>
bayern bremen

$ mediathek ba<tab>yern
```


## International IP Addresses

Mediathek does not play geoblocked streams. This is not completely true: some streams which are geoblocked on the ARD mediathek website are actually not geoblocked and do nicely play in mediathek.

Mediathek plays streams which the ARD mediathek website fails playing with "Dieses Video kann leider nicht abgespielt werden. Wir bitten um Ihr Verständnis. Qualitätsauswahl für externen Player". This happens very often with my international IP address and is main reason why this project exist.

What probably goes without saying ist that mediathek does not play "Die derzeigte Sendung ist aus rechtlichen Gründen nicht im Livestream verfügbar."

Mediathek supports running over https proxies (see Configuration). A proxy from Germany should work around geoblocked content.


## Prerequisites

bash (for autocompletion), lynx (for downloading broadcast titles), mpv (for displaying video streams).

commit 673c93a5e80307a3bcf8ad5105425cb61760864b was the last commit requiring youtube-dl and ffplay. They have been now replaced with mpv.

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

Environment variable MEDIATHEK_QUALITY takes precedence over the hardcoded value from ~/.mediathekrc, e.g.

```
$ MEDIATHEK_QUALITY=1280 mediathek ard
```

A https/ssl proxy can be configured via environment variable https_proxy. e.g.

```
$ https_proxy=127.0.0.1:4001 mediathek ard
```


## Contributing

For contribution guidelines, see [CONTRIBUTING.md](./CONTRIBUTING.md).
