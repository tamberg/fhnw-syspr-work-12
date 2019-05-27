# System-Programmierung
## Hands-on zu Lektion 12
Für Slides und Code Beispiele, siehe [Lektion 12](../../../fhnw-syspr/blob/master/12/README.md)

> *Achtung: Arbeiten Sie nicht direkt auf diesem Repository.*<br/>
> *[Prüfen Sie die vorhandenen Forks, um das Repository für Ihre Klasse zu finden.](../../network/members)*

### a) Kalender-Zeit, 15'
* Lesen Sie das folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programm:<pre>
[calendar_time.c](http://man7.org/tlpi/code/online/book/time/calendar_time.c.html)</pre>
* Vergleichen Sie den Output der Kommandos:<pre>
$ ./date
$ ./calendar_time</pre>
* Schreiben Sie ein eigenes Programm, welches den Überlauf von Sekunden bei *mktime()* zeigt.

### b) Zeit parsen / formatieren, 10'
* Lesen Sie das folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programm:<pre>
[strtime.c](http://man7.org/tlpi/code/online/book/time/strtime.c.html)</pre>
* Vergleichen Sie den Output der Kommandos:<pre>
$ ./strtime "9:39:46pm 1 Feb 2011" "%I:%M:%S%p %d %b %Y"
$ ./strtime "9:39:46pm 1 Feb 2011" "%I:%M:%S%p %d %b %Y" "%F %T"</pre>
* Geben Sie das Datum im [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) Format aus.

### c) Locale, 15'
* Schreiben Sie ein Programm *my_locale.c*, welches die Zahl *10'000.5* in zwei verschiedenen Locales ausgibt.
* Prüfen Sie, ob die Locale nach Programmende bleibt.
* Falls ja, erweitern Sie ihr Programm, um am Ende die vor dem Aufruf gesetzte Locale wieder herzustellen.

### d) Zeitmessung, 15'
* Schreiben Sie ein eigenes *time* Programm, *my_time.c*
* Das zu messende Programm soll aus *argv* gelesen und mit *fork()* und *execve()* gestartet werden.
* Der Parent Prozess wartet mit *wait()*, und bestimmt die Laufzeit, real und CPU Zeit, des Child Prozesses.
* Die Ausgabe soll derjenigen von *time* entsprechen.

### e) Timer, 15'
* Lesen Sie das folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programm:<pre>
[real_timer.c](http://man7.org/tlpi/code/online/book/timers/real_timer.c.html)</pre>
* Testen Sie den Timer, z.B. mit den Kommandos:<pre>
$ ./real_timer 1 800000 1 0 # 1.8s, 1s Periode
$ ./real_timer 3 0 # einmaliger Timer, nach 3s</pre>
* Ändern Sie das Programm, dass der Timer CPU Zeit
statt reale Zeit verwendet, und testen Sie den Code.

### Abgabe (optional)
* Lokale Änderungen [committen und pushen](#git).
* GitHub [Issue erstellen](../../issues/new) mit "Bitte um Review, @tamberg".
* Offene Fragen ausformulieren, was geht nicht, was haben Sie versucht.
* GitHub mailt mir (@tamberg) automatisch, ich versuche in weniger als 24h zu antworten :)

## Tools
### Git
Auf Ihrem Computer
* Zu Beginn jeder Lektion wird ein Hands-on Repository Link freigeschaltet
* Nachdem Sie das "Assessment" annehmen, bekommen Sie per Email ein Repository
* Die REPO_URL enthält Ihren GitHub Account USER_NAME und Ihre Klasse 3ia oder 3ib, z.B.<br/>
            https://github.com/fhnw-syspr-3ia/fhnw-syspr-work-12-tamberg

Auf dem Raspberry Pi
* Repository klonen<pre>
    $ cd ~
    $ git clone REPO_URL</pre>
* Neue Datei kreieren<pre>
    $ git add FILE</pre>
* Änderungen committen<pre>
    $ git commit FILE -m "Fixed all bugs"</pre>
* Änderungen hochladen<pre>
    $ git push</pre>

### Nano
Auf dem Raspberry Pi
* Neue oder bestehende Datei öffnen mit $ nano FILE
* Editieren (Achtung, nano hat kein Undo)
* Speichern mit `CRTL-X` `Y` `RETURN`

### SSH
Auf Ihrem Computer
* Terminal öffnen (Mac) oder `WINDOWS` `R` cmd `RETURN` (Windows)
* SSH Session starten mit<pre>
    $ ssh pi@raspberrypi.local</pre>

## Support
- [FHNW Syspr Slack](https://fhnw-syspr.slack.com/)
