---
layout: default
---

# 2D Tutorial
Diese Wochen werden wir ein 2D Spiel mit der Gaming Engine Godot entwickeln.


![Branching](https://docs.godotengine.org/en/stable/_images/dodge_preview.gif)


[Teste das Eregebnis](https://html-classic.itch.zone/html/5531876/HTML/index.html){:target="_blank"}

## Vorbereitung

Bitte installiere folgende Tools:
* [Godot Engine](https://godotengine.org/download/windows/){:target="_blank"}
* [WinMerge](https://winmerge.org/downloads/?lang=de){:target="_blank"}

Bitte lade die Assets herunter:
* [Asset Bibliothek](https://godotengine.org/asset-library/asset/2712){:target="_blank"}

### WinMerge Einstellungen

Um die Ergebnisse nachher besser vergleichen zu können sind folgende Einstellungen notwendig:

Unter "Bearbeiten/Einstellungen" oder "Edit/Options" im Baum die Einstellungen zum Vergleichen suchen: 

"Vergleichen/Allgemein" oder "Compare/Generel" 

Dort sind folgende Einstellungen zu setzen:
* Leerzeichen -> Alle ignorieren oder Whitespaces -> Ignore all
* Leerzeilen ignorieren oder Ignore blank lines
* Ingore EOL differeneces

Unter Tools/Filter(s) lege bitte einen neuen Filter names Godot an. Danach öffnet sich die Konfiguration für diesen Filter.

Bitte ändere folgenden Konfiguration

```
f: \.ext$ ## Filter for filename

d: \\subdir$ ## Filter for directory
```

wie folgt ab:

```
f: \.import$ ## Filter for filename

d: \\.godot$ ## Filter for directory
```

Und speichere die Datei.

## Tutorial

Im Rahmen dieses Kurses werden wir folgendes Tutorial verwenden:
* [Tutorial 2D Spiel](https://docs.godotengine.org/de/4.x/getting_started/first_2d_game/index.html){:target="_blank"}

## Ergebnisse

Damit jeder Teilnehmer am Ende des Kurses ein lauffähiges Spiel zur Verfügung hat, stellen wir hier alle Teilergebnisse zur Verfügung.

### Teilergebnisse

| Schritt | Name des Schrittes | Download Link |
|:--------|:-------------------|:--------------|
| 1 | Einrichten des Projektes| [Ergebnis Schritt 1](https://markus1982.github.io/digicamp/downloads/schritt-1.zip) |
| 2 | Die Spieler-Szene erstellen | [Ergebnis Schritt 2](https://markus1982.github.io/digicamp/downloads/schritt-2.zip) |
| 3 | Den Spieler programmieren | [Ergebnis Schritt 3](https://markus1982.github.io/digicamp/downloads/schritt-3.zip) |
| 4 | Die Gegner erschaffen | [Ergebnis Schritt 4](https://markus1982.github.io/digicamp/downloads/schritt-4.zip) |
| 5 | Die Hauptszene des Spiels| [Ergebnis Schritt 5](https://markus1982.github.io/digicamp/downloads/schritt-5.zip) |
| 6 | Head-up-Display | [Ergebnis Schritt 6](https://markus1982.github.io/digicamp/downloads/schritt-6.zip) |
| 7 | Fertigstellung | [Ergebnis Schritt 7](https://markus1982.github.io/digicamp/downloads/schritt-7.zip) |

### Endergebnis

Hier noch der Original Source Code auf GitHub:

* [Fertiges 2D Spiel](https://github.com/godotengine/godot-demo-projects/tree/master/2d/dodge_the_creeps){:target="_blank"}


