# Wegeskript

Ausfuehrliches README wird die naechsten Tage nachgereicht. Vorneweg schonmal so viel:

Der Code kann bereits als Paket im Mudlet importiert werden. Damit es vollstaendig funktioniert, muss allerdings auch mein "evented navigation" (https://github.com/Mundron/Evented-Navigation) ebenfalls importiert werden (Reihenfolge egal)

Und dann kann das Wegeskript auch gleich genutzt werden. Aber dazu muessen natuerlich erstmal Wege gespeichert werden.
Die gespeicherten Wege befinden sich in einer externen Textdatei. Fuer diesen muesst ihr einmalig einen Pfad im Code eingeben.
Schaut dabei zeu Skripte im Ordner "Mundron: Wegeskript" in das Element "Pathscript Core". Dort sollte in Zeile 10 sowas stehen wie:
[...] directory="C:/Users/ [...]
Hier muesst ihr natuerlich einen Pfad auf eurem PC eingeben, wo die Wege gespeichert werden sollen.

Eines der Vorteile ist, dass ihr bei Verbesserung des Codes den alten Code einfach austauschen koennt und eure Wege dennoch alle gespeichert sind.
Ich empfehle dennoch hin und wieder die Textdatei mit den Wegen zu kopieren und archivieren (ggf baue ich sowas auch noch spaeter ein, mal schauen)


Mit dem Skript kann man zunaechst Wege speichern. Dazu muss man sich ein Zentrum im Spiel suchen. 
Um Wege zwischen zwei Punkten zu haben, muss man immer einen Hin- und Rueckweg von den Punkten zum Zentrum speichern.

Beispiel:
Wir waehlen als Zentrum den Sandtiger. 
Nun koennen wir uns viele Punkte in MG speichern indem wir zu jedem Punkt den Hin- und Rueckweg zum Sandtiger speichern!
Und dann können wir von Punkte A nach B ganz bequem mit #go A B reisen oder sogar auch nur mit #go B, 
denn der Wegeskript erkennt automatisch ob man sich an einem gespeicherten Punkt befindet!
(Allerdings nur, wenn der Charakter nicht blind ist, da dann gmcp nicht die noetigen Daten sendet. 
In dem Fall funktioniert  #go A B trotzdem!)

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

## Funktionen

### \#wa <start|stop|weiter>
Startet die Aufzeichnung des Weges, inklusive Rueckweg!

### \#sweg <namen> <startpunkt> <ruecklaeufig> <titel>
  Dieser Alias ist mehrere Funktionen. Hauptsaechlich geht es darum damit die aufgezeichneten Wege zu speichern.
  Legt man zum Beispiel einen neuen Weg vom Zentrum nach Moulokin an und man moechte dem Punkt den Namen "mk" geben und den Titel "Eingang von Moulokin", dann waere der Befehl
  
  \#sweg mk  h Eingang von Moulokin
  
  Der Parameter <ruecklaeufig> dafuer da, wenn man zum Beispiel den Weg nicht vom Zentrum nach Moulokin aufgezeichnet hat, sondern von Moulokin gestartet ist und zum Zentrum gelaufen. Dann gibt man als diesen Parameter "z" an, ansonsten "h".
  
  Hier wurde als Startpunkt nichts eingegeben, weil es sich um einen Weg vom Zentrum aus handelt! Dennoch muessen die Leerzeichen fuer das Alias ausgehalten werden! Also zwei Leerzeichen zwischen mk und h!
  (Man kann natuerlich auch mehrere Alias machen fuer die verschiedene Faelle, aber das ist mir etwas zu laestig...)
  Wie beschrieben, wenn man den Weg von Moulokin aufzeichnet, dann waere der Alias
  
  \#sweg mk  z Eingang von Moulokin
  
  Im naechsten Beispiel wollen wir beim Polartiger vorm Eingang von Moulokin einen neuen Punkt speichern. Dann starten wir die Wegaufzeichnung im Raum, wo "mk" gespeichert wurde und laeuft zum Polartiger. Mit
  
  \#sweg pt mk h Polartiger nahe Moulokin
  
  wird der Weg von "mk" ausgehend bis zum Polartiger gespeichert. Man kann nun "pt" als eigenstaendigen Punkt ansehen und auch von diesem oder zu diesem reisen.
  
  Wenn man moechte, dann kann man mit diesem Alias auch Wege nur _temporaer_ speichern. Temporaer heisst hier, dass man den Weg benutzen kann, solange man mit dem Wegeskript nicht alle Wege neu laedt oder man den Client schliesst. Dies erreicht man, indem man den Titel einfach weglaesst, also zum Beispiel mit

\#sweg pt mk h 

Dies kann praktisch sein, wenn man fuers Metzeln sich einen Weg anlegen moechte, von dem man weiss, dass man ihn nachher nicht mehr braucht. Damit kann man sich die kurzen Namen fuer die wichtigen Punkte aufheben. Hier ist es auch sehr wichtig zu beachten, dass nach dem h noch ein Leerzeichen steht obwohl der Titel dahinter fehlt!

### \#go <start?> <ziel>
  Grundsaetzlich gibt es zwei Moeglichkeiten mit dem Wegeskript von einem Punkt zu einem anderen zu kommen.
  1. Moeglichkeit:
  Blindes Laufen mit \#go <start> <ziel> vom Punkt <start> nach Punkt <ziel>. Der gespeicherte Weg ueber das Zentrum wird abgelaufen, selbst wenn man sich nicht bei <start> befindet.
  2. Moeglichkeit:
  Automatisches Laufen mit \#go <ziel>. Dabei ermittelt der Wegeskript aus der Raum-ID, ob an dem Standort sich ein gespeicherter Punkt befindet. Falls dem so ist, dann laeuft man zum Punkt <ziel>. Befindet man sich aber in keinem gespeicherten Punkt, dann kommt nur eine Fehlermeldung. Dies hat nicht nur den Vorteil, dass man keinen Startraum angeben muss, sondern auch noch, dass der Wegeskript nicht blind laeuft und man moeglicherweise ein einem ungewuenschten Ort landet oder gar auf einem Weg stirbt. Jedoch gibt es auch Situationen, wo auch diese Moeglichkeit zu Problemen fuehrt, naemlich wenn der Charakter im Spiel erblindet ist. In dem Fall wird vom gmcp die Raum-Infos _nicht_ aktualisiert! Ist man also in einem gespeicherten Punkt erblindet, dann kann man zwar von diesem zu einem anderen Punkt noch laufen, aber da die Raumdaten nicht aktualisert sind, erkennt das Wegeskript dies nicht. Es wird also im neuen Punkt immer noch glauben, im alten Punkt zu sein. Wenn man von dort weiterlaufen will, wuerde man wieder blind laufen. In diesem Fall ist die 1. Moeglichkeit vorzuziehen, was aber auch voraussetzt selbst sicher zu wissen in welchem Raum man steht. Und falls man in einem Raum erblindet, welches kein gespeicherter Punkt ist,
  dann kann man diese Funktion des Wegeskriptes gar nicht benutzen, solange man erblindet ist.
