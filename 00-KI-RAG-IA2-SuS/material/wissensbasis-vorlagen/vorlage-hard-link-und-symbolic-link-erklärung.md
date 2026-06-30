# Was ist der Unterschied zwischen einem Hard Link und einem Symbolic Link?

## Zweck von Links unter Linux

Links ermöglichen es, mehrere Verweise auf Dateien oder Verzeichnisse anzulegen.

Linux unterscheidet zwei Arten von Links:

* Hard Links (harte Links)
* Symbolic Links (symbolische Links oder Soft Links)

Beide dienen dazu, auf bestehende Dateien oder Verzeichnisse zu verweisen, funktionieren jedoch unterschiedlich.

---

## Was ist ein Hard Link?

Ein Hard Link ist ein zusätzlicher Verzeichniseintrag für dieselbe Datei.

Mehrere Hard Links verweisen auf denselben Inode und damit auf dieselben Daten auf der Festplatte.

Es gibt keinen „Original-Link“ und keine „Kopie“. Alle Hard Links sind gleichwertige Verweise auf dieselbe Datei.

---

## Hard Link erstellen

Syntax:

```bash
ln QUELLE LINKNAME
```

Beispiel:

```bash
ln dokument.txt dokument_hardlink.txt
```

Danach verweisen beide Dateinamen auf dieselben Daten.

---

## Eigenschaften von Hard Links

* Verweisen direkt auf denselben Inode
* Änderungen sind über alle Hard Links sichtbar
* Benötigen keinen zusätzlichen Speicher für den Dateiinhalt
* Die Datei bleibt erhalten, solange mindestens ein Hard Link existiert
* Funktionieren normalerweise nur innerhalb desselben Dateisystems

---

## Beispiel für Hard Links

Datei erstellen:

```bash
echo "Hallo Welt" > datei.txt
```

Hard Link erstellen:

```bash
ln datei.txt link.txt
```

Datei ändern:

```bash
echo "Neue Zeile" >> link.txt
```

Anzeige:

```bash
cat datei.txt
```

Ausgabe:

```text
Hallo Welt
Neue Zeile
```

Die Änderung ist über beide Dateinamen sichtbar.

---

## Was ist ein Symbolic Link?

Ein Symbolic Link (Symlink) ist eine spezielle Datei, die lediglich den Pfad zu einer anderen Datei oder einem Verzeichnis speichert.

Ein Symlink funktioniert ähnlich wie eine Verknüpfung unter Windows.

---

## Symbolic Link erstellen

Syntax:

```bash
ln -s QUELLE LINKNAME
```

Beispiel:

```bash
ln -s dokument.txt dokument_link.txt
```

Der Symlink verweist auf die angegebene Datei.

---

## Eigenschaften von Symbolic Links

* Speichern nur einen Pfad
* Besitzen einen eigenen Inode
* Können auf Dateien und Verzeichnisse verweisen
* Können Dateisystemgrenzen überschreiten
* Werden ungültig, wenn das Ziel gelöscht oder verschoben wird

---

## Beispiel für Symbolic Links

Datei erstellen:

```bash
echo "Hallo Welt" > datei.txt
```

Symlink erstellen:

```bash
ln -s datei.txt link.txt
```

Inhalt anzeigen:

```bash
cat link.txt
```

Ausgabe:

```text
Hallo Welt
```

Der Symlink leitet den Zugriff auf die eigentliche Datei weiter.

---

## Defekte Symbolic Links

Wird die Zieldatei gelöscht:

```bash
rm datei.txt
```

anschließend:

```bash
cat link.txt
```

Fehlermeldung:

```text
No such file or directory
```

Der Symlink existiert weiterhin, verweist aber auf ein nicht mehr vorhandenes Ziel.

Ein solcher Link wird als „Broken Link“ oder „Dangling Symlink“ bezeichnet.

---

## Hard Link vs. Symbolic Link

| Merkmal                                      | Hard Link          | Symbolic Link |
| -------------------------------------------- | ------------------ | ------------- |
| Verweist auf                                 | Inode              | Pfad          |
| Eigener Inode                                | Nein               | Ja            |
| Funktioniert über Dateisystemgrenzen         | Nein               | Ja            |
| Verweis auf Verzeichnisse möglich            | Normalerweise nein | Ja            |
| Funktioniert nach Löschen des Originalnamens | Ja                 | Nein          |
| Kann defekt werden                           | Nein               | Ja            |

---

## Links anzeigen

Dateien mit Details anzeigen:

```bash
ls -l
```

Beispielausgabe:

```text
lrwxrwxrwx 1 max max 9 Jun 23 10:00 link.txt -> datei.txt
```

Das führende `l` kennzeichnet einen Symbolic Link.

---

## Inode-Nummern anzeigen

Befehl:

```bash
ls -i
```

Beispiel:

```text
12345 datei.txt
12345 hardlink.txt
67890 symlink.txt
```

Bedeutung:

* Hard Link und Originaldatei besitzen denselben Inode.
* Der Symbolic Link besitzt einen eigenen Inode.

---

## Typische Anwendungsfälle

### Hard Links

Geeignet für:

* Mehrere Dateinamen für dieselben Daten
* Speicherplatzsparende Referenzen
* Backup- und Snapshot-Systeme

---

### Symbolic Links

Geeignet für:

* Verknüpfungen auf häufig genutzte Dateien
* Verweise auf Verzeichnisse
* Flexible Ordnerstrukturen
* Verweise über mehrere Dateisysteme hinweg

---

## Häufige Fehler und Stolpersteine

### Hard Link über Dateisystemgrenzen erstellen

Problem:

```bash
ln /mnt/disk1/datei.txt /mnt/disk2/link.txt
```

Fehlermeldung:

```text
Invalid cross-device link
```

Ursache:

Hard Links funktionieren nur innerhalb desselben Dateisystems.

---

### Symbolic Link zeigt auf falschen Pfad

Problem:

```bash
ln -s datei.txt link.txt
```

Wenn der Pfad falsch angegeben wurde, funktioniert der Link nicht.

Prüfung:

```bash
ls -l link.txt
```

---

### Zieldatei eines Symlinks löschen

Problem:

```bash
rm datei.txt
```

Der Symlink bleibt bestehen, verweist jedoch ins Leere.

---

### Hard Link mit einer Kopie verwechseln

Ein Hard Link erzeugt keine neue Datei.

Alle Hard Links greifen auf dieselben Datenblöcke zu.

Änderungen über einen Hard Link sind sofort über alle anderen Hard Links sichtbar.

---

## Zusammenfassung

Linux unterstützt Hard Links und Symbolic Links zur Referenzierung von Dateien und Verzeichnissen.

Wichtige Unterschiede:

* Hard Links verweisen direkt auf denselben Inode.
* Symbolic Links speichern lediglich einen Pfad.
* Hard Links bleiben nach dem Löschen eines Dateinamens funktionsfähig.
* Symbolic Links können defekt werden, wenn das Ziel gelöscht wird.
* Symbolic Links sind flexibler und können auch auf Verzeichnisse sowie andere Dateisysteme verweisen.
