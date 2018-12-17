# System-Programmierung
## Hands-on zu Lektion 12
Für Slides und Code Beispiele, siehe [Lektion 12](../../../fhnw-syspr/blob/master/12/README.md)

> *Achtung: Arbeiten Sie nicht direkt auf diesem Repository.*<br/>
> *[Prüfen Sie die vorhandenen Forks, um das Repository für Ihre Klasse zu finden.](../../network/members)*

### a) Message Queues, 30'
* Lesen Sie die folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programme:<pre>
[pmsg_create.c](http://man7.org/tlpi/code/online/book/pmsg/pmsg_create.c.html), [pmsg_getattr.c](http://man7.org/tlpi/code/online/book/pmsg/pmsg_getattr.c.html), [pmsg_unlink.c](http://man7.org/tlpi/code/online/book/pmsg/pmsg_unlink.c.html), [pmsg_send.c](http://man7.org/tlpi/code/online/book/pmsg/pmsg_send.c.html) und [pmsg_receive.c](http://man7.org/tlpi/code/online/book/pmsg/pmsg_receive.c.html)</pre>
* Testen Sie eine Message Queue mit den Kommandos:<pre>
    $ ./pmsg_create -cx /my_mq
    $ ./pmsg_send /my_mq "my msg a" 0 # Prio. 0
    $ ./pmsg_send /my_mq "my msg b" 1 # > 0 => Skip
    $ ./pmsg_receive /my_mq # Blockierend
    $ ./pmsg_unlink /my_mq</pre>

### b) Notifications, 30'
* Lesen Sie die folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programme:<pre>
[mq_notify_via_signal.c](http://man7.org/tlpi/code/online/book/pmsg/mq_notify_via_signal.c.html), [mq_notify_via_thread.c](http://man7.org/tlpi/code/online/book/pmsg/mq_notify_via_thread.c.html)</pre>
* Testen sie Notifications mit den Kommandos:<pre>
$ ./pmsg_create -cx /my_mq
$ ./mq_notify_via_signal /my_mq # bzw. _thread
$ ./pmsg_send /my_mq "my msg a" 0 # Prio. 0
$ ./pmsg_send /my_mq "my msg b" 0
$ ./pmsg_unlink /my_mq</pre>

### c) Semaphore, 15'
* Lesen Sie die folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programme:<pre>
[psem_create.c](http://man7.org/tlpi/code/online/book/psem/psem_create.c.html), [psem_wait.c](http://man7.org/tlpi/code/online/book/psem/psem_wait.c.html), [psem_getvalue.c](http://man7.org/tlpi/code/online/book/psem/psem_getvalue.c.html), [psem_post.c](http://man7.org/tlpi/code/online/book/psem/psem_post.c.html) und [psem_unlink.c](http://man7.org/tlpi/code/online/book/psem/psem_unlink.c.html)</pre>
* Testen Sie ein Semaphor mit den Kommandos:<pre>
$ ./psem_create -c /my_sem 600 0
$ ./psem_wait /my_sem &
$ ./psem_getvalue /my_sem
$ ./psem_post /my_sem
$ ./psem_unlink /my_sem</pre>

### Shared Memory, 15'
* Lesen Sie die folgenden [TLPI](http://man7.org/tlpi/) Beispiel Programme:<pre>
[pshm_create.c](http://man7.org/tlpi/code/online/book/pshm/pshm_create.c.html), [pshm_write.c](http://man7.org/tlpi/code/online/book/pshm/pshm_write.c.html), [pshm_read.c](http://man7.org/tlpi/code/online/book/pshm/pshm_read.c.html) und [pshm_unlink.c](http://man7.org/tlpi/code/online/book/pshm/pshm_unlink.c.html)</pre>
* Testen Sie Shared Memory mit den Kommandos:<pre>
$ ./pshm_create -c /my_shm 0
$ ls -l /dev/my_shm
$ ./pshm_write /my_shm "hello"
$ ./pshm_read /my_shm
$ ./pshm_unlink /my_shm</pre>

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
