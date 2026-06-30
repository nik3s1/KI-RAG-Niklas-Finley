# Arbeitsblatt 4 – Grenzen der KI testen

**Gruppe:** ____________________  **Domäne:** ____________________

> **Ziel:** Ihr findet heraus, dass eine KI nur so gut ist wie ihre Wissensbasis
> – und entwickelt ein kritisches Auge für KI-Antworten.
> **Leitgedanke:** Wer die Grenzen einer Technik kennt, kann sie verantwortungsvoll
> einsetzen.

---

## Teil A – "KI kaputt machen" (Falsch-Info-Experiment)

> Ihr manipuliert hier **absichtlich** eure Wissensbasis, um das Verhalten zu
> beobachten. **Macht vorher eine Kopie eurer korrekten Dokumente!**

**A.1** Ändert in einem Dokument bewusst eine Tatsache ins Falsche - z. B. einen
Befehl, eine Zahl oder einen Fachbegriff. Was habt ihr gefälscht?

Wir haben in dateirechte.md den Befehl chmod 755 absichtlich zu chmod 999 geändert.

**A.2** Ladet das geänderte Dokument neu hoch und stellt die passende Frage.
Übernimmt die KI die falsche Information?

[x] ja, übernimmt sie   [ ] nein, antwortet trotzdem korrekt   [ ] teils

**A.3** Notiert die Antwort der KI (sinngemäß):

Die KI erklärte den absichtlich falschen Wert 999 als gültige Berechtigung und übernahm damit die fehlerhafte Information aus der Wissensbasis

**A.4** Was schließt ihr daraus über die Vertrauenswürdigkeit eines RAG-Systems?

Ein RAG-System überprüft die Informationen aus der Wissensbasis nicht automatisch auf Wahrheit. Es verwendet die bereitgestellten Daten. Deshalb müssen die Dokumente korrekt und vertrauenswürdig sein.
> **Nach dem Experiment:** Stellt eure korrekten Dokumente wieder her!

---

## Teil B - Optional (für schnelle Gruppen)

Wenn ihr Zeit habt, testet zusätzlich **eine** dieser Varianten:

- **Widerspruch:** Zwei Dokumente widersprechen sich. Welche Version "gewinnt"?
- **Lücke:** Frage zu einem Thema, das **nicht** in der Wissensbasis steht.
  Sagt die KI ehrlich "weiß ich nicht" - oder erfindet sie etwas?

Eure Beobachtung:

Bei wiederspruch ist es random und bei nachfrage nach einer lücke erfindet die KI eine Antwort, die plausibel klingt, aber nicht korrekt ist.

---

## Teil C - Kritische Reflexion (wichtig fürs Abnahmegespräch)

**C.1** Nennt **zwei** Situationen, in denen man einer KI-Antwort **nicht** blind
vertrauen sollte:

1. Bei sicherheitkonfigurationen wie Firewall-Regeln oder Benutzerrechten.
2. Bei medizinischen Diagnosen oder Behandlungen.

**C.2** Was bedeutet euer Ergebnis aus Teil A für den Einsatz von KI im
IT-Berufsalltag (z. B. bei Konfigurationen oder Code)?

Im IT-Berufsalltag muss man KI-Ergebnisse überprüfen. Eine falsche Konfiguration kann Sicherheitsprobleme oder Systemausfälle verursachen

**C.3** Formuliert eine Regel für euch selbst: "Bevor ich eine KI-Antwort
übernehme, ..."

Bevor ich eine KI-Antwort übernehme, überprüfe ich die Informationen anhand von Dokumentationen oder Tests.

---

[OK] **Geschafft, wenn:** Ihr Teil A durchgeführt, dokumentiert und eure korrekten
Dokumente wiederhergestellt habt.
