# Wegeskript (v2.0)

Dieses Skript ist in Lua fürs [Mudlet](https://www.mudlet.org/) geschrieben.
Das Skript habe ich fuer mich selbst zur Nutzung in
[Morgengrauen](http://mg.mud.de) erstellt, so dass gewisse Rahmenbedingungen
erfuellt sein muessen, siehe Installation. Generell ist es aber auch auf
andere Spiele uebertragbar. Allerdings ist dazu zu erwaehnen, dass dieses
Skript Daten aus gmcp.MG.char benutzt. In anderen Spielen wird die
Datenstruktur von gmcp moeglicherweise anders sein, so dass diese Stellen
angepasst werden muessten.

# Inhaltsverzeichnis

1. Was ist das Wegeskript

2. Installation

3. Wie kann man ws Wegeskript nutzen?

4. Wie erstelle ich Knoten und Wege?

    4.1 Knoten erstellen

    4.2. Wegaufzeichnung, Basic

    4.3. Wegaufzeichnung, Features

    4.4. Aufgezeichneten Weg speichern

    4.5. Alias fuer Richtungen erweitern

    4.6. Anzeige des bisher aufgezeichneten Weges

    4.7. Loeschen der letzten Eingaben der Aufzeichnung

5. Reisen mit dem Wegeskript

    5.1. Reise von A nach B

    5.2. Die zuletzt gelaufene Strecke

    5.3. Weg berechnen und anzeigen lassen

    5.4. Wege vorbereiten

6. Anzeige und Bearbeitung gespeicherter Knoten

    6.1. Knoten anzeigen oder nach Knoten suchen

    6.2. Raum-ID loeschen oder hinzufuegen

    6.3. Titel

7. Anzeige und Bearbeitung gespeicherter Wege

8. Seherportale

9. Hilfefunktion / Syntaxhilfe

10. Spezielle Wege

  10.1. Wechsel zwischen den Welten

  10.2. Bonbons von der Rieseninsel

  10.3. Kram in verschiedenen Laeden verkaufen


# 1. Was ist das Wegeskript

  Das Wegeskript ermoeglicht schnelles Reise zwischen beliebigen gespeichtern
  Punkten im Spiel. Es gibt sogar eine Syntax, bei der man nur das Ziel
  eingeben muss und das Skript automatisch erkennt, wenn man sich an einem
  gespeicherten Ort befindet um dann den Weg zum Ziel zu finden.

# 2. Installation

  Das Wegeskript ist ein Teil der Skript-Sammlung. Daher muss zur Nutzung
  das Modul Mundron\_Core.xml bereits installiert sein und dann nur noch
  zusätzlich Wegeskript\_v2.xml als Modul installieren und fertig. Die Module
  könnt ihr im Mudlet installieren indem ihr Alt+I drückt oder im Menü auf
  "Werkzeuge" geht und dort "Module" auswählt. Da klickt ihr auf
  "Installieren", wählt die Datei aus und fertig! Möglicherweise muesst
  ihr Mudlet einmal neustarten.

# 3. Wie kann man das Wegeskript nutzen?

  Es gibt schon einige vorgefertigte Aliase im Skript, die ihr benutzen
  koennt. Wenn ihr im Spielt \#WS eingebt, erscheint eine Liste der
  moeglichen Befehle.

  Im Wesentlichen werden Raeume als Knoten definiert, die mit einem Titel
  versehen werden koennen um nach ihnen zu suchen. Ausserdem werden wischen
  den Knoten Wege definiert um von einem Knoten zum naechsten Reisen
  zu koennen. Das bildet die Basis und kann bereits fuer die meisten Faelle
  genutzt werden.

  Dennoch gibt es weitere Features, die moeglich sind, worauf spaeter noch
  eingegangen wird, wie zum Beispiel Wartebefehle oder Trigger entlang
  von Wegen oder auch spielerabhaengige Nutzbarkeit von Seherportalen.

# 4. Wegaufzeichnung / Wie erstelle ich Knoten und Wege?

## 4.1 Knoten erstellen

  Wenn der aktuelle Raum als Knoten gespeichert werden soll, so ist dazu

    \#addnode <Knotenname>:<Titel fuer den Knoten>

  gedacht. Der Titel kann optional auch weggelassen werden, ist aber hilfreich
  um spaeter Knoten anhand des Titels wieder zu finden.

  Beispiele:
    \#addnode sandtiger
    \#addnode pv:Am Hafen von Port Vain

  Es ist aber auch moeglich einen Weg aufzuzeichnen und dabei mit einem
  Befehl den Start- und Zielknoten direkt (ohne Titel) erstellen zu lassen.
  Der Titel kann jederzeit und ueberall auch nachgetragen werden, siehe XX.

## 4.2. Wegaufzeichnung, Basic

  Fuer die Wegaufzeichnung sind folgende Befehle direkt im Spiel nutzbar:

             \#wa start
             \#wa stop
             \#wa weiter
             \#wa ziel

  Mit

             \#wa start

  wird die Aufzeichnung gestartet. Dies kann an einem bereits definierten
  Knoten stattfinden, muss aber nicht, da nachtraeglich das noch als
  Knoten definiert werden kann.

  Nun geht man zum Zielpunkt. Dabei werden fuer folgende Richtungen
  automatisch ein Alias erzeugt, so dass man bei Nutzung dieser Befehle
  in der Konsole die Wegaufzeichnung direkt die Eingabe speichert:

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

  Bei Bedarf kann dies auch erweitert werden, wie im Abscnitt XX
  beschrieben wird.

  **ACHTUNG**
  Wenn es gewuenscht ist, dass das NumPad auch bei der Wegaufzeichnung
  genutzt wird, muessen die Tastenbelegungen entsprechend angepasst werden
  indem statt send("n") dann expandAlias("n") benutzt wird.
  Eine entsprechende Tastenbelegung liegt als **zusaetzliches** Packet
  "expandAlias\_NumPad\_Belegung.xml" bei und kann geladen und genutzt werden.
  Diese Belegung funktioniert unabhaengig davon, ob die Wegaufzeichnung
  eingeschaltet ist oder nicht.

  Ist man im Zielraum angekommen, so wird dies mit

             #wa ziel

  markiert. Nun kann man entweder die Aufzeichnung mit

             #wa stop

  beenden und den Weg speichern nur vom Start- zum Endknoten zu speichern,
  siehe XX.
  In der Regel will man aber auch den Rueckweg speichern. Dies ist bequem
  moeglich indem man statt dem Beenden der Aufzeichnung diese nun vom
  End- zum Startknoten fortsetzt. Nachdem das Ziel markiert ist, erkennt
  die Wegaufzeichnung, dass man sich nun auf dem Rueckweg finden. Am
  Startknoten wieder angekommen beendet man die Aufzeichnung und speichert
  automatisch den Hin- und Rueckweg zwischen Start- und Zielknoten.

  Nun kann es passieren, dass der Start- und Zielraum noch keine definierten
  Knoten sind. Sollte dies der Fall sein, gibt es eine Meldung und man kann
  nun nachtraeglich die Knoten mit

    \#addboundaries <Startknoten-Name> <Zielknoten-Name>

  speichern und den Speicherbefehl wiederholen.

## 4.3. Wegaufzeichnung, Features

  Im vorigen Abschnitt wurde erklaert, wie man einen Weg aufzeichnet, bei
  der die herkoemmlichen Himmelsrichtungen gebraucht werden. Nun ist es
  so, dass manche Wege auch speziellere Eingaben brauchen, wie das
  oeffnen eines Seherhauses oder das Zwaengen durch ein Gebuesch.
  Dies kann man mit

    \#vor <Befehl>

  eingeben und gleichzeitig speichern und ausfuehren, zum Beispiel

    \#vor oeffne tuer


  Ausserdem gibt es auch Orte, bei denen man eine Zeit warten muss,
  auf eine bestimmte Meldung wartet oder ein blockender NPC im Weg steht.
  Auch dafuer gibt es Funktionen bei der Aufzeichnung:


    \#wait <Anzahl an Sekunden, die man wartet>

  Dabei wird nach der gegebenen Anzahl an Sekunden die Bewegung fortgesetzt.


    \#trigger <Name des Triggers>:<Ausloeser>?

  Der Trigger-Name bezieht sich auf den Trigger, der man selbst unter
  "Trigger" in der Mudlet-GUI hinterlegt. Es ist empfehlenswert bei der
  Namensweg den Start- und Endknoten zu integrieren um spaeter zu wissen,
  zu welchem Weg der entsprechende Trigger zaehlt. Notwendig ist dies jedoch
  nicht. Der Trigger sollte deaktiviert sein. Beim Laufen des Weges wird der
  Trigger aktiviert und am Ende wieder deaktiviert. Der optionale Ausloeser
  ist ein Befehl oder eine Liste von Befehlen durch ein Komma getrennt,
  der oder die nach dem Aktivieren des Triggers ausgefuehrt wird bzw werden
  um den Trigger zu befeuern. Der "schau" Befehl ist dabei nicht notwendig bzw
  besser wegzulassen, da am Ende des Weges dieser automatisch ausgefuehrt wird
  um die Raumbeschreibung am Ziel anzuzeigen.

  Beispiele:

    \#trigger drachenhort_schlange:stelle an schlange an
    \#trigger katzensprung
    \#trigger mundron_furz:trete mundron,sag Was faellt Dir ein?

  Sollen mehrere Trigger gleichzeitig aktiviert werden, so ist dies mit
  der Triggergruppe analog moeglich:

    \#triggergroup <Liste von Triggernamen>:<Ausloeser>?

  Analog sind die Ausloeser optional und durch Komma getrennt auch als
  Liste angebbar. Bei den Triggernamen muessen diese auch durch ein
  Komma getrennt aufgelistet werden, wie zum Beispiel

    \#triggergroup flack_portal,offenes_portal


  Eine spezielle Art von Trigger bilden ist bei Blocker noetig.

    \#blocker <NPC Name>:<1. Zeile beim Knuddeln>:<1. Zeile beim Tod>

  Hier sollte der Name des NPCs idealerweise eindeutig sein. Mit
  einem Knuddel-Befehl wird geprueft ob der Blockende NPC anwesend ist.
  Falls nicht, wir der Weg fortgesetzt, anderfalls der NPC angegriffen
  und nach dem Tod wird der Weg fortgesetzt.


  **Empfehlung:** Sowohl beim Trigger, als auch beim Blocker ist es sinnvoll
  den Weg dort enden zu lassen, damit man bei Bedarf sich umentscheiden und
  woandershin laufen kann. Gerade bei Blockern, die nicht trivial sind oder
  der Spieler noch klein ist, wird dies wichtig sein.


## 4.4 Aufgezeichneten Weg speichern

  Sobald die Wegaufzeichnung beendet wurde gibt es die Moeglichkeit entweder
  mit

    \#seinbahn <Startknoten> <Zielknoten>

  nur den Weg vom Startknoten zum Endknoten hin zu speichern oder falls
  der Hin- und Rueckweg aufgezeichnet wurde mit

    \#sweg <Startknoten> <Zielknoten>

  diese zu speichern. Wie oben erwaehnt, kann es zu einer Meldung kommen,
  wenn entweder der Start- oder Zielknoten nicht definiert wurden. Die
  Aufzeichnung wird aber solange gespeichert bis das Profil beendet wird
  oder eine neue Aufzeichnung mit \#wa start initiiert wurde.


## 4.5 Alias fuer Richtungen erweitern

  Fuer die Anzeige welche Aliase fuer die Wegaufzeichnung definiert sind:

    \#showaliases

  Um weitere Aliase hinzuzufuegen, die **nur** bei der Wegaufzeichnung
  definiert werden:

    \#addalias <Neuer Alias>

  Um einen selbst hinzugefuegten Alias wieder zu entfernen schaue man sich
  zuerst in der Uebersicht an, welche ID es erhalten at um es anschliessend
  ueber die ID zu loeschen:

    \#deletealias <Alias-ID>


### 4.6 Anzeige des bisher aufgezeichneten Weges

  Um die bisher aufgezeichnete Strecke anzuzeigen kann

    \#showrecord <Anzahl der Schritte>?

  genutzt werden. Die Anzahl der Schritte kann weggelassen werden um
  die ganze Aufzeichnung anzeigen zu lassen.


### 4.7 Loeschen der letzten Eingaben der Aufzeichnung

  Es kann passieren, dass man sich vertippt und man den letzten Eintrag
  oder auch die letzten X Eintraege in der Aufzeichnung loeschen will.
  Dabei ist

    \#deleterecord <Anzahl der Eintraege>?

  hilfreich. Ohne ein Argument wird die gesamte Aufzeichnung gespeichert.
  Dies wuerde ebenfalls passieren, wenn die Aufzeichnung mit \#wa start
  neu initiiert wird.


# 5. Reisen mit dem Wegeskript

Das Skript benutzt den Algorithmus von Dijkstra um den kuerzesten Weg
von einem Startknoten zu einem Zielknoten zu finden. Bei der ersten Nutzung
wird der kuerzeste Weg berechnet, doch auch auch gespeichert um die Rechnung
zu sparen. Es ist auch moeglich im Vorfeld einen Weg zwischen zwei Knoten
vorbereiten zu lassen. Dazu spaeter mehr.

## 5.1 Reise von A nach B

  Befindet man sich an einem Startknoten und will zu einem Zielknoten reisen,
  so waere der Befehl dazu

    \#go <Zielknoten>

  denn das Wegeskript wird in der Regel automatisch erkennen, wenn du bereits
  an einem Knoten stehst und brauchst dies nicht explizit einzugeben.


  Jedoch gibt es Situationen in denen man erblindet oder der Raum zu dunkel
  ist um etwas zu erkennen. In diesen Faellen werden die Raum-IDs ueber
  gmcp nicht aktualisiert, so dass man "blind" laufen muss. Dies ist moeglich
  indem man an den letzt besuchten Zielknoten geht und dort

    \#run <Zielknoten>

  Moechtest du jedoch an einem anderen Knoten starten, dann benutze

    \#run <Startknoten> <Zielknoten>


## 5.2 Die zuletzt gelaufene Strecke

  Man kann sich mit

    \#runned

  anzeigen lassen, welchen Weg man zuletzt gelaufen ist.

## 5.3 Weg berechnen und anzeigen lassen

  Moechte man wissen, ueber welche Knoten und mit welchen Befehlen
  das Skript zwischen zwei Knoten gehen wuerde, kann man sich das berechnen
  und anzeigen lassen mit

    \#computepath <Startknoten> <Zielknoten>


## 5.4 Wege vorbereiten

  In der Regel ist es nicht notwendig Wege explizit vorzubereiten, da nach
  der ersten Nutzung eines Weges zwischen zwei Knoten, dieser einmal
  berechnet wird und bis zum Schliessen des Profils gespeichert bleibt.
  Jedoch will man einen bestimmten Weg aus irgendwelchen Gruenden doch
  vorbereiten ohne es einmal abzulaufen. In diesem Fall ist dies mit

    \#prepare <Startknoten> <Zielknoten>

  moeglich. Wird ein neuer Weg angelegt, der einem kuerzere Verbindungen
  erlaubt, so kann man die erneute Berechnung des Weges mit

    \#reprepare <Startknoten> <Zielknoten>

  erzwingen. Gibt man es ohne Argument an, also nur

    \#reprepare

  so werden **alle** bisher berechneten Wege neu berechnet.

# 6. Anzeige und Bearbeitung von gespeicherten Knoten

## 6.1 Knoten anzeigen oder nach Knoten suchen

  Wenn der Name eines Knotens bekannt ist, koennen alle Informationen zu
  diesem Knoten mit

    \#shownode <Knotenname>

  angezeigt werden. Jedoch vergisst man vielleicht Knoten, die man selten
  besucht, so dass hier eine gute Wahl fuer einen Titel hilfreich sein kann,
  denn mit

    \#searchnode <Suchtext>

  wird case-insensitive geschaut, welche Knoten im Titel den Suchtext
  beinhalten und gibt bei einem Treffer die volle Information des Knotens
  wieder und bei mehreren Treffern eine kurze Liste der Treffer.

## 6.2 Raum-ID loeschen oder hinzufuegen

  Um eine Raum-ID zu einem Knoten hinzuzufuegen, stelle man sich in den
  entsprechenden Raum und nutze

    \#addid <Knotenname>

  Dies wird zum Beispiel gebraucht, da in Parallelwelten die Raume andere
  IDs haben. Jedoch nur, wenn sich die Parallelwelt in dem Raum von der
  Normalwelt unterscheidet.


  Falsch zugewiesene IDs lassen sich auf zwei Arten loeschen. Entweder steht
  man in dem Raum, dessen ID entfernt werden soll und nutzt

    \#deleteid <Knotenname>

  oder man merkt sich die Nummer vor der ID, die bei \#shownode angezeigt wird
  und loescht genau diese ID mit

    \#deleteid <Knotenname> <ID-Nummer>

## 6.3 Titel

  Empfehlenswert ist es bei der Knotenerstellung direkt den Titel mit
  anzugeben. Jedoch kann man sich auch nachtraeglich mit

    \#addtitle <Knotenname>:<Titel>

  nachholen. Der selbe Befehl wird auch genutzt um den Titel mit einem
  neuen Titel zu ueberschreiben. Das Loeschen eines Titels ist mit

    \#deletetitle <Knotenname>

  moeglich.

# 7. Anzeigen und Bearbeitung gespeicherter Wege

  Um einen Weg sich anzuschauen muss man beachten, dass du wir hier nur
  Wege betrachten, die explizit angelegt wurden und keine kombinierten Wege
  die nutzbar sind.
  Um sich diese Wege anzuschauen benoetigt man die Pfad-ID. Um diesen zu
  erhalten schaut man sich den Startknoten mit \#shownode an um dann
  die Nachbarknoten und die Pfad-ID mit dem Weg zu diesem Nachbarknoten
  zu erhalten. Mit dieser Pfad-ID wird einem der Weg dann ueber

    \#showpath <Pfad-ID>

  angezeigt. Aktuell ist eine besondere Bearbeitung des Weges umgesetzt,
  jedoch laesst sich dieser Weg mit

    \#deletepath <Pfad-ID>

  loeschen um es neu anzulegen.

# 8. Seherportale

  MorgenGrauen besticht vor allem mit besonders bequemen Reisen mit Hilfe
  der Seherportale. Per Standard ist zunaechst KEIN Seherportal nutzbar.
  Um eine Uebersicht zu haben, welche Portale nutzbar sind, gibt es

    \#showportals

  Nun wird man vielleicht bereits einen Seher haben mit einer bestimmten
  Menge an Seherportalen, die man automatisch erfassen lassen kann indem man
  sich an ein Portal stellt und den Befehl

    \#catchportals

  eingibt. Dabei werden alle Portale mit p0 bis p40 angelegt, sowie alle
  Wege zwischen den Portalen, die Titel werden, sofern sie nicht vorhanden
  sind mit der Beschreibung gesetzt und am Ende wird der Charakter durch alle
  Portale geschickt um die Raum-ID zu speichern und sich zu merken, welche
  der Portale nutzbar sind. Ausserdem werden alle potentielle Wege zwischen
  allen Portalen auch bereits angelegt. Dies kann einige Sekunden dauern.
  Werden spaeter weitere Portale gefunden, muessen unter Umstaenden die
  IDs nachgetragen werden und mit

    \#flipportal <Portalnummer>

  dann die Nutzung eines Portals an oder auch ausgeschaltet werden.

  **WICHTIG** Die Nutzbarkeit der Portale ist __profilabhaengig__, so dass
  das ein Seherprofil die Portale nutzen kann, waehrend ein Profil fuer einen
  Nichtseher die Profile nicht nutzen wird. Aber die Knoten und Wege sind
  aber global, so dass wenn sie alle einmal angelegt wurden, nicht
  mehr neu angelegt werden muss. Es reicht dann mit \#flipportal sie
  nur noch "freizuschalten".

# 9. Hilfefunktion / Syntaxhilfe

  Um im Spiel direkt eine Liste der moeglichen Befehle einzusehen ohne
  immer die Hilfe nach der Syntax aufschlagen zu muessen erhaelt man eine
  Anzeige mit

    \#WS

  was kurz fuer "WegeSkript" steht.

# 10. Spezielle Wege

  Natuerlich gibt es Situationen in denen man spezielle Wege anlegen will,
  die weitere Besonderheiten erfordern. Fuers erste ermutige ich hierzu
  dies selbst zu versuchen, da der Aufwand das in einzelne Funktionen
  zu kapseln und Befehle dafuer anzulegen und die Hilfe zu erweitern fuer
  Einzelfaelle unverhaeltnismaessig ist. Dennoch habe ich drei Beispiele
  im Skript hinterlegt mit dem Versuch im Kommentar anzuleiten, wieso
  entsprechende Befehle genutzt wurden. So gibt es zum Beispiel auch die
  Moeglichkeit beim Laufen weggegaggte Zeilen auszuwerten und nach dem Lauf
  am Ende eine Funktion aufzurufen, welche die Auswertung anzeigt.
  Dazu folgende Beispiele:

## 10.1. Wechsel zwischen den Welten

  Der entsprechende Alias im Skript wird mit

    \#para <Nummer der Welt>

  aktiviert. Im Wesentlichen ist es ein go-Befehl zu p32, dort zum
  Weltenportal im nordwesten, das Portal betreten, warten, zurueck zu
  p32 und dann an den urspruenglichen Ort zuruecklaufen. Zu beachten ist,
  wie auch in den anderen beiden Beispielen, dass wir hierzu drei
  Besonderheiten haben:

  1. Der Ursprungsknoten muss gespeichert werden.
  2. Das Ausfuehren des Weges ist so schnell, dass wir beim Zwischenschritt
  **nicht** die Raum-ID automatisch erfassen lassen koennen, also muessen
  bei allen go-Befehlen der Start- und Zielknoten explizit angegeben werden.
  3. Um die Schau-Meldung bei Zwischen-Knoten zu unterdruecken muss bei
  jedem go-Befehl, welcher am Ende nicht die Raumbeschreibung ausgeben soll,
  zusaetzlich false, falsch, true also weitere Parameter uebergeben werden.

  Wichtig ist bei diesem Befehl zusaetzlich, dass beim Wechsel der Welten
  eine Zeitverzoegerung noetig ist, ansonsten wird man unter Umstaenden an
  unliebsame Orte teleportiert. Daher muss das zuruecklaufen nach der Wahl
  in welche Welt man reisen will, verzoegert mit einem Timer ausgefuehrt
  werden.

## 10.2. Bonbons von der Rieseninsel

  Die Nutzung, sofern man in der Normalwelt ist, wird mit

    \#sdrops

  ausgeloest.
  Im Gegensatz zum vorigen Beispiel ist es hier nicht noetig eine
  Zeitverzoegerung einzubauen, jedoch ist man unter Umstaenden daran
  interessiert, wie viele Drops man gesammelt hat ohne vorher und nachher
  dies im Inventar pruefen zu muessen. Zu diesem Zweck gibt es
  die Moeglichkeit Auswertungsfunktionen zu speichern, welche die
  beim Weg gegaggten Zeilen auswertet und eine Funktion am Ende, welche
  nach dem Weg ausgefuehrt wird. Details dazu im Alias.


## 10.3. Kram in verschiedenen Laeden verkaufen

  Hat man das Inventar voll mit Sachen, die man alle verkaufen will, also
  in einem Laden mit "verkaufe alles" alles verkaufen moechte, so kann
  man dies ueberall mit

    \#shop

  erreichen. Dies kann als eine etwas allgemeinere Funktion von dem
  obigen Beispiel mit den Bonbons von der Rieseninsel angesehen werden.
  Hier wird eine Liste von Shops gebraucht und ein Index, welcher nach jeder
  Nutzung erhoeht wird. In dem Beispiel sind persoenliche Shop-Knoten noch zu
  ergaenzen. Hierbei ist beruecksichtigt, dass es Shops gibt, die in allen
  Welten erreichbar sind, sowie auch Shops, die nur in der Normalwelt
  erreichbar sind, zum Beispiel der Shop in Moulokin. Das macht den Code ein
  wenig unschoener, wenn man das beruecksichtigen will. Alternativ kann man
  auch sich einschraenken indem man den Verkauf von Kram nur in der Normalwelt
  erlaubt und somit nur eine Liste nutzen muss. Das ist jedem selbst
  ueberlassen.


