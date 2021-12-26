# GUI (v1.1)

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

1. Was ist das GUI-Skript?

2. Installation

3. Wie kann man das GUI-Skript nutzen?

4. Wieso bekomme ich bei den Attributen so eine seltsame Anzeige?

5. Wie kann ich die Position anpassen?


## 1. Was ist das GUI-Skript

DAS Skript erstellt aus den gmcp Daten über der Konsole eine Fläche in der
Level, die Lebens- und Konzentrationspunkte, sowie Statuswerte und
Rauminformationen angezeigt werden.

## 2. Installation

Das GUI-Skript ist ein Teil der Skript-Sammlung. Daher muss zur Nutzung
das Modul Mundron_Core.xml bereits installiert sein und dann nur noch
zusätzlich GUI.xml als Modul installieren und fertig. Die Module
könnt ihr im Mudlet installieren indem ihr Alt+I drückt oder im Menü auf
"Werkzeuge" geht und dort "Module" auswählt. Da klickt ihr auf
"Installieren", wählt die Datei aus und fertig! Möglicherweise muesst
ihr Mudlet einmal neustarten.


## 3. Wie kann man das GUI-Skript nutzen?

Sobald das Modul installiert und Mudlet neugestartet wurde, funktioniert das
Skript unmittelbar.


## 4. Wieso bekomme ich bei den Attributen so eine seltsame Anzeige?

Die Attributsanzeige ist dafür gedacht, dass man Unterschiede zu den
Normalwerten farblich unterlegt angezeigt bekommt. Dies hat den Vorteil, dass
man auf einem Blick erkennt, wenn eine Ausrüstung die Werte verbessert oder
verschlechtert oder ein Gegner eine Statusveränderung bei einem bewirkt hat.
Jedoch kann das Skript nicht wissen, was die Normalwerte sind, weswegen diese
manuell eingetragen werden müssen. Die kann man in der Konsole mit dem Befehl

    #attr <ausdauerwert> <intelligenzwert> <kraftwert> <geschickwert>

eingegeben werden. Die Reihenfolge ist genau die, wie sie auf der GUI
angezeigt wird. Sollte sich euer Normalwert dauerhaft verändert haben, so muss
dies wieder manuell angepasst werden.


## 5. Wie kann ich die Position anpassen?

Dazu gibt es nun eine Funktion, welche die Fensterposition anpasst und
speichert:

    #moveGUI (main|guild|exit) <delta x> <delta y>

Hier ist zu beachten, dass man entweder main, guild oder exit angibt um
das einzelne Fenster zu verschieben.
main
steht für das Haupt-GUI in der sich die Lebenspunkte-Anzeige befindet.
guild
steht für das Gilden-GUI, welches aktuell erstmal nur für Kleriker und
Werwölfe erscheint.
exit
steht für das Ausgangskreuz-GUI.

Zur Orientierung gilt: Positives delta x verschiebt das Fenster nach rechts
und positives delta y nach oben. Dabei darf die linke obere Ecke nicht die
Konsole verlassen, da ansonsten die gesamte GUI ausgeblendet wird.
