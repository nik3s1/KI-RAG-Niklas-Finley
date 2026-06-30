# Wofür wird der Befehl `chmod` verwendet?

## Zweck von `chmod`

Der Linux-Befehl `chmod` (Change Mode) wird verwendet, um die Zugriffsrechte von Dateien und Verzeichnissen zu ändern.

Mit `chmod` kann festgelegt werden:

* Wer eine Datei lesen darf
* Wer eine Datei schreiben darf
* Wer eine Datei ausführen darf

Die Rechte können für verschiedene Benutzergruppen vergeben oder entzogen werden.

---

## Benutzergruppen bei Linux-Dateirechten

Linux unterscheidet drei Gruppen:

| Gruppe     | Bedeutung                  |
| ---------- | -------------------------- |
| User (u)   | Besitzer der Datei         |
| Group (g)  | Zugeordnete Benutzergruppe |
| Others (o) | Alle anderen Benutzer      |

---

## Arten von Berechtigungen

Es gibt drei grundlegende Berechtigungen:

| Symbol | Bedeutung           |
| ------ | ------------------- |
| r      | Lesen (read)        |
| w      | Schreiben (write)   |
| x      | Ausführen (execute) |

Beispiel:

```bash
-rwxr-xr--
```

Bedeutung:

* Besitzer: lesen, schreiben, ausführen
* Gruppe: lesen, ausführen
* Andere: nur lesen

---

## Berechtigungen mit Symbolen ändern

Rechte können symbolisch vergeben oder entfernt werden.

### Ausführungsrecht hinzufügen

```bash
chmod +x script.sh
```

Das Skript wird ausführbar.

### Schreibrecht für Gruppe entfernen

```bash
chmod g-w datei.txt
```

Die Gruppe verliert das Schreibrecht.

### Leserecht für andere hinzufügen

```bash
chmod o+r datei.txt
```

Andere Benutzer dürfen die Datei lesen.

---

## Berechtigungen mit Zahlen ändern

Rechte können auch numerisch angegeben werden.

### Zahlenwerte

| Recht | Wert |
| ----- | ---- |
| r     | 4    |
| w     | 2    |
| x     | 1    |

Die Werte werden addiert.

Beispiele:

| Zahl | Rechte |
| ---- | ------ |
| 7    | rwx    |
| 6    | rw-    |
| 5    | r-x    |
| 4    | r--    |

---

## Beispiel: `chmod 755`

```bash
chmod 755 script.sh
```

Bedeutung:

| Gruppe   | Wert | Rechte |
| -------- | ---- | ------ |
| Besitzer | 7    | rwx    |
| Gruppe   | 5    | r-x    |
| Andere   | 5    | r-x    |

Ergebnis:

```bash
-rwxr-xr-x
```

Der Besitzer darf alles, alle anderen dürfen lesen und ausführen.

---

## Beispiel: `chmod 644`

```bash
chmod 644 dokument.txt
```

Bedeutung:

| Gruppe   | Wert | Rechte |
| -------- | ---- | ------ |
| Besitzer | 6    | rw-    |
| Gruppe   | 4    | r--    |
| Andere   | 4    | r--    |

Ergebnis:

```bash
-rw-r--r--
```

Nur der Besitzer darf die Datei verändern.

---

## Anwendung bei Verzeichnissen

Auch Verzeichnisse besitzen Berechtigungen.

Beispiel:

```bash
chmod 755 projektordner
```

Dadurch können andere Benutzer den Ordner betreten und dessen Inhalte lesen, aber keine Dateien verändern.

---

## Typische Anwendungsfälle

### Skript ausführbar machen

```bash
chmod +x backup.sh
```

### Webseite lesbar machen

```bash
chmod 644 index.html
```

### Verzeichnis für mehrere Benutzer freigeben

```bash
chmod 775 projektordner
```

---

## Häufige Fehler und Stolpersteine

### Ausführungsrecht vergessen

Ein Skript kann nicht direkt gestartet werden:

```bash
./script.sh
```

Fehlermeldung:

```text
Permission denied
```

Lösung:

```bash
chmod +x script.sh
```

---

### Zu viele Rechte vergeben

Problem:

```bash
chmod 777 datei.txt
```

Bedeutung:

* Jeder darf lesen
* Jeder darf schreiben
* Jeder darf ausführen

Dies stellt häufig ein Sicherheitsrisiko dar.

---

### Verzeichnis und Datei verwechseln

Bei Verzeichnissen bedeutet das Ausführungsrecht (`x`) nicht „Programm starten“.

Es erlaubt Benutzern, das Verzeichnis zu betreten und dessen Inhalte aufzurufen.

---

## Zusammenfassung

Der Befehl `chmod` wird verwendet, um Dateirechte und Verzeichnisrechte unter Linux zu ändern.

Wichtige Punkte:

* `r` = Lesen
* `w` = Schreiben
* `x` = Ausführen
* Rechte können symbolisch oder numerisch vergeben werden.
* Häufig verwendete Werte sind:

  * `755` für ausführbare Skripte und Verzeichnisse
  * `644` für normale Dateien
* Zu weit gefasste Rechte wie `777` sollten möglichst vermieden werden.
