# Wegeskript

Dieses README ist noch nicht vollstaendig. Im Laufe der kommenden Tage werde ich es nach und nach bearbeiten.
Das Skript selbst ist aber voll funktionstuechtig und kann bereits benutzt werden. Zum Teil gibt es auch Erklaerungen im Code.

Dieses Skript ist in Lua fürs [Mudlet](https://www.mudlet.org/) geschrieben.
Das Skript habe ich fuer mich selbst zur Nutzung in [Morgengrauen](http://mg.mud.de) erstellt, so dass gewisse Rahmenbedingungen erfuellt sein muessen, siehe Installation. Generell ist es aber auch auf andere Spiele uebertragbar.

### Inhaltsverzeichnis

1. Was ist das Wegeskript
2. Installation
3. Wie kann man das Wegeskript nutzen?
4. Das Wegeskript wurde geupdatet. Muss ich nun wieder alle Punkte speichern um die neue Version zu nutzen?
5. Wegaufzeichnung / Wie speichere ich Punkte fuer das Wegeskript?

     5.1. Basispunkt

     5.2. Wegaufzeichnung starten/stoppen/fortsetzen

     5.3. Manuell Bewegungsaktion hinzufuegen

     5.4. Anzeige des bisher aufgezeichneten Weges

     5.5. Korrektur falsch eingegebener manueller Bewegungsaktionen

     5.6. Punkt speichern
     
     5.7. Speichern nur des Hinweges oder nur des Rueckweges

     5.8. Tipps/Tricks fuer effektive Wege

6. Schnelles Reisen mit dem Wegeskript

7. Bearbeitung von gespeicherten Punkten (coming soon)

     7.1. Namen aendern (coming soon)
     
     7.2. ID auslesen, hinzufuegen oder loeschen (coming soon)
     
     7.3. Titel aendern (coming soon)
     
8. Gespeichtern Punkt loeschen (coming soon)

9. Suchfunktion fuer die gespeichten Punkte (coming soon)

10. Externe Speicherung der Wege mit automatischem monatlichen Backup (coming soon)

11. Super-Safe-Modus (coming soon)

## 1. Was ist das Wegeskript

Das Wegeskript ermoeglicht schnelles Reise zwischen beliebigen gespeichtern Punkten im Spiel. Es gibt sogar eine Syntax, bei der man nur das Ziel eingeben muss und das Skript automatisch erkennt, wenn man sich an einem gespeicherten Ort befindet um dann den Weg zum Ziel zu finden.

## 2. Installation

1. Man installiere mein ["evented navigation"](https://github.com/Mundron/Evented-Navigation):

     evented_number_pad.xml runterladen, im Mudlet Alt+O druecken oder unter Werkzeuge auf Pakete klicken, 
     dann auf "Installieren" und die runtergeladene Datei auswählen.
2. Installiere dieses Skript:

     Wegeskript.xml runterladen, im Mudlet Alt+O druecken oder unter Werkzeuge auf Pakete klicken, 
     dann auf "Installieren" und die runtergeladene Datei auswählen.
3. Arbeitsordner zum Speichern der Wege einstellen:

     Wenn Schritt 2 fertig ist, dann unter "Skripte" den Wegeskript-Ordner oeffnen (ggf ist darin noch ein Ordner...)
     Das Element "Core" auswaehlen. Die Zeile mit dem Inhalt
     
        PF = {directory="C:/Users/Mundron/Documents/Morgengrauen/Einstellungen/",
     
     suchen, was Zeile 10 sein sollte.
     Zwischen den Anfuehrungszeichen " " den Pfad eingeben, wo der Wegeskript die Wege speichern darf.
    
    
 ## 3. Wie kann man das Wegeskript nutzen?
 
 Als erstes muessen natuerlich die Punkte im Spiel gespeichert werden zwischen denen man schnell reisen moechte.
 Dazu beeinhaltet das Wegeskript auch eine Wegaufzeichnung. Wenn wir zum Beispiel 10 Punkte im Spiel speichern wollen,
 dann braucht man 45 verschiede Wege um von jedem dieser 10 Punkte zu jedem reisen zu koennen. Klingt noch ueberschaubar, 
 aber bei 100 Punkten sind es schon 5.050 Wege und dann wird es nicht mehr lustig...
 
 Daher ist ein wesentliches Konzept dieses Wegeskriptes, dass man sich in einem Gebiet einen zentralen Punkte auswaehlt. 
 Sozusagen einen Basispunkt. Und dann speichert man sich einen Punkt indem man den Hin- und Rueckweg vom Basispunkt 
 zum neuen Punkt aufzeichnet (mit dem Skript, siehe weiter unten). Wenn man dann von Punkt A nach B reisen will, dann laeuft
 das Wegeskript von A zum Basispunkt und dann vom Basispunkt nach B. Damit braucht man lediglich zwei Wege pro 
 gespeicherten Punkt zu sichern.
 
 Natuerlich gibt es auch Orte, von von diesem Basispunkt aus nicht mit dem Skript erreichbar sind. 
 Zum Beispiel Orte, die man nur mit Gefaehrten, wie Schiffe, erreichen kann. Man muss auch dort das Wegeskript nutzen!
 Dazu muss man sich lediglich in jedem getrennten Gebiet einen neuen Basispunkt auswaehlen.
 Das Wegeskript ist auch in der Lage zu erkennen, ob man sich an einem gespeicherten Punkt befindet, so dass man nur
 den Zielpunkt eingeben muss.
 
 ## 4. Das Wegeskript wurde geupdatet. Muss ich nun wieder alle Punkte speichern um die neue Version zu nutzen?
 
 Nein, das Wegeskript wurde bewusst so geschrieben, dass alle Wege in einer Textdatei im Arbeitsordner gespeichert werden.
 Wenn du die neue Version nutzen willst, dann musst du erstmal das alte Wegeskript vom Client loeschen. 
 Dazu loeschst du den gesamten Ordner bei Aliase und Skripte, die beim Installieren des Wegeskriptes dazugekommen sind.
 (Die Ordner haben im Namen dann Wegeskript oder Pathscript).
 
 Anschliessend laedt man sich wieder Wegeskript.xml runter und installiert das Paket, wie oben bei Schritt 2 erklaert wurde.
 Ebenso muss Schritt 3 auch erneut ausgefuehrt werden. Die alten Wege sollten dann automatisch erkannt und geladen werden.
 
 ## 5. Wegaufzeichnung / Wie speichere ich Punkte fuer das Wegeskript?
 
 Jede notwendige Bearbeitung verlaeuft im Skript. Die Aliase sind lediglich dafuer da um die entsprechenden Funktionen 
 im Spiel aufrufen zu koennen. Man startet die Wegaufzeichnung am Basispunkt und benutzt das Nummerfeld zur Bewegung.
 Dabei wird automatisch vom Wegeskript die eingegebene Richtung gespeichert. Automatisch wird auch die Rueckrichtung
 gespeichert! 
 
 Wenn man nun nicht das Nummerfeld benutzen moechte oder man einen bestimmen Befehl braucht um den naechsten Raum 
 zu betreten, zum Beispiel "betrete haus", dann muss man diese Bewegungsaktion "manuell" an die Wegaufzeichnung eingeben.
 Dann muss aber auch die Bewegungsaktion fuer den Rueckweg eingeben. Dazu gibt es aber auch vorgefertigte Alias-Befehle.
 
 Wenn man am Punkt angekommen ist, den man speichern moechte, dann stoppt man die Wegaufzeichnung und speichert den Punkt.
 Dabei braucht der Punkt wenigstens einen Namen und einen Titel. Die Raum-ID zum Erkennen des Raumes, wird automatisch von
 der Wegaufzeichnung gespeichert.
 
 Es ist aber auch moeglich, dass man statt den Weg vom Basispunkt den Weg von einem anderen in der Naehe befindlichen 
 Punkt aufzeichnet und das dann mit angibt.
 
 Wenn man sich an dem zu speichernden Punkt befindet, muss man nicht zwingend vom Basispunkt dahin laufen, sondern man 
 kann die Wegaufzeichnung am zu speichernden Punkt startet und zum Basispunkt laufen. Dann uebergibt man beim Speichern
 einen weiteren Parameter, womit das Wegeskript die Wege richtig herum speichert.
 
 ### 5.1. Basispunkt
 
 Der Basispunkt ist ein Bezugspunkt, der aber nicht gesondert gespeichert oder erwaehnt werden muss. Du musst fuer dich
 selbst bestimmen wo der Basispunkt sein soll. Was letztendlich gespeichert wird ist ein Hin- und Rueckweg zu einem Punkt.
 Der Wegeskript geht automatisch davon aus, dass der Rueckweg immer zu einem Basispunkt fuehrt. Deswegen ist es kein Problem
 in verschiedenen Gebieten auch unterschiedliche Basispunkte zu benutzen.
 
 ### 5.2. Wegaufzeichnung starten/stoppen/fortsetzen
 
 Dazu kann man die Befehle
 
         #wa start
         #wa stop
         #wa weiter
 benutzen.

### 5.3. Manuell Bewegungsaktion hinzufuegen

Mit

        #vor <aktion>
        
gibt man manuell die Bewegungsaktion <aktion> an die Wegaufzeichnung weiter UND gleichzeitig wird dieser auch ausgefuehrt.
Damit braucht nicht die Aktion zur Bewegung eingeben und es an die Wegaufzeichnung weitergeben, sondern man kann beides mit 
diesem einen Befehl machen.
  
  Beispiel: \#vor betrete haus
 
  
  Damit wir die Aktion "betrete haus" ausgefuehrt und an die Wegaufzeichnung weiter gegeben.
  
  
  Fuer den Rueckweg benutzt man in dem Raum den Befehl
  
        #zurueck <aktion>
  
  Im Gegensatz zum Hinweg wird bei dieser Befehl die Aktion _NICHT_ ausgefuehrt. Wenn mehrere Aktionen fuer den Rueckweg 
  noetig sind, dann muss man sie in der Reihenfolge eingeben, in der sie ausgefuehrt werden soll. Muss man zum Beispiel eine 
  Tuer zuerst oeffnen und damit man das Haus betreten kann, dann gibt man in der Reihen Folge auch ein:
  
        #zurueck oeffne tuer
        #zurueck betrete haus
        

### 5.4. Anzeige des bisher aufgezeichneten Weges

Mit dem Befehl

        #zeigeweg <anzahl>
        
kann man sich die letzten \<anzahl> gespeicherten Bewegungsaktionen sowohl vom Hin- als auch dem Rueckweg anzeigen lassen.
Gibt man als Anzahl 0 ein, dann wird der gesamte aufgezeichnete Weg angezeigt. 

Beispiel: \#zeigeweg 5

Zeigt die letzten 5 gespeicherten Bewegungsaktionen.

### 5.5. Korrektur falsch eingegebener manueller Bewegungsaktionen

Mit

        #lvor <anzahl>
        #lzurueck <anzahl>
        
werden die letzten \<anzahl> viel Bewegungsaktionen geloescht.

Beispiel: \#lvor 3

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
          #sweg sandtiger:Der Sandtiger beim Wettpalast am Westeingang von Port Vain
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
dass jeder Weg mit einem Teleport-Befehle zum entsprechenden Portal beginnen muss!


## 6. Schnelles Reisen mit dem Wegeskript

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
  
## 7. Bearbeitung von gespeicherten Punkten (coming soon)

### 7.1. Namen aendern (coming soon)
     
###  7.2. ID auslesen, hinzufuegen oder loeschen (coming soon)
     
###  7.3. Titel aendern (coming soon)
     
## 8. Gespeichtern Punkt loeschen (coming soon)

## 9. Suchfunktion fuer die gespeichten Punkte (coming soon)
