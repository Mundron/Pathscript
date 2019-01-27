# Wegeskript

Ausfuehrliches README wird die naechsten Tage nachgereicht. Vorneweg schonmal so viel:

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
