---
layout: default
---

# 2D Tutorial
Diese Wochen werden wir ein 2D Spiel mit der Gaming Engine Godot entwickeln.


![Branching](https://docs.godotengine.org/en/stable/_images/dodge_preview.gif)


[Teste das Eregebnis](https://markus1982.github.io/digicamp/game){:target="_blank"}

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

## Erweiterung Wall

Teste wieder zu Beginn das Ergebnis:

[Spiel mit Hinderniss](https://markus1982.github.io/digicamp/wall){:target="_blank"}

Um die Wand zu ergänzen gibt es folgende Hilfestellungen:
* [Wandbilder](https://de.freepik.com/vektoren-kostenlos/sammlung-von-sechzehn-nahtlose-vektor-pixel-bodentexturen_959312.htm){:target="_blank"}

Die Hauptfunktion für den Player:

```
func _on_body_shape_entered(_body_rid: RID, body: Node2D, static_body_2d_index: int, area_2d_index: int) -> void:
	# check if colliding body is a wall, in this case I used groups, but you can also check it any other way
	if not body.is_in_group("Wall"):
		return
	
	# check if the plant is already being repositioned, so that it doesn't loop when colliding with more than 1 wall
	if is_repositioning:
		return
	is_repositioning = true
	
	$AnimatedSprite2D.stop()
	
	# assign shapes to check collisions
	var static_body_2d_id: int = body.shape_find_owner(static_body_2d_index)
	var static_body_2d_owner: CollisionShape2D = body.shape_owner_get_owner(static_body_2d_id)
	#var parent : StaticBody2D=body_shape_owner.get_parent();
	var static_body_2d: Shape2D = body.shape_owner_get_shape(static_body_2d_id, static_body_2d_index)
	var area_2d_owner_id: int = shape_find_owner(area_2d_index)
	var area_2d_shape_owner: CollisionShape2D = shape_owner_get_owner(area_2d_owner_id)
	var area_2d_shape: Shape2D = shape_owner_get_shape(area_2d_owner_id, area_2d_index)
	
	# check which direction to move the player
	var direction_x: float = static_body_2d_owner.global_position.x - area_2d_shape_owner.global_position.x
	var direction_y: float = static_body_2d_owner.global_position.y - area_2d_shape_owner.global_position.y
	# move the plant by 1 pixel, until it doesn't collide with the wall anymore
	while area_2d_shape.collide(area_2d_shape_owner.global_transform, static_body_2d, static_body_2d_owner.global_transform):
		if direction_x < 0:
			global_position.x += 1
		else:
			global_position.x -= 1
		if direction_y < 0:
			global_position.y += 1
		else:
			global_position.y -= 1
	
	is_repositioning = false
```

Vergiss nicht die Variable is_repositioning zu erstellen und in der Methode _on_body_entered folgende Überprüfung zu ergänzen:

```
if not body is StaticBody2D:
```

[Ergebnis zum 2D Spiel mit Wand](https://markus1982.github.io/digicamp/downloads/wall.zip)

