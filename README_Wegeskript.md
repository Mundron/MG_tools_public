# Wegeskript (v1.21)

Dieses Skript ist in Lua fürs [Mudlet](https://www.mudlet.org/) geschrieben.
Das Skript habe ich fuer mich selbst zur Nutzung in [Morgengrauen](http://mg.mud.de) erstellt, so dass gewisse
Rahmenbedingungen erfuellt sein muessen, siehe Installation. Generell ist es aber auch auf andere Spiele uebertragbar.
Allerdings ist dazu zu erwaehnen, dass dieses Skript Daten aus gmcp.MG.char benutzt. In anderen Spielen wird die Datenstruktur
von gmcp moeglicherweise anders sein, so dass diese Stellen angepasst werden muessten.

### Inhaltsverzeichnis

1. Was ist das Wegeskript

2. Installation

3. Wie kann man das Wegeskript nutzen?

4. Wichtiges zu Updates des Wegeskriptes

      4.1. Das Wegeskript wurde geupdatet. Muss ich nun wieder alle Punkte speichern um die neue Version zu nutzen?

      4.2. Was hat sich  mit Version v1.1 geaendert?

      4.3. Was hat sich  mit Version v1.2 geaendert?

      4.4. Plaene fuer Version v1.3 (bisher)

5. Wegaufzeichnung / Wie speichere ich Punkte fuer das Wegeskript?

     5.1. Basispunkt

     5.2. Wegaufzeichnung

     5.3. Automatisch speichernde Bewegung/Aktion anzeigen und anpassen

     5.4. Anzeige des bisher aufgezeichneten Weges

     5.5. Korrektur falsch eingegebener manueller Bewegungsaktionen

     5.6. Punkt/Wegaufzeichnung speichern

     5.7. Speichern nur des Hinweges oder nur des Rueckweges

     5.8. Tipps/Tricks fuer effektive Wege

6. Welcher Char nutzt welche Wege? Gemeinsame und unterschiedliche Wege.

7. Reisen mit dem Wegeskript

    7.1. Wie kann ich nun von Punkt A nach B gelangen?

    7.2. Wie kann ich nachschauen welchen Weg ich eben gelaufen bin?

8. Bearbeitung von gespeicherten Punkten

     8.1. Namen aendern

     8.2. ID auslesen, hinzufuegen oder loeschen

     8.3. Titel aendern

9. Gespeichtern Punkt loeschen

10. Suchfunktion fuer die gespeichten Punkte

11. Externe Speicherung der Wege mit automatischem monatlichen Backup

12. Super-Safe-Modus

13. Raummeldungen entlang des Weges weggaggen (v1.1)

      13.1. Anzeigen der Gags (v1.2)

      13.2. Hinzufuegen von Gags (v1.2)

      13.3. Loeschen von Gags (v1.2)

14. Hilfefunktion im Spiel (v1.1)


## 1. Was ist das Wegeskript

Das Wegeskript ermoeglicht schnelles Reise zwischen beliebigen gespeichtern Punkten im Spiel. Es gibt sogar eine Syntax, bei der man nur das Ziel eingeben muss und das Skript automatisch erkennt, wenn man sich an einem gespeicherten Ort befindet um dann den Weg zum Ziel zu finden.

## 2. Installation

    Das Wegeskript ist ein Teil der Skript-Sammlung. Daher muss zur Nutzung 
    das Modul Mundron_Core.xml bereits installiert sein und dann nur noch 
    zusätzlich Wegeskript.xml als Modul installieren und fertig. Die Module 
    könnt ihr im Mudlet installieren indem ihr Alt+I drückt oder im Menü auf 
    "Werkzeuge" geht und dort "Module" auswählt. Da klickt ihr auf 
    "Installieren", wählt die Datei aus und fertig! Möglicherweise muesst 
    ihr Mudlet einmal neustarten.

    Nun könnt ihr verschiedene Dateien anlegen, da fuer Seher andere Wege 
    durch Portale moeglich sind, wie Nichtsehern. Aktuell wird eine Datei 
    mit dem Namen "Wege.txt" erstellt, in der die Wege gespeichert werden.
    Wollt ihr verschiedene Profile anlegen, die verschiedene Dateien 
    benutzen sollen, dann muss aktuell eine andere Datei im Skript 
    geaendert werden, naemlich im Element "Core" in Zeile 10 steht:

        PF = PF or {filename="Wege",

    Wenn ihr hier "Wege" durch etwas anderes ersetzt, dann wird fuer das 
    Profil die entsprechen andere Datei benutzt oder angelegt, wenn es noch
    keine gibt.

## 3. Wie kann man das Wegeskript nutzen?

 Es gibt schon einige vorgefertigte Aliase im Skript, die ihr benutzen
 koennt. Wenn ihr im Spielt \#WS eingebt, erscheint eine Liste der 
 moeglichen Befehle und auch, wie man mit der Hilfsfunktion Details
 zu den Befehlen bekommt.

 Grundsetzlich muessen natuerlich die Punkte im Spiel gespeichert werden 
 zwischen denen man schnell reisen moechte. Dazu beeinhaltet das Wegeskript
 auch eine Wegaufzeichnung. 

 Ein wesentliches Konzept dieses Wegeskriptes, dass man sich in einem Gebiet
 einen zentralen Punkte auswaehlt, sozusagen einen Basispunkt. 
 Und dann speichert man sich einen Punkt indem man den Hin- und Rueckweg vom Basispunkt
 zum neuen Punkt aufzeichnet (mit dem Skript, siehe weiter unten). 
 Wenn man dann von Punkt A nach B reisen will, dann laeuft das 
 Wegeskript von A zum Basispunkt und dann vom Basispunkt nach B. 
 Damit braucht man lediglich zwei Wege pro gespeicherten Punkt
 zu sichern.

 Natuerlich gibt es auch Orte, von von diesem Basispunkt aus
 nicht mit dem Skript erreichbar sind. Zum Beispiel Orte,
 die man nur mit Gefaehrten, wie Schiffe, erreichen kann.
 Man muss auch dort das Wegeskript nutzen! Dazu muss man
 sich lediglich in jedem getrennten Gebiet einen neuen
 Basispunkt auswaehlen. Das Wegeskript ist auch in der
 Lage zu erkennen, ob man sich an einem gespeicherten
 Punkt befindet, so dass man nur den Zielpunkt eingeben muss.

## 4. Wichtiges zu Updates des Wegeskriptes

### 4.1. Das Wegeskript wurde geupdatet. Muss ich nun wieder alle Punkte speichern um die neue Version zu nutzen?

 Nein, das Wegeskript wurde bewusst so geschrieben, dass alle
 Wege in einer Textdatei im Arbeitsordner gespeichert werden.
 Wenn du das Skript als Modul geladen hast, reicht es auch die
 Datei auszutauschen, bzw wenn du git nutzt und die Datei aus 
 dem Repository laedst, kannst du mit git pull die Skripte 
 aktualisieren. Moeglicherweise ist aber ein Neustart des 
 Mudlets notwendig.

### 4.2. Was hat sich  mit Version v1.1 geaendert?

  Zum einen wurden ein Paar Bugs ausgebessert, die sich erst im Laufe der Nutzung zeigten:
  - Loeschen von IDs werden nun tatsaechlich ausgefuehrt
  - Speichern von Wegen sollte nun klappen
  - Anzeige von der Wegaufzeichnung ist nun in der richtigen Reihenfolge

  Es gibt aber auch zwei neue Funktion:
  - Funktion zur Anzeige des zuletzt gelaufenen Weges, siehe 7.2.
  - Hilfefunktion im Spiel, siehe 14. In erster Ebene als Syntaxhilfe nutzbar, aber detailiertere Hilfe mit Beispielen zu den Funktionen ist ebenfalls moeglich!

  Und auch zwei neue Features sind zu verzeichnen:
  - Raummeldungen entlang des Weges kann gegaggt werden, siehe 13.
  - Wegaufzeichnung erkennt manuelle Richtungseingabe von Standardrichtungen automatisch, siehe 5.3. Damit ist man nicht gezwungen mein "evented navigation" zu nutzen, welches die Wegaufzeichnung mit dem Nummerfeld steuert.

### 4.3. Was hat sich  mit Version v1.2 geaendert?

  Behobene Bugs:
  - beim Speichern eines Weges wird nun die richtige Raum-ID gespeichert.
  - Fehlendes Anfordern von gmcp-Pakete hinzugefuegt.

  Neue Funktionen:
  - Wegaufzeichnung Typ 2 hinzugefuegt, siehe
  - Unterdrueckte Raummeldungen bei Reisen werden in einer externen Dateie gespeichert und kann nun flexibel angepasst werden, siehe Unterpunkte von 13..
  - Automatisch erkannte Bewegungs bei der Wegauchzeichnung ist nun ebenfalls dynamisch anpassbar, siehe Unterpunkte von 5.3..

### 4.4. Was hat sich  mit Version v1.21 geaendert?

  - Inklusion des Wegeskriptes als Teil eines Skript-Pakets
  - Wegaufzeichnung Typ 1 entfernt

### 4.5. Plaene fuer Version v1.3 (bisher)

  - Alle Bugs erschlagen, die in der Zwischenzeit auftauchen
  - Verwaltungssystem fuer die gespeicherten Wege und Gags um diese zwischen Dateien hin und her zu kopieren und sie nach Wunsch je Profil zu personalisieren.
  - Einstellungsverwaltung bei der Einstellungen im Spiel gesteuert werden koennen, so wieder Super-Safe-Modus oder die Dateinamen.
  - sinnvolle Vorschlaege/Wuensche von dir umsetzen :-)

## 5. Wegaufzeichnung / Wie speichere ich Punkte fuer das Wegeskript?

 Grundsaetzlich startet man entweder am Basispunkt oder einem bereits 
 gespeicherten Wegpunkt, startet die Wegaufzeichnung, laeuft zum Ziel,
 gibt ein, dass es der Zielpunkt ist, laeuft zurueck und speichert sich
 das als neuen Weg ein. Und das war es auch schon im Prinzip.

### 5.1. Basispunkt

 Der Basispunkt ist ein Bezugspunkt, der aber nicht gesondert gespeichert oder erwaehnt werden muss. Du musst fuer dich
 selbst bestimmen wo der Basispunkt sein soll. Was letztendlich gespeichert wird ist ein Hin- und Rueckweg zu einem Punkt.
 Der Wegeskript geht automatisch davon aus, dass der Rueckweg immer zu einem Basispunkt fuehrt. Deswegen ist es kein Problem
 in verschiedenen Gebieten auch unterschiedliche Basispunkte zu benutzen.

#### 5.2. Wegaufzeichnung

  Fuer die Wegaufzeichnung sind folgende Befehle direkt im Spiel nutzbar:

             #wa start
             #wa stop
             #wa weiter
             #wa ziel

  Wir beginnen entweder an einem Basispunkt oder einem anderen Wegpunkt
  und starten die Wegaufzeichnung mit 

             #wa start

  Nun werden vom Skript Aliase fuer die Standardhimmelsrichtungen

    n, norden, nordunten, nordoben, 
    no, nordosten, nordostunten, nordostoben,
    o, osten, ostunten, ostoben,
    so, suedosten, suedostunten, suedostoben,
    s, sueden, suedunten, suedoben,
    sw, suedwesten, suedwestunten, suedwestoben,
    w, westen, westunten, westoben,
    nw, nordwesten, nordwestunten, nordwestoben,
    ob, oben, 
    u, unten, 
    raus
 
  angelegt. Die Liste kann aber, siehe 5.3, ergaenzt werden. 
  Wenn ihr also diese Richtungen benutzt, wird das vom
  Skript automatisch gespeichert.
  **ACHTUNG**
  Das funktioniert nur, wenn ihr diese Richtungen eintippt!
  Wenn ihr ueber eine Tastenbelegung arbeitet, dann 
  funktioniert das nicht.

  Falls nun eine andere Eingabe fuer das Vorankommen benoetigt
  wird, ist das auch kein Problem, dabei hilft

             #vor <Aktion>
  
  welches nicht nur die Bewegung speichert, sondern auch ausfuehrt.

  Wenn wir am Ziel angekommen sind, wo der neue Wegpunkt entstehen soll,
  dann geben wir

             #wa ziel

  ein. Damit wird der Endpunkt gespeichert. Nun gehen wir zurueck
  zum Startpunkt und beenden die Aufzeichnung mit 

             #wa stop

Kleines Beispiel:

Wir wollen eine Weg beginnenden bei einem Knoten starten zu einem Haus, bei dem wir auch ordentlich das Haus und die Tuer oeffnen und hinter uns schliessen wollen.

             #wa start
             osten
             norden
             nordwesten
             #vor schliesse haus auf
             #vor oeffne tuer
             #vor betrete haus
             #vor schliesse tuer
             #vor schliesse haus ab
             #wa ziel     -- wir sind im Haus, hier soll der Weg enden!
             #vor schliesse haus auf
             #vor oeffne tuer
             raus
             #vor schliesse tuer
             #vor schliesse haus ab
             suedosten
             sueden
             westen
             #wa stop

 Anschliessend kann der neue Weg gespeichert werden.

#### 5.3 Automatisch speichernde Bewegung/Aktion anzeigen und anpassen

  Da ihr moeglicherweise die in 5.2. beschriebe Liste an automatisch 
  erkennbaren Bewegungsaktionen erweitert habt, wollt ihr vielleicht 
  nachschauen, welche gespeichert wird. Dies ist moeglich mit dem Befehl

             #zeigedir

  Damit werden alle nummeriert aufgelistet.
  Wollt ihr nun eine Bewegungsaktion/Richtung hinzufuegen, 
  die ihr oft benutzt oder fuer wichtig erachtet? Dann kann man das mit

             #adddir <aktion>

  erreichen. Dabei muss die Aktion zwingend aus einem Wort bestehen. 
  Andernfalls muesst ihr leider das manuell eintragen.

 Beispiel:

             #adddir rechts

  Speichert die Richtung "rechts", was dann bei der
  Wegaufzeichnung automatisch erkannt wird.

  Wenn ihr euch vertan habt, koennt ihr auch eine gespeicherte
  Aktion wieder loeschen. Dazu benoetigt ihr aber die Nummer der
  Aktion, die ihr mit der Anzeige, siehe 5.3.1. erhaltet. Der Befehl lautet

             #deldir <nummer>

  Jedoch koennt ihr nur Aktionen loeschen, die ihr hinzugefuegt habt. 
  Die Aktionen 1 bis 37 sind Standardrichtungen, die nicht loeschbar sind.

Beispiel:

             #deldir 38

Loescht die 38. gespeicherte Aktion.


### 5.4. Anzeige des bisher aufgezeichneten Weges

Mit dem Befehl

           #zeigewa <anzahl>

kann man sich die letzten \<anzahl> gespeicherten Bewegungsaktionen sowohl vom Hin- als auch dem Rueckweg anzeigen lassen.
Gibt man als Anzahl 0 ein, dann wird der gesamte aufgezeichnete Weg angezeigt.

Beispiel:

           #zeigewa 5

Zeigt die letzten 5 gespeicherten Bewegungsaktionen.

### 5.5. Korrektur falsch eingegebener manueller Bewegungsaktionen

Mit

           #lvor <anzahl>
           #lzurueck <anzahl>

werden die letzten \<anzahl> viel Bewegungsaktionen geloescht.

Beispiel:

           #lvor 3

Loescht die letzten 3 Bewegungsaktionen vom Hinweg.

### 5.6. Punkt speichern

Hat man mit der Wegaufzeichnung den zu speichernden Weg abgelaufen, dann kann man folgende Befehle zum Speichern nutzen:

           #sweg <name>
           #sweg <name> <startpunkt>
           #sweg <name>-z
           #sweg <name> <startpunkt>-z
           #sweg <name>:<titel>
           #sweg <name> <startpunkt>:<titel>
           #sweg <name>-z:<titel>
           #sweg <name> <startpunkt>-z:<titel>

 *WICHTIG:* Zwischen den Namen und dem Startpunkt muss ein Leerzeichen stehen, aber die Benutzung von -z oder :\<titel>
     muessen zwingend ohne Leerzeichen gemacht werden! Daher bitte genau auf die Syntax achten, siehe die Beispiele:

           #sweg sandtiger
           #sweg polartiger moulokin
           #sweg sandtiger-z
           #sweg polartiger moulokin-z
           #sweg sandtiger:Der Sandtiger beim Wettpalast am Westeingang von Port  Vain
           #sweg polartiger moulokin:Der Polartiger westlich von Moulokin
           #sweg sandtiger-z:Der Sandtiger beim Wettpalast am Westeingang von Port Vain
           #sweg polartiger moulokin:Der Polartiger westlich von Moulokin

 Generell ist zu empfehlen eher kurze Namen zu geben um diese schnell eingeben zu koennen. Fuer "Sandtiger" waere auch "st"
 moeglich. Namen koennen eine beliebige Kombination aus Zahlen und Buchstaben sein.

 Wie zu sehen ist, gibt es 4 verschiedene Parameter die man in allen Kombinationen an den Befehl weitergeben kann.
 Der Name muss aber immer dabei sein. Klar, der neue Punkt muss einen eindeutigen noch nicht benutzten Namen haben,
 damit man benennen kann wohin man moechte.

 Gibt man zusaetzlich einen Startpunkt mit an, dann geht die Wegaufzeichnung davon aus, dass der aufgezeichnete Weg von
 diesem Startpunkt zum neuen Punkt ist. Ohne den Startpunkt wird der Weg als vom Basispunkt ausgehend angenommen.
 Der Parameter z muss genutzt werden, wenn man den Weg nicht vom Basispunkt zum neuen Punkt aufgezeichnet hat, sondern
 umgekehrt und die Wegaufzeichnung das umdrehen muss um es richtig zu speichern. Wird es weggelassen, dann geht es davon aus,
 dass die Wegaufzeichnung den Weg vom Basispunkt zum neuen Punkt gespeichert hat.

 Schliesslich ist der Titel auch ein optionaler Parameter, denn damit kann man bestimmen ob man den neuen Punkt
 nur temporaer, also bis zum Schliessen des Profils, oder dauerhaft speichern moechte. Gibt man keinen Titel an,
 dann ist der Weg nur temporaer gespeichert und geht verloren. Gibt man einen Titel an, dann wird der Weg auch in der
 externen Textdatei gespeichert. Sollte man einen Weg temporaer gespeichert haben und dann doch beschliessen, diesen
 dauerhaft speichern zu wollen, dann kann man dies noch nachholen indem man den Speicherbefehl erneut mit einem Titel eingibt.


### 5.7. Speichern nur des Hinweges oder nur des Rueckweges

Es kann auch sein, dass notwendig ist, dass nur der Hinweg oder nur der Rueckweg gespeichert ist. Dies kann der Fall sein,
wenn man von durch irgendwas in einem Raum gelangt von der man zwar weg will, aber eigentlich nicht hinlaufen oder wenn man dort ist, vielleicht einen ganz anderen Weg fuer den Rueckweg braucht und daher beide Wege lieber getrennt aufnehmen will.
Dazu starte man die Wegaufzeichnung wie gewohnt und lauft einmal den zu speichernden Weg entlang, wie oben beschrieben.

Nennen den Basispunkt B und einen interessanten Punkt X. Wenn wir nur den Hinweg, also den Weg von B nach X speichern wollen,
dann laufen starten wir mit der Wegaufzeichnung bei B und laufen nach X. Nun koennen wir folgende Befehle, aehnlich wie bei 5.6.
zum Speichern des Hinweges benutzen:

           #sebs <name>
           #sebs <name> <startpunkt>
           #sebs <name>:<titel>
           #sebs <name> <startpunk>:<titel>

 Es gelten hier die selben Syntaxregeln, wie auch bei 5.6. Der Name "sebs" steht fuer "speichere Einbahnstrasse",
 da nur die eine Richtung gespeichert werden soll. Aber selbstverstaendlich kann sich jeder die Namen der Aliase anpassen
 wie es besser gefaellt.

 Wollen wir nur den Rueckweg festhalten, also den Weg von X nach B, dann starten wir die Wegaufzeichnung bei X und nehmen
 den Weg nach B auf. Die Befehle zum Speichern sind die selben, nur dass noch der Parameter -z dazu kommt, also

           #sebs <name>-z
           #sebs <name> <startpunkt>-z
           #sebs <name>-z:<titel>
           #sebs <name> <startpunk>-z:<titel>



### 5.8. Tipps/Tricks fuer effektive Wege

Trick 1:
Das Zentrum muss an sich erstmal nicht benannt werden. Es muessen nur alle Punkte einen Weg zum Zentrum hin und zurueck haben.
Aber vielleicht ist es ja auch dennoch ein wichtiger Ort zu dem man gleichzeitig oft reisen will? Kein Problem:
Dann speichert man den Zentrum ab mit einem "leeren Weg". Das heisst, man startet die Wegaufzeichnung
und speichert dann sofort ohne sich zu bewegen.

Trick 2:
Ist man in einem groesseren Gebiet, von wo man nicht zum ausgewaehlten Zentrum hinlaufen kann, zum Beispiel auf einer Insel,
dann kann man dort ein "neue Zentrum" auswaehlen und dann dort den Wegeskript auch nutzen!

Trick 3:
Wenn man einen neuen Punkt speichern will, welches in der Naehe eines anderen Punkten sich befindet,
so muss man nicht den gesamten Weg neu ablaufen! Man kann beim Speichern den anderen Punkt als Startpunkt
angeben, so dass der neue Punkt nur den Hin- und Rueckweg zum alten Punkt benoetigt.
Allerdings wird das Skript trotzdem den Weg bis zum Zentrum zuruecklaufen. Dies ist jedoch so schnell, dass man es nicht merkt.

Trick 4:
Als Seher gibt es Portale und diese erlauben einfachere und kuerzere Wege. Man kann naemlich die "Portale" als Zentrum waehlen.
Jeder Wege sollte also von naechsten Portel hin und zurueck fuehren. Allerdings muss man dann beachten,
dass jeder Weg mit einem Teleport-Befehle zum entsprechenden Portal beginnen muss! Lies dazu noch 8.2., da bei dieser
speziellen Form Raum-IDs nachgetragen werden muessen.

## 6. Welcher Char nutzt welche Wege? Gemeinsame und unterschiedliche Wege.

Im Skript-Element Core ist mit dem Dateinamen festgehalten aus welcher Datei die Wege bezogen werden. Wenn ihr also mehrere Profile anlegt und bei allem das Skript installiert, dann wird natuerlich bei allen Profilen der selbe Dateiname stehen und damit greifen alle Profile auf die selben Wege zurueck. Ich empfehle aber Wege fuer Seher und Nichtseher-Profile zu unterscheiden. Legt fuer Nichtseher-Profile eine eigene Datei an indem ihr dies im Code aendert. Damit muesst ihr im Skript-Element Core den Namen bei filename aendern. Fuer die Zukunft plane ich dies mit ein Verwaltungssystem, welches im Spiel steuerbar ist, zu vereinfachen.

## 7. Reisen mit dem Wegeskript

### 7.1. Wie kann ich nun von Punkt A nach B gelangen?

Es gibt zwei Moeglichkeiten das schnelle Reisen mit dem Wegeskript zu bedienen:

1. Moeglichkeit:

           #go <start> <ziel>
  Dies ist ein *blindes Laufen* vom Punkt \<start> nach Punkt \<ziel>.
  Dabei arbeitet das Skript stur den Weg von \<start> zum Basispunkt und dann vom Basispunkt nach \<ziel> ab.


2. Moeglichkeit:

           #go <ziel>

  Dies ist ein automatisches Laufen. Dabei ermittelt der Wegeskript aus der Raum-ID, ob an dem Standort sich ein gespeicherter Punkt befindet. Falls dem so ist, dann laeuft man zum Punkt \<ziel>. Befindet man sich aber in keinem gespeicherten Punkt, dann kommt nur eine Fehlermeldung.


  Beide Moeglichkeiten haben ihre Vor- und Nachteile. Im Allgemeinen ist es schneller und einfacher die 2. Moeglichkeit
  zu benutzen, aber dieser kann auch in gewissen Situationen Probleme machen.

  Die 2. Moeglichkeit ist automatisiert. Wenn ein Weg richtig gespeichert ist, dann kann es nicht passieren, dass man den
  Wegeskript in einem benachbarten Raum ausloest und man durch das sture Abarbeiten moeglicherweise in gefaehrliche Raeume
  rein laeuft.

  Anderer setzt es voraus, dass das gmcp die Raum-ID richtig ausgibt. Dies ist meistens der Fall, aber nicht, wenn der
  Spielercharakter erblindet ist. In dem Fall werden die Raum-Informationen ab der Erblindung nicht mehr aktualisiert,
  selbst wenn man einen anderen Raum betritt. Erblindet man somit in einem nicht gespeichtern Punkt, dann wird das
  automatisierte Laufen nicht funktionieren, weil es den richtigen Raum nicht erkennen kann. Daher muss man altbewaehrt
  sich zu einem gespeichtern Punkt orientieren und dann die 1. Moeglichkeit nutzen. Die Gefahr des Irrlaufens besteht
  natuerlich trotzdem, aber der Befehl wird dennoch unter diesen Umstaenden ausgefuehrt.

### 7.2. Wie kann ich nachschauen welchen Weg ich eben gelaufen bin?

Du bist vielleicht nicht dort gelandet, wo du eigentlich hin wolltest?
Das kann zwei Ursachen haben. Entweder hat sich ein Fehler im einem Weg
eingeschlichen oder auf dem Weg ist etwas Unerwartes passiert, wodurch
der Char nicht ans richtige Ziel ankommen konnte. Dazu gibt es den Befehl

           #runned

Dieser gibt einen den vollstaendigen Weg an, den das Skript bei der letzten
Reise abgearbeitet hat. Allerdings kann es natuerlich nicht zeigen an welcher
Stelle zum Problem kam. Dazu muss man den Weg per Hand nachlaufen.

## 8. Bearbeitung von gespeicherten Punkten

Natuerlich passiert es, dass man sich vertippt oder etwas an den Informationen, wie dem Namen, den IDs oder dem Titel was nachtraeglich aendern will. Dies ist auch moeglich.

### 8.1. Namen aendern

Der Befehl

           #rename <old_name> <new_name>

 benennt den Punkt mit dem Namen \<old_name> in \<new_name> um.

 Beispiel:

           #rename sandtiger st

 Benennt den gespeicherten Punkt "sandtiger" in den kuerzen Namen "st" um.

###  8.2. ID auslesen, hinzufuegen oder loeschen

Die Raum-ID wird normalerweise bei der Wegaufzeichnung mitgefuehrt und mitgespeichert. Dennoch kann es Vorteile haben mehr
als eine Raum-ID fuer einen gespeicherten Punkt zu hinterlegen. Zum Beispiel in der Situation von Trick 4 im Abschnitt 5.8..
Denn die Portale als Basispunkt zu nehmen ist sehr praktisch, da man oft mit sehr kurzen Wegen arbeiten muss.
In Morgengrauen muss man dann nur aufpassen, dass in den Para-Welten manche Portale auch nicht ungefaehrlich sind.
Nun ist die Sache, dass man im Allgemeinen zwar den Basispunkt nicht irgendwie zu beachten braucht. Es muessen nur die Wege
stets darueber fuehren. Als Seher kann es passieren, dass man an einem Portal steht und dann irgendwo hinreisen will.
Da gibt es zwei Moeglichkeiten. Entweder man markiert jedes Portal als ein Punkt mit einem *leeren* Weg. Man startet also die
Wegaufzeichnung am Portal und beendet diesen und speichert dannn den Weg. Das ist moeglich.

Ich persoenlich habe aber nur den Sandtiger als Punkt gespeichert, da man sich doch oft dort trifft, und dann die IDs von
allen anderen Portalen zum Punkt Sandtiger hinzugefuegt. Wenn ich also an einem Portal stehe und in mein Haus laufen will,
dann wird das Portal als Punkt Sandtiger erkannt. Da jedes Weg mit einem Teleport-Befehl beginnt, ist das aber egal, dass
ich dann vielleicht nicht wirklich am Sandtiger stehe, da der Weg funktioniert!

Natuerlich gibt es auch noch andere Moeglichkeiten mit mehr als einer ID zu einem Punkt zu arbeiten, wenn der Weg auch
von anderen Raeumen aus funktioniert. Daher kann man

           #zeigeids <namen>

sich anzeigen lassen, welche Raum-IDs an dem Punkt mit den Namen \<name> gespeichert wurden.

Beispiel:

           #zeigeids sandtiger

Zeigt alle gespeicherten IDs, die dem Punkt "sandtiger" zugeordnet wurden. Natuerlich muss man auch abgleichen koennen,
wie die Raum-ID im dem Raum ist, in dem man sich befindet. Dazu kann man

           #raumid

so ohne Argumente eingeben. Die Raum-ID wird im Spiel als Info angezeigt. Will man nun die ID des Raumes hinzufuegen in der
man sich gerade befindet, dann gibt man

           #aid <name>

ein um die ID dem Punkt mit den Namen \<name> hinzuzufuegen.

Beispiel:

           #aid sandtiger

Fuegt die aktuelle Raum-ID dem Punkt "sandtiger" hinzu.

Natuerlich kann es passieren, dass man sich dabei vertan hat und eine Raum-ID wieder loeschen will. Dazu laesst man
sich zuerst die IDs zum Punkt anzeigen. Die werden aufgelistet mit einer Nummer. Anschliessen kann man eine ID mit

           #lid <name> <nummer>

loeschen.

Beispiel:

           #lid sandtiger 3

Loescht die 3. ID des Punktes namens "sandtiger".

###  8.3. Titel aendern

Vielleicht hat man einen doofen Titel ausgewaehlt beim Speichern. Oder der Titel ist zu ungenau und man moechte zusaetzliche
Informationen hinzufuegen? Dies ist mit dem Befehl

           #retitel <name> <titel>

 erreichen. Dann wird dem Punkt \<name> der alte Titel durch \<titel> ersetzt.

 Beispiel:

           #retitel st Am Sandtiger von Port Vain

 Ersetzt den alten Titel von "st" durch "Am Sandtiger von Port Vain"

## 9. Gespeichtern Punkt loeschen

Vielleicht hat man sich bei einem Weg vertan oder etwas wurde was falsch gespeichert oder man hat andere Gruende einen
gespeicherten Punkt wieder loeschen zu wollen. Um sicher zu gehen, dass man nicht verstehentlich einen falschen Punkt loescht,
wird das Loeschen in zwei Stufen ausgefuehrt. Dazu verwendet man den Befehl

           #loesche <name>

benutzen um den Punkt \<name> zu loeschen. Wenn man den Befehl einmal eingibt, dann wird erstmal nur der Titel geloescht.
Damit zaehlt der Punkt als *temporaerer Punkt* (vergleiche 5.7.). Solange das Profil des Clients noch nicht geschlossen wird,
kann man die Loeschung jederzeit rueckgaengig machen, indem man mit einen Titel wieder hinzufuegt. Das Hinzufuegen des Titels
ist aber hier gleichbedeutend mit aendern des Titel. Das heisst, dass man mit \retitle \<name> \<titel> dem Punkt wieder einen
Titel hinzufuegt. Tut man dies nicht, dann ist der Punkt mit dem Beenden des Profils endgueltig geloescht.

Man kann aber jedoch auch darauf bestehen einen Punkt sofort entgueltig zu loeschen. Dazu gibt man den Loeschbefehl genauso
ein zweites Mal ein und fertig.

Beispiel 1:

           #loesche st
           -- Löscht den Punkt st, zunaechst temporaer
           #retitel st Am Sandtiger von Port Vain
           -- Fuegt dem Punkt st wieder einen Titel hinzu, womit die Loeschung rueckgaengig gemacht wurde.

Beispiel 2:

           #loesche st
           #loesche st

-- Löscht den Punkt st dauerhaft

## 10. Suchfunktion fuer die gespeichten Punkte

Vielleicht hat man vergessen, welche Namen man fuer die Punkte bereits vergeben wurden oder man moechte den Namen von einem
Punkt raussuchen, erinnert sich aber nur an den Titel oder einen Teil des Titels? Dann kann man folgenden Befehl benutzen:

           #finde <Buchstabe oder Text>

Uebergibt man der Funktion den Parameter nur einen Buchstaben, dann erhaelt man eine Liste aller vergebenen Namen,
die mit diesem Buchstaben anfangen. Gibt man mehr als einen Buchstaben ein, dann werden alle Titel darauf geprueft, welcher
den Parameter als Teil enthaelt.

Beispiel 1:

           #finde a

Listet alle Namen auf, die mit dem Buchstaben 'a' anfangen.

Beispiel 2:

           #finde haus

Listet alle Namen mit Titel auf, wo der Titel d 'haus' beeinhaltet.

## 11. Externe Speicherung der Wege mit automatischem monatlichen Backup

Fuer alle Faelle wird automatisch vom Wegeskript monatlich ein Backup der gespeicherten Wege erstellt. Dazu wird im
Arbeitsordnet erstellt. Der Name endet mit dem Jahr und dem Monat vom Backup. Ausserdem ist eine Datei dort erstellt,
welches festhaelt in welchem Monat zuletzt ein Backup erstellt wurde. Jedes Mal beim Starten des Profils wird geprueft ob
in diesem Monat ein Backup besteht und falls nicht, wird es erstellt.

Moechte man einen Backup benutzen statt der aktuellen Datei, dann muss man dies manuell tun. Dazu loescht man im
Arbeitsordner die Datei *Wege.txt* und sucht sich das Backup aus, welches man benutzen wird. Diese benennt man dann
in *Wege.txt* um.

Im Normalfall wird es wahrscheinlich nicht notwendig sein ein Backup zu benutzen. Moechte man dies nicht haben,
dann schaut man nach der Installation bei den Skripten im Ordner "waiting for events" im Element "load_pathes_at_beginn".
Die Zeile

           PF:test_backup()

muss dann einfach nur geloescht werden (dies sollte Zeile 10 sein).

## 12. Super-Safe-Modus

Normalerweise werden beim Start des Profils die ganzen Wege geladen und beim Beenden werden die ganzen Wege gespeichert.
Aber falls der Client abstuerzen sollte, dann gehen die Veraenderungen seit dem Start verloren.

Und dafuer gibt es den "Super-Safe-Modus", der lediglich besagt, dass bei jeder Veraenderung auch automatisch alles in
der externen Textdatei gespeichert wird. Also beim Erstellen eines neuen Punktes, beim Aendern der Informationen eines
Punktes, sei es Name, Titel oder ID.

Standardmaessig ist der Modus eingeschaltet. Man kann dies bei Skripte im Element "Core" in der Zeile

           super_safe=true}

(Zeile 25) aendern, indem man *true* durch *false* ersetzt.


## 13. Raummeldungen entlang des Weges weggaggen (ab v1.1)

  Reist man mit dem Wegeskript, so geschieht dies im ultakurz-Modus, damit nicht die ganzen Raumbeschreibungen das Spiel und somit auch den Log vollscrollen. Jedoch wurden weiterhin Leerzeilen fuer jeden Raum erzeugt. Des Weiteren wurden Raummeldungen trotzdem angezeigt. Dies ist unschoen und kann ab Version v1.1 nun entfernt werden! Ich habe schonmal ein Paar Meldungen eingestellt, die beim Reisen unterbunden werden sollen, aber ab v1.2 koennt ihr diese Liste nach eigenem Ermessen modizifieren! Dazu die folgenden Unterpunkte:

### 13.1. Anzeigen der Gags (v1.2)

  Mit dem Befehl

           #zeigegags

 koennt ihr euch anzeigen lasse welche Texte erkannt und dann die ganze Zeilen beim Laufen geloescht wird.

### 13.2. Hinzufuegen von Gags (v1.2)

 Mit dem Befehl

           #addgag <text>

koennt ihr die Liste aus 13. erweitern. Beachtet, dass eine ganze Zeile geloescht wird, wenn der Text in dieser _enthalten_ ist.

Beispiel:

           #addgag Einhorn

Damit wird der Text _Einhorn_ hinzugefuegt. Wenn also beim Laufen eine Raummeldung das Wort Einhorn enthaelt, wird diese Zeile geloescht.

### 13.3. Loeschen von Gags (v1.2)

Mit dem Befehle

           #delgag <nummer>

koennt ihr wieder einen Text aus der Liste loeschen. Dazu muss man die Nummer angeben, die der Anzeige, siehe 13.1., angegeben wird.

## 14. Hilfefunktion im Spiel (ab v1.1)

  Wer kann sich schon alle Befehle merken? Und wer will mitten im Spiel die
  README.txt raussuchen? Und den passenden Alias rauszusuchen ist auch nicht
  einfacher. Aus diesem Grund habe ich eine Hilfefunktion eingebaut, die auf
  zwei Ebenen funktionert. Mit

           hilfe WS

  wird die Liste der im Spiel zur Verfuegung stehenden Befehle mit ihrere
  Syntax angezeigt. Benoetigt man detailiertere Hilfe zu einem Befehl,
  so ist dies nun auch im Spiel moeglich. So wird zum Beispiel mit

           hilfe WS #go

  Die detailierte Information zum Befehl \#go angezeigt.

