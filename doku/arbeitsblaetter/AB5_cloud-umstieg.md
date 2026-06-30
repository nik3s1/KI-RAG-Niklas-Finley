# Arbeitsblatt 5 – Umstieg auf ein externes (Cloud-)LLM  ⭐ OPTIONAL

**Gruppe:** Niklas/Finley **Domäne:** Linux

> **⭐ Zusatzaufgabe für schnelle Gruppen.** Nur bearbeiten, wenn euer RAG-System
> läuft, getestet und dokumentiert ist (AB1–AB4 fertig).
>
> **Ziel:** Ihr bindet ein schnelles Cloud-LLM (z. B. Groq) an, vergleicht es mit
> dem lokalen Modell und bewertet Vor- und Nachteile – auch beim Datenschutz.
> **Hintergrund:** `docs/05_troubleshooting.md` (Abschnitt 5)

---

## Teil A – Warum überhaupt umsteigen?

**A.1** Wie lange dauert eine typische Antwort mit dem lokalen `gemma3:1b`?

ca. 0.5 Sekunden

**A.2** Was ist der vermutete Grund für die Geschwindigkeit lokaler Modelle ohne
Grafikkarte?

Weniger TOPS, heißt weniger Rechenleistung, daher langsamer.

## Teil B – Cloud-LLM anbinden

> Den API-Key stellt die Lehrkraft bereit (oder ihr legt selbst einen
> kostenlosen Groq-Account an: console.groq.com).

**B.1** Tragt den externen Anbieter in Open WebUI ein:
`Admin Panel → Settings → Connections → OpenAI API`

- Base URL: `https://api.groq.com/openai/v1`
- API-Key: (von der Lehrkraft)

**B.2** Wählt ein Modell mit großem Kontextfenster:
`llama-3.1-8b-instant` (128k Token).

**B.3** Stellt eine eurer Domänen-Fragen. Antwortzeit jetzt?

ca. - Sekunden  (lokal war: 0.5 Sekunden)

---

## Teil C – Das „Request Entity Too Large"-Problem

Viele Gruppen stoßen jetzt auf diese Fehlermeldung.

**C.1** Was bedeutet sie? (Tipp: Token-Limit + RAG-Kontext)

Die anfrage an sich ist zu groß, weil das Modell nur eine bestimmte Anzahl an Token verarbeiten kann. Wenn die Anfrage (inklusive Kontext) dieses Limit überschreitet, kommt es zu dieser Fehlermeldung.

**C.2** Welche Lösung habt ihr angewandt? (mehrere möglich)

- [ ] Modell mit größerem Kontext gewählt
- [ ] Chunk Size reduziert (auf ______)
- [ ] Top-K reduziert (auf ______)
- [ ] Dokumente gekürzt

**C.3** Hat es funktioniert? ☐ ja ☐ nein – Beobachtung:
Die Cloud-KI haben wir nicht aktiv genutzt, sondern nur theorie gemacht, da es wegen der schon vorhandenen rechenleistung eher sinnlos war.

---

## Teil D – Vergleich & Bewertung

Füllt die Vergleichstabelle aus (eigene Einschätzung):

| Kriterium | Lokal (gemma3:1b) | Cloud (Groq) |
|-----------|-------------------|--------------|
| Geschwindigkeit | Sehr Schnell| Auch sehr schnell|
| Antwortqualität | Geht, liegt am wissen| Gute Antwort|
| Datenschutz | Hoher Schutz| Geringerer Schutz|
| Internet nötig? | Nein | Ja |
| Kosten | Kostenlos | Bezahlbar |

---

## Teil E – Datenschutz-Reflexion (wichtig!)

**E.1** Beim Cloud-LLM verlassen eure Eingaben den eigenen Rechner. Wohin gehen
die Daten ungefähr, und warum ist das relevant?

Bei Groq werden die Eingaben über das Internet an die Server gesendet und dort verarbeitet. Das ist relevant, weil dabei sensible oder vertrauliche Daten den eigenen Rechner verlassen und Datenschutz- sowie Unternehmensrichtlinien beachtet werden müssen.

**E.2** Nennt ein Beispiel aus dem IT-Berufsalltag, bei dem man **auf keinen
Fall** ein Cloud-LLM nutzen sollte:

Quellcode eines nicht veröffentlichten Projekts, Kundendaten, Passwörter oder interne Konfigurationsdateien.

**E.3** Wann ist umgekehrt ein lokales Modell die bessere Wahl, obwohl es
langsamer ist?

Ein lokales Modell ist die bessere Wahl, wenn sensible Daten verarbeitet werden oder keine Internetverbindung verfügbar ist. An sich ist die Leistung ein geringes Problem und es bleiben die Daten auf dem eigenen Rechner.

---

✅ **Geschafft, wenn:** Das Cloud-LLM antwortet, das „Too Large"-Problem gelöst
ist und eure Vergleichstabelle + Datenschutz-Reflexion ausgefüllt sind.
