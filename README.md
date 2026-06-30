# Linux-RAG mit Open WebUI und Ollama

## Projektbeschreibung

Dieses Projekt demonstriert den Aufbau eines einfachen **Retrieval-Augmented Generation (RAG)**-Systems für die Domäne **Linux**. Als Sprachmodell wird `gemma3:1b` über **Ollama** verwendet. Die Benutzeroberfläche wird durch **Open WebUI** bereitgestellt.

Ziel des Projekts ist es, zu zeigen, wie sich die Qualität von KI-Antworten durch eine eigene Wissensbasis verbessern lässt und welche Grenzen ein RAG-System besitzt.

---

## Projektziele

* Lokale KI ohne Cloud-Dienste betreiben
* Eigene Linux-Wissensbasis erstellen
* RAG (Retrieval-Augmented Generation) praktisch einsetzen
* Unterschiede zwischen Antworten mit und ohne Wissensbasis untersuchen
* Grenzen und Risiken von KI-Systemen kennenlernen

---

## Verwendete Technologien

* Docker Desktop
* Ollama
* Open WebUI
* Gemma 3 (1B)
* Markdown (`.md`) als Wissensbasis

---

## Projektstruktur

```text
.
├── docker-compose.yml
├── README.md
└── wissensbasis/
    ├── linux-grundlagen.md
    ├── dateirechte.md
    ├── shell-befehle.md
    ├── chmod_erklärung.md
    ├── grep_erklärung.md
    ├── absolute_und_relative_pfade.md
    ├── etc_verzeichnis.md
    └── hardlink_symboliclink.md
```

---

## Installation

### Voraussetzungen

* Docker Desktop
* Ollama
* Modell `gemma3:1b`

Modell herunterladen:

```bash
ollama pull gemma3:1b
```

Container starten:

```bash
docker compose up -d
```

Open WebUI anschließend im Browser öffnen:

```
http://localhost:3000
```

---

## Wissensbasis

Die Wissensbasis besteht aus mehreren Markdown-Dateien zu Linux-Themen, darunter:

* Linux-Grundlagen
* Dateirechte
* `chmod`
* `grep`
* Shell-Befehle
* `/etc`-Verzeichnis
* Absolute und relative Pfade
* Hard Links und Symbolic Links

Diese Dokumente werden in Open WebUI als **Knowledge Base** importiert und dem Modell zugewiesen.

---

## System Prompt

Für das Modell wird ein System Prompt verwendet, der es als Linux-Tutor definiert. Das Modell beantwortet Fragen anhand der bereitgestellten Wissensbasis und weist darauf hin, wenn Informationen fehlen.

---

## Tests

Im Rahmen des Projekts wurden verschiedene Tests durchgeführt:

* Vergleich von Antworten mit und ohne RAG
* Test der Antwortqualität bei Linux-Fachfragen
* Manipulation der Wissensbasis zur Untersuchung der Vertrauenswürdigkeit eines RAG-Systems
* Analyse der Grenzen kleiner Sprachmodelle

---

## Erkenntnisse

* RAG verbessert die Qualität domänenspezifischer Antworten deutlich.
* Die Qualität der Antworten hängt direkt von der Qualität der Wissensbasis ab.
* Fehlerhafte oder manipulierte Dokumente können zu falschen Antworten führen.
* Kleine Modelle wie `gemma3:1b` sind schnell und ressourcenschonend, stoßen jedoch bei komplexeren Aufgaben an ihre Grenzen.

---

## Lizenz

Dieses Projekt wurde zu Lern- und Ausbildungszwecken erstellt.
