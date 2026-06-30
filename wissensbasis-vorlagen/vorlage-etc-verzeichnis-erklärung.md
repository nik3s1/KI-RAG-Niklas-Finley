# Wofür wird das Verzeichnis `/etc` verwendet?

## Zweck des Verzeichnisses `/etc`

Das Verzeichnis `/etc` enthält systemweite Konfigurationsdateien eines Linux-Systems.

Hier werden Einstellungen gespeichert, die das Verhalten des Betriebssystems, von Diensten und installierten Programmen beeinflussen.

Das Verzeichnis enthält in der Regel keine ausführbaren Programme, sondern hauptsächlich Textdateien mit Konfigurationen.

---

## Bedeutung von `/etc`

Der Name `/etc` stammt historisch von „et cetera“ (lateinisch für „und so weiter“).

Heute wird das Verzeichnis als zentraler Speicherort für Systemkonfigurationen verwendet.

Nahezu jeder wichtige Dienst unter Linux besitzt eine oder mehrere Konfigurationsdateien in diesem Verzeichnis.

---

## Eigenschaften von `/etc`

* Enthält systemweite Konfigurationen
* Meist Textdateien
* Änderungen wirken sich häufig auf das gesamte System aus
* Viele Dateien können mit einem Texteditor bearbeitet werden
* Für Änderungen sind oft Administratorrechte erforderlich

---

## Beispiele für wichtige Dateien in `/etc`

### Hostname des Systems

Datei:

```bash id="host1"
/etc/hostname
```

Beispielinhalt:

```text id="host2"
server01
```

Diese Datei definiert den Namen des Systems.

---

### Informationen zu Benutzern

Datei:

```bash id="user1"
/etc/passwd
```

Diese Datei enthält Informationen über lokale Benutzerkonten.

Beispiel:

```text id="user2"
max:x:1000:1000:Max Mustermann:/home/max:/bin/bash
```

---

### Gruppeninformationen

Datei:

```bash id="group1"
/etc/group
```

Diese Datei enthält Informationen über Benutzergruppen.

---

### DNS-Konfiguration

Datei:

```bash id="dns1"
/etc/resolv.conf
```

Beispiel:

```text id="dns2"
nameserver 8.8.8.8
```

Die Datei definiert die verwendeten DNS-Server.

---

### Zuordnung von Hostnamen

Datei:

```bash id="hosts1"
/etc/hosts
```

Beispiel:

```text id="hosts2"
127.0.0.1 localhost
```

Hier können lokale Namensauflösungen definiert werden.

---

## Wichtige Unterverzeichnisse in `/etc`

### `/etc/ssh`

Enthält Konfigurationsdateien für den SSH-Dienst.

Beispiel:

```bash id="ssh1"
/etc/ssh/sshd_config
```

Hier wird festgelegt, wie SSH-Verbindungen angenommen werden.

---

### `/etc/systemd`

Enthält Konfigurationen für den System- und Dienstmanager systemd.

---

### `/etc/network`

Auf vielen Linux-Systemen befinden sich hier Netzwerkkonfigurationen.

---

### `/etc/apache2`

Bei installiertem Apache-Webserver befinden sich hier dessen Konfigurationsdateien.

---

## Konfigurationsdateien anzeigen

Dateien in `/etc` können mit verschiedenen Befehlen gelesen werden.

Beispiel:

```bash id="view1"
cat /etc/hostname
```

oder

```bash id="view2"
less /etc/passwd
```

---

## Konfigurationsdateien bearbeiten

Zur Bearbeitung werden häufig Editoren verwendet.

Beispiel:

```bash id="edit1"
sudo nano /etc/hostname
```

oder

```bash id="edit2"
sudo vi /etc/hostname
```

Administratorrechte sind häufig erforderlich.

---

## Typische Anwendungsfälle

### Hostname ändern

Datei bearbeiten:

```bash id="case1"
/etc/hostname
```

---

### SSH konfigurieren

Datei bearbeiten:

```bash id="case2"
/etc/ssh/sshd_config
```

---

### DNS-Server anpassen

Datei bearbeiten:

```bash id="case3"
/etc/resolv.conf
```

---

### Benutzerinformationen prüfen

Datei anzeigen:

```bash id="case4"
/etc/passwd
```

---

## Zusammenhang mit dem Linux-Dateisystem

Das Verzeichnis `/etc` gehört zur Standardstruktur eines Linux-Systems.

Andere wichtige Verzeichnisse sind:

| Verzeichnis | Zweck                             |
| ----------- | --------------------------------- |
| `/bin`      | Wichtige Befehle und Programme    |
| `/home`     | Benutzerverzeichnisse             |
| `/var`      | Variable Daten und Logdateien     |
| `/usr`      | Programme und Bibliotheken        |
| `/tmp`      | Temporäre Dateien                 |
| `/etc`      | Systemweite Konfigurationsdateien |

---

## Häufige Fehler und Stolpersteine

### Konfigurationsdateien ohne Backup ändern

Problem:

Eine fehlerhafte Änderung kann dazu führen, dass ein Dienst nicht mehr startet.

Empfehlung:

Vor Änderungen eine Sicherung erstellen:

```bash id="err1"
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

---

### Änderungen werden nicht wirksam

Viele Dienste müssen nach einer Konfigurationsänderung neu gestartet werden.

Beispiel:

```bash id="err2"
sudo systemctl restart ssh
```

---

### Dateien versehentlich löschen

Das Löschen wichtiger Dateien in `/etc` kann zu Systemproblemen führen.

Beispiel:

```bash id="err3"
sudo rm /etc/hosts
```

Dies kann die lokale Namensauflösung beeinträchtigen.

---

### Schreibrechte fehlen

Fehlermeldung:

```text id="err4"
Permission denied
```

Ursache:

Der Benutzer besitzt keine Administratorrechte.

Lösung:

```bash id="err5"
sudo nano /etc/hostname
```

---

## Zusammenfassung

Das Verzeichnis `/etc` enthält die systemweiten Konfigurationsdateien eines Linux-Systems.

Wichtige Merkmale:

* Zentrale Ablage für Konfigurationen
* Enthält meist Textdateien
* Beeinflusst das Verhalten von System und Diensten
* Typische Dateien sind:

  * `/etc/hostname`
  * `/etc/passwd`
  * `/etc/group`
  * `/etc/hosts`
  * `/etc/resolv.conf`
* Änderungen erfordern häufig Administratorrechte
* Vor Änderungen sollten Sicherungskopien erstellt werden
