# Erklärung: Warum `mount -t tmpfs -o size=1G tmpfs /mnt/ramdisk` dir scheinbar "gratis RAM" gibt

Der Linux-Befehl

```bash
mount -t tmpfs -o size=1G tmpfs /mnt/ramdisk
```

erstellt eine **RAM-Disk** mithilfe des Dateisystems **tmpfs**.

## Erklärung des Befehls

- `mount` – bindet ein Dateisystem ein.
- `-t tmpfs` – verwendet das Dateisystem **tmpfs**, das Daten im Arbeitsspeicher speichert.
- `-o size=1G` – legt eine maximale Größe von 1 GB fest.
- `tmpfs` – Name des Dateisystems.
- `/mnt/ramdisk` – Verzeichnis, in das die RAM-Disk eingebunden wird.

> Hinweis: Das Verzeichnis `/mnt/ramdisk` muss vorher existieren, z. B. mit:
>
> ```bash
> sudo mkdir -p /mnt/ramdisk
> ```

## Warum wirkt es wie "gratis RAM"?

Es sieht so aus, als würde der Befehl zusätzlichen Arbeitsspeicher bereitstellen. Tatsächlich wird jedoch **kein neuer RAM erzeugt**. Stattdessen reserviert `tmpfs` einen Bereich des bereits vorhandenen Arbeitsspeichers und stellt ihn als Laufwerk zur Verfügung.

Dabei gilt:

- Es wird **kein zusätzlicher physischer RAM** hinzugefügt.
- `tmpfs` nutzt vorhandenen Arbeitsspeicher dynamisch.
- Ungenutzter Speicher wird nicht dauerhaft belegt.
- Bei Bedarf kann `tmpfs` – je nach Systemkonfiguration – auch Auslagerungsspeicher (Swap) verwenden.

## Vorteile

- Sehr hohe Lese- und Schreibgeschwindigkeit.
- Ideal für temporäre Dateien, Caches oder Build-Verzeichnisse.
- Weniger Schreibzugriffe auf SSDs.

## Nachteile

- Der verfügbare Arbeitsspeicher für andere Programme wird reduziert.
- Alle Daten gehen nach einem Neustart verloren.
- Eine zu große RAM-Disk kann die Systemleistung beeinträchtigen.

## Fazit

Der Befehl

```bash
mount -t tmpfs -o size=1G tmpfs /mnt/ramdisk
```

stellt **keinen kostenlosen oder zusätzlichen RAM** bereit. Er verwendet lediglich vorhandenen Arbeitsspeicher als besonders schnelles virtuelles Laufwerk. Der Begriff "gratis RAM" ist daher technisch nicht korrekt – tatsächlich wird vorhandener RAM nur anders genutzt.