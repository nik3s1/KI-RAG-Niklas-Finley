# Was ist der Unterschied zwischen einem absoluten und einem relativen Pfad?

## Zweck von Pfadangaben

Pfadangaben werden verwendet, um den Speicherort von Dateien und Verzeichnissen in einem Dateisystem zu beschreiben.

Unter Linux können Pfade auf zwei Arten angegeben werden:

* Absoluter Pfad
* Relativer Pfad

Der Unterschied besteht darin, von welchem Ausgangspunkt der Pfad interpretiert wird.

---

## Absoluter Pfad

Ein absoluter Pfad beschreibt den vollständigen Weg zu einer Datei oder einem Verzeichnis.

Er beginnt immer beim Wurzelverzeichnis (`/`).

Beispiel:

```bash
/home/max/dokumente/projekt/datei.txt
```

Der Pfad ist unabhängig vom aktuellen Arbeitsverzeichnis immer gültig.

---

## Eigenschaften eines absoluten Pfades

* Beginnt immer mit `/`
* Beschreibt den vollständigen Speicherort
* Funktioniert unabhängig vom aktuellen Verzeichnis
* Eignet sich für Skripte und Konfigurationen

Beispiel:

```bash
cat /etc/hosts
```

Die Datei wird unabhängig vom aktuellen Verzeichnis geöffnet.

---

## Relativer Pfad

Ein relativer Pfad beschreibt einen Speicherort ausgehend vom aktuellen Arbeitsverzeichnis.

Der Pfad beginnt nicht mit `/`.

Beispiel:

```bash
projekt/datei.txt
```

Die Bedeutung hängt davon ab, in welchem Verzeichnis sich der Benutzer aktuell befindet.

---

## Eigenschaften eines relativen Pfades

* Beginnt normalerweise nicht mit `/`
* Bezieht sich auf das aktuelle Arbeitsverzeichnis
* Ist oft kürzer als ein absoluter Pfad
* Wird häufig bei der täglichen Arbeit in der Shell verwendet

Beispiel:

```bash
cat datei.txt
```

Die Datei muss sich im aktuellen Verzeichnis befinden.

---

## Das aktuelle Arbeitsverzeichnis

Das aktuelle Arbeitsverzeichnis kann mit folgendem Befehl angezeigt werden:

```bash
pwd
```

Beispielausgabe:

```text
/home/max/projekt
```

Von diesem Verzeichnis aus werden relative Pfade berechnet.

---

## Beispiel für absolute und relative Pfade

Angenommen, das aktuelle Arbeitsverzeichnis lautet:

```text
/home/max
```

Die Datei befindet sich hier:

```text
/home/max/projekt/datei.txt
```

Absoluter Pfad:

```bash
/home/max/projekt/datei.txt
```

Relativer Pfad:

```bash
projekt/datei.txt
```

Beide Pfade verweisen auf dieselbe Datei.

---

## Sonderzeichen bei relativen Pfaden

### Aktuelles Verzeichnis (`.`)

Der Punkt steht für das aktuelle Verzeichnis.

Beispiel:

```bash
./script.sh
```

Das Skript wird aus dem aktuellen Verzeichnis gestartet.

---

### Übergeordnetes Verzeichnis (`..`)

Zwei Punkte stehen für das übergeordnete Verzeichnis.

Beispiel:

```bash
cd ..
```

Wechselt eine Ebene nach oben.

---

### Mehrere Ebenen nach oben

Beispiel:

```bash
../../datei.txt
```

Der Pfad wechselt zunächst zwei Verzeichnisebenen nach oben und sucht dort die Datei.

---

## Vergleich von absoluten und relativen Pfaden

| Merkmal                            | Absoluter Pfad           | Relativer Pfad               |
| ---------------------------------- | ------------------------ | ---------------------------- |
| Ausgangspunkt                      | Wurzelverzeichnis (`/`)  | Aktuelles Arbeitsverzeichnis |
| Beginnt mit `/`                    | Ja                       | Nein                         |
| Abhängig vom aktuellen Verzeichnis | Nein                     | Ja                           |
| Länge                              | Oft länger               | Oft kürzer                   |
| Verwendung                         | Skripte, Konfigurationen | Interaktive Shell-Arbeit     |

---

## Typische Anwendungsfälle

### Absoluter Pfad

Geeignet für:

* Shell-Skripte
* Cronjobs
* Konfigurationsdateien
* Automatisierungen

Beispiel:

```bash
cp /home/max/backup/datei.txt /tmp/
```

---

### Relativer Pfad

Geeignet für:

* Tägliche Arbeit in der Shell
* Projekte mit festen Ordnerstrukturen
* Kurze Befehle

Beispiel:

```bash
cd projekt
```

---

## Häufige Fehler und Stolpersteine

### Relativer Pfad funktioniert nicht

Problem:

```bash
cat datei.txt
```

Fehlermeldung:

```text
No such file or directory
```

Ursache:

Die Datei befindet sich nicht im aktuellen Arbeitsverzeichnis.

Lösung:

Aktuelles Verzeichnis prüfen:

```bash
pwd
```

Oder einen absoluten Pfad verwenden.

---

### Verwechslung von `/` und `~`

Beispiel:

```bash
/home/max
```

und

```bash
~
```

sind nicht identisch.

`/home/max` ist ein absoluter Pfad.

`~` ist eine Abkürzung für das Home-Verzeichnis des aktuell angemeldeten Benutzers.

---

### Relativer Pfad in Skripten

Ein Skript mit relativen Pfaden kann fehlschlagen, wenn es aus einem anderen Verzeichnis gestartet wird.

Beispiel:

```bash
cp daten/datei.txt backup/
```

Der Befehl funktioniert nur, wenn das Skript aus dem erwarteten Verzeichnis ausgeführt wird.

Absolute Pfade sind in Skripten häufig robuster.

---

## Zusammenfassung

Pfade beschreiben den Speicherort von Dateien und Verzeichnissen.

Wichtige Unterschiede:

* Ein absoluter Pfad beginnt beim Wurzelverzeichnis (`/`).
* Ein relativer Pfad beginnt beim aktuellen Arbeitsverzeichnis.
* Absolute Pfade funktionieren unabhängig vom aktuellen Standort.
* Relative Pfade sind kürzer und werden häufig in der Shell verwendet.
* Die Sonderzeichen `.` und `..` erleichtern die Navigation mit relativen Pfaden.
