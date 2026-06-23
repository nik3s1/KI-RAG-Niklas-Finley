# Arbeitsblatt 2 – Installation der lokalen KI-Umgebung

**Gruppe:** Niklas/Finley **Domäne:** Linux

> **Ziel:** Ihr habt Docker, Ollama und Open WebUI eingerichtet und das Modell
> `gemma3:1b` läuft.
> **Hintergrund:** `docs/03_installation.md` · Bei Fehlern: `docs/05_troubleshooting.md`

---

## Architektur – was läuft wo?

Trage ein, wo welche Komponente läuft (im Container / direkt auf dem PC):

| Komponente | läuft … | Port |
|------------|---------|------|
| Open WebUI | __________________ | ______ |
| Ollama | __________________ | ______ |
| gemma3:1b | (im Modell-Speicher von Ollama) | – |

---

## Checkliste Installation

Hake ab, sobald ein Schritt erledigt und geprüft ist.

- [x] **Docker Desktop** läuft (`docker --version` zeigt eine Version)
- [x] **Ollama installiert** (`ollama --version`)
- [x] **Umgebungsvariable** `OLLAMA_HOST = 0.0.0.0` gesetzt
- [x] **Modell geladen** (`ollama pull gemma3:1b`)
- [x] **Compose-Datei** im Projektordner
- [x] **Container gestartet** (`docker compose up -d`)
- [x] **WebUI erreichbar** unter `http://localhost:3000`
- [x] **Account angelegt** (lokal)
- [x] **Modell `gemma3:1b`** in der Auswahl sichtbar
- [x] **Erste Antwort** erhalten

---

## Prüf-Befehle (Ergebnis notieren)

**Ollama läuft?**
```bash
curl http://localhost:11434
```
Ausgabe: 
StatusCode        : 200
StatusDescription : OK
Content           : Ollama is running
RawContent        : HTTP/1.1 200 OK
                    Content-Length: 17
                    Content-Type: text/plain; charset=utf-8
                    Date: Tue, 23 Jun 2026 08:14:00 GMT

                    Ollama is running
Forms             : {}
Headers           : {[Content-Length, 17], [Content-Type, text/plain; charset=utf-8], [Date, Tue, 23 Jun 2026 08:14:00
                    GMT]}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 17

**Welche Modelle sind installiert?**
```bash
curl http://localhost:11434/api/tags
```
Gefundene Modelle: 
StatusCode        : 200
StatusDescription : OK
Content           : {"models":[{"name":"gemma3:1b","model":"gemma3:1b","modified_at":"2026-06-23T09:42:18.0014364+02:00
                    ","size":815319791,"digest":"8648f39daa8fbf5b18c7b4e6a8fb4990c692751d49917417b8842ca5758e7ffc","det
                    ai...
RawContent        : HTTP/1.1 200 OK
                    Content-Length: 369
                    Content-Type: application/json; charset=utf-8
                    Date: Tue, 23 Jun 2026 08:14:37 GMT

                    {"models":[{"name":"gemma3:1b","model":"gemma3:1b","modified_at":"2026-06-23...
Forms             : {}
Headers           : {[Content-Length, 369], [Content-Type, application/json; charset=utf-8], [Date, Tue, 23 Jun 2026
                    08:14:37 GMT]}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 369


---

## Fehler-Protokoll

Notiert **jedes** Problem und wie ihr es gelöst habt – das ist später Teil eurer
Dokumentation und hilft anderen Gruppen!

| Problem | Lösung | gelöst? |
|---------|--------|---------|
| Erst gab es Probleme mit der WebUI | Port Geändert | x |
| | | ☐ |
| | | ☐ |

> **Tipp:** Die drei häufigsten Fehler sind: (1) WebUI findet kein Modell →
> `host.docker.internal` statt `localhost`; (2) `OLLAMA_HOST` nicht gesetzt;
> (3) Firewall blockiert Port 11434. Alle Lösungen in `docs/05_troubleshooting.md`.

---

✅ **Geschafft, wenn:** Das Modell `gemma3:1b` in Open WebUI antwortet und euer
Fehler-Protokoll ausgefüllt ist.
