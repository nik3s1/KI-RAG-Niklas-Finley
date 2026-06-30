# Arbeitsblatt 1 – KI-Grundlagen & erster Kontakt

**Gruppe:** Niklas/Finley  **Domäne:** Linux
**Datum:** 23.6.2026

> **Ziel:** Du verstehst, wie ein Sprachmodell grundsätzlich funktioniert, und
> hast die lokale KI zum ersten Mal selbst ausprobiert.
> **Hintergrund:** `docs/02_ki-grundlagen.md`


## Teil 1 – Theorie (mit Hilfe der Hintergrund-Doku)

**1.1** Erkläre in einem Satz, was ein LLM bei jeder Eingabe eigentlich tut.

-> Ein LLM sagt bei jedem Schritt das wahrscheinlichste nächste Token voraus.

**1.2** Was ist ein **Token**? Gib ein Beispiel.

-> Ein Token ist eine Texteinheit, die ein Wort, Wortteil oder Zeichen sein kann. Beispiel: „Programmierung" kann in mehrere Tokens zerlegt werden.

**1.3** Das Modell „weiß" nichts, es rechnet mit Warscheinlichkeiten.
Deshalb kann es Antworten geben, die plausibel klingen, aber falsch sind.
Dieses Phänomen heißt Halluzination.

**1.4** Was bedeutet **nicht-deterministisch**? Nenne den Unterschied zu einer
C#-Methode, die ihr im Unterricht geschrieben habt.

Nicht-deterministisch bedeutet, dass bei gleicher Eingabe unterschiedliche Antworten entstehen können. Eine normale C#-Methode liefert bei gleichen Eingaben normalerweise immer das gleiche Ergebnis.

**1.5** Ordne zu, was die **Temperatur** bewirkt:

- niedrige Temperatur (0–0.3): eher vorhersehbare und konsistente Antworten
- hohe Temperatur (0.8–1.5): unvorhersehbare und unterschiedlichere Antworten


## Teil 2 – Erster Kontakt mit der lokalen KI

> Voraussetzung: Open WebUI läuft, Modell `gemma3:1b` ist ausgewählt
> (siehe Arbeitsblatt 2, falls noch nicht installiert).

**2.1 Halluzination provozieren.** Stelle dem Modell eine sehr spezifische
Frage aus deiner Domäne, deren Antwort du selbst kennst. Notiere:

- Deine Frage: Wie heißt der Netzwerkdrucker im Raum B214 unserer Schule?
- War die Antwort korrekt? ☐ ja ☐ teilweise x nein
- Was war falsch oder erfunden? Der Netzwerkdrucker im Raum B214 Ihrer Schule heißt HP LaserJet ProDM II 766YW.

**2.2 Gleiche Frage zweimal.** Stelle dieselbe Frage zweimal in zwei neuen
Chats. Sind die Antworten identisch?

☐ identisch x leicht unterschiedlich ☐ stark unterschiedlich

Was sagt das über das Verhalten des Modells aus? 

Das Modell arbeitet nicht-deterministisch und kann verschiedene Antworten erzeugen.

**2.3 Sprache testen.** Frage etwas auf Deutsch. Antwortet das Modell zuverlässig
auf Deutsch?  x ja ☐ nein – wechselt manchmal zu: __________________

**2.4 Grenzen des kleinen Modells.** `gemma3:1b` ist klein und schnell, aber
schwach. Notiere ein konkretes Beispiel, bei dem das Modell erkennbar an seine
Grenzen kommt:

Spezifisches wissen, wie z.B. die genaue Bezeichnung von niechen objekten, kann das Modell nicht zuverlässig liefern.

## Teil 3 – Mini-Reflexion

**3.1** Warum kann man sich auf die Antworten dieses Modells (ohne weitere
Hilfsmittel) bei Fachfragen **nicht** verlassen?

Man kann sich nicht vollständig auf die Antworten verlassen, weil das Modell Wahrscheinlichkeiten berechnet und Informationen erfinden kann.

**3.2** Formuliere eine Vermutung: Wie könnte man dem Modell beibringen, bei
*deiner* Domäne korrektere Antworten zu geben? (Das ist das Thema von Tag 2.)

Man könnte das Modell mit Daten aus unserer Linuxbasierten Domäne trainieren oder ihm relevantes Fachwissen über eine Wissensdatenbank bereitstellen.


✅ **Geschafft, wenn:** Du Teil 1 ausgefüllt hast und mindestens eine
Halluzination selbst provoziert und dokumentiert hast.
