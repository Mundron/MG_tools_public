# EK-Tracker (v3)

~ dieses README ist noch im Entstehen, enthält aber schonmal ein paar
nützliche Informationen. Bei Unklarheiten einfach mich in Morgengrauen
anschreiben, danke. ~

Dieses Skript ist in Lua fürs [Mudlet](https://www.mudlet.org/) geschrieben.
Das Skript habe ich fuer mich selbst zur Nutzung in
[Morgengrauen](http://mg.mud.de) erstellt, so dass gewisse Rahmenbedingungen
erfuellt sein muessen, siehe Installation. Generell ist es aber auch auf
andere Spiele uebertragbar. Allerdings ist dazu zu erwaehnen, dass dieses
Skript Daten aus gmcp.MG.char benutzt. In anderen Spielen wird die
Datenstruktur von gmcp moeglicherweise anders sein, so dass diese Stellen
angepasst werden muessten.

### Inhaltsverzeichnis

1. Was ist der EK-Tracker?

2. Installation

3. Wie kann man den EK-Tracker benutzen?


## 1. Was ist das EK-Tracker

Das Skript ist dafuer gedacht sich NPCs mit Namen, Ort, Region, Magier,
Hinweis und Parallelwelt zu speichern um eine Uebersicht zu haben.
Insbesondere sind dabei die NPCs spannend, die Erstkillpunkte (EKs)
beim ersten Toeten vergeben. Und gerade diese NPCs sind der Hauptgrund fuer
dieses Skript, denn zusaetzlich zur einfachen Auflistung der NPCs kannst du
auch markieren wann du welchen EK erhalten hast. Falls du sogar die
Plakette aus der Para-Duesterwald-Quest hast, kannst du mit Mitspielern die
Plakette vergleichen, welches mit Datum und Differenz zum vorigen Vergleich
gespeichert wird.


## 2. Installation

Der EK-Tracker ist ein Teil der Skript-Sammlung. Daher muss zur Nutzung
das Modul Mundron_Core.xml bereits installiert sein und dann nur noch
zusätzlich EK-Tracker.xml als Modul installieren und fertig. Die Module
könnt ihr im Mudlet installieren indem ihr Alt+I drückt oder im Menü auf
"Werkzeuge" geht und dort "Module" auswählt. Da klickt ihr auf
"Installieren", wählt die Datei aus und fertig! Möglicherweise muesst
ihr Mudlet einmal neustarten.


## 3. Wie kann man den EK-Tracker benutzen?

Sobald das Modul installiert und Mudlet neugestartet wurde, funktioniert das
Skript unmittelbar. Um im Spiel eine Uebersicht ueber die Funktionen zu
erhalten, gibt man im Spiel
    #EK
fuer eine kurze Uebersicht der Befehle mit ihrere Syntax ein oder
    #EK -v
fuer die selbe Uebersicht, welcher mit kurzen Beschreibungen ergaenzt wurde.
