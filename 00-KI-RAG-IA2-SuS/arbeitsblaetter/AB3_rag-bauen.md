# Arbeitsblatt 3 – Mini-RAG bauen

**Gruppe:** Finley & Niklas  **Domäne:** Linux

> **Ziel:** Ihr baut für eure Domäne eine eigene Wissensbasis und seht im
> direkten Vorher/Nachher-Vergleich, was RAG bewirkt.
> **Hintergrund:** `docs/04_rag-erklaert.md`

---

## Teil A – Verstehen, was RAG ist

**A.1** Wofür steht die Abkürzung RAG?

Retrieval	Augmented	Generation

**A.2** Erkläre den Vergleich „Klassenarbeit ohne / mit Spickzettel" in eigenen
Worten:

Ohne RAG beantwortet das Modell Fragen nur anhand seines trainierten Wissens. Mit RAG bekommt es zusätzlich passende Informationen aus einer Wissensbasis und kann dadurch genauer antworten.

**A.3** Nenne die zwei wichtigsten Faktoren für die Qualität eines RAG-Systems:

1. Qualität und Aktualität der Dokumente
2. Relevanz der gefundenen Informationen

---

## Teil B – VORHER: Modell ohne Wissensbasis

> Wichtig: Dieser Schritt passiert **bevor** ihr Dokumente hochladet.

**B.1** Überlegt euch **5 Fachfragen** zu eurer Domäne, deren korrekte Antwort
ihr kennt. Tragt sie in die Tabelle ein und stellt sie dem Modell.

| # | Frage | Antwort korrekt? (ja/teils/nein) | Was war falsch? |
|---|-------|----------------------------------|-----------------|
| 1 | Wofür wird der Befehl chmod verwendet? | teils | Behauptung: chmod 755 stelle sicher, dass "nur der Benutzer lesbar ist" und nur der Entwickler die Datei lesen kann.Die Realität: Das Gegenteil ist der Fall. Man müsste chmod 600 oder chmod 700 verwenden |
| 2 | Was ist der Unterschied zwischen einem absoluten und einem relativen Pfad? | teils | Das Beispiel ./data/my_file.py wird fälschlicherweise als absoluter Pfad benannt. Das ist nicht korrekt. Der Punkt am Anfang steht für das aktuelle Verzeichnis, was diesen Pfad zu einem relativen Pfad macht |
| 3 | Wofür wird das Verzeichnis /etc verwendet? | Großteils falsch | /etc = nur Konfigurationsdateien		Kernel: in /boot, nicht in /etc		Programme: in /bin, /usr/bin, nicht in /etc		Bibliotheken: in /lib, /usr/lib		Treiber: in /lib/module		Datenbank-Programme: nicht in /etc, nur Konfiguration dort	Datenbanken: meist in /var/lib|
| 4 | Was macht der Befehl grep? | Ja | - |
| 5 | Was ist der Unterschied zwischen einem Hard Link und einem Symbolic Link? | nein | Ein Symlink ist keine Kopie, er "springt" nicht automatisch auf einen neuen Pfad, wenn man die Datei verschiebt, "erstellt eine eindeutige Kopie... die Datei selbst wird nur einmal gespeichert". Das widerspricht sich.|

**B.2** Wie viele der 5 Antworten waren vollständig korrekt? 1 / 5

---

## Teil C – Wissensbasis erstellen

**C.1** Erstellt pro Thema eine Markdown-Datei (`.md`). Nutzt die Vorlage aus
`material/wissensbasis-vorlagen/` für eure Domäne als Startpunkt.

Achtet auf gute Struktur (siehe Checkliste in `docs/04_rag-erklaert.md`):
- klare Überschriften
- kurze Absätze
- Befehle/Code in Codeblöcken
- häufige Fehler benennen

**C.2** Welche Dateien habt ihr erstellt?

| Dateiname                                | Inhalt (Stichworte)                  |
| ---------------------------------------- | ------------------------------------ |
| absolute und relative pfade erklärung.md | Pfade, Verzeichnisse, Navigation     |
| chmod_erklärung.md                       | Rechte ändern, chmod, Berechtigungen |
| dateirechte.md                           | rwx-Rechte, Besitzer, Gruppen        |
| etc verzeichnis erklärung.md             | `/etc`, Konfiguration, Systemdateien |
| grep erklärung.md                        | Textsuche, Muster, Optionen          |
| hard link und symbolic link erklärung.md | Hard Links, Symlinks, Verknüpfungen  |
| linux_wissen_ubuntu_arch.md              | Ubuntu, Arch, Unterschiede           |
| linux-grundlagen.md                      | Linux-Aufbau, Grundlagen, Befehle    |
| shell-befehle.md                         | Terminal, Shell, wichtige Befehle    |


**C.3 System-Prompt setzen.** Legt in Open WebUI ein eigenes Modell an:
`Workspace → Models → + Create Model`, basierend auf `gemma3:1b`, mit einem
System-Prompt, der die Rolle festlegt (Vorlage in den Wissensbasis-Vorlagen).

Euer System-Prompt (Kurzfassung notieren):

_________________________________________________________________

---

## Teil D – NACHHER: Modell mit Wissensbasis

**D.1** Ladet eure Dokumente hoch
(`Workspace → Knowledge → + Create Knowledge`) und ordnet sie eurem Modell zu
(`Workspace → Models → (euer Modell) → Knowledge`).

**D.2** Stellt **dieselben 5 Fragen** aus Teil B erneut.

| # | Antwort jetzt korrekt? (ja/teils/nein) | Besser als vorher? |
|---|----------------------------------------|--------------------|
| 1 | Wofür wird der Befehl chmod verwendet? | Ja | Ja
| 2 | Was ist der Unterschied zwischen einem absoluten und einem relativen Pfad? | Ja | Ja
| 3 | Wofür wird das Verzeichnis /etc verwendet? | Ja | Ja
| 4 | Was macht der Befehl grep? | Ja | Ja
| 5 | Was ist der Unterschied zwischen einem Hard Link und einem Symbolic Link? | Fast | Ja, aber 1 fehler

**D.3** Wie viele sind **jetzt** korrekt? 5 / 5  (vorher: 1 / 5)

**D.4** Beschreibt den deutlichsten Unterschied, den ihr beobachtet habt:

Die antworten sind allgemein korrekt, wenn es um trainiertes Wissen geht. Wenn es um spezifische Fragen geht, die in der Wissensbasis stehen, ist das Modell in der Lage, diese korrekt zu beantworten. Die Antworten sind leicht präziser und enthalten mehr Details.

---

## Teil E – Verbessern

**E.1** Wählt eine Frage, die noch nicht gut beantwortet wird. Verbessert das
zugehörige Dokument (mehr Details, klarere Struktur). Lade es neu hoch und teste
erneut. Was hat sich geändert?

Die frage "Was ist der Unterschied zwischen einem Hard Link und einem Symbolic Link?" wird nun korrekt beantwortet

---

✅ **Geschafft, wenn:** Ihr den Vorher/Nachher-Vergleich vollständig ausgefüllt
habt und eure Wissensbasis im RAG aktiv ist.
