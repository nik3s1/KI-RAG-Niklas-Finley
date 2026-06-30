# Comprehensive Linux Knowledge Base: Ubuntu & Arch Linux

Ein Leitfaden für das Schulprojekt zur Erstellung einer Wissensbasis (RAG) mit Open WebUI und Ollama. Dieses Dokument deckt die Grundlagen, Kernunterschiede und wichtigsten Befehle von Ubuntu (Debian-basiert) und Arch Linux ab.

---

## 1. Die Philosophie: Ubuntu vs. Arch Linux

Bevor man die Befehle lernt, muss man verstehen, warum es beide Welten gibt:

| Kriterium | Ubuntu | Arch Linux |
| :--- | :--- | :--- |
| **Zielgruppe** | Einsteiger, Entwickler, Server-Admins (Fokus auf Stabilität und "Out of the Box"-Nutzererfahrung) | Fortgeschrittene, Bastler (Fokus auf Minimalismus, volle Kontrolle und "Do It Yourself") |
| **Release-Modell** | **Point Release**: Feste Versionen (z.B. alle 6 Monate, LTS-Versionen alle 2 Jahre). Software wird über Jahre stabil gehalten. | **Rolling Release**: Keine festen Versionen. Einmal installiert, bleibt das System durch tägliche Updates immer absolut brandneu. |
| **Installation** | Grafischer Installer (Ubiquity/Calamares), in 15 Minuten einsatzbereit. | Standardmäßig textbasiert über die Kommandozeile (`archinstall` oder manuell), jeder Baustein wird selbst gewählt. |
| **Init-System** | systemd | systemd |

---

## 2. Die Paketmanager: Software installieren und verwalten

Der größte Unterschied im Alltag ist die Art und Weise, wie Software installiert wird.

### Ubuntu: APT (Advanced Package Tool) & Snap
Ubuntu nutzt das `.deb`-Format und greift standardmäßig auf offizielle, von Canonical geprüfte Repositories zurück.

* **Paketquellen aktualisieren:**
    ```bash
    sudo apt update
    ```
* **System aktualisieren (alle Pakete upgraden):**
    ```bash
    sudo apt upgrade -y
    ```
* **Software installieren:**
    ```bash
    sudo apt install <paketname>
    # Beispiel für Docker:
    sudo apt install docker.io docker-compose
    ```
* **Software entfernen:**
    ```bash
    sudo apt remove <paketname>
    # Komplett inklusive Konfigurationsdateien löschen:
    sudo apt purge <paketname>
    ```

### Arch Linux: Pacman & AUR (Arch User Repository)
Arch nutzt das hocheffiziente `.pkg.tar.zst`-Format. Zusätzlich gibt es das **AUR**, eine riesige Community-Datenbank, in der fast jede existierende Linux-Software zu finden ist.

* **Paketquellen aktualisieren & System upgraden (In einem Befehl!):**
    ```bash
    sudo pacman -Syu
    ```
* **Software installieren:**
    ```bash
    sudo pacman -S <paketname>
    ```
* **Software entfernen (inklusive nicht mehr benötigter Abhängigkeiten):**
    ```bash
    sudo pacman -Rs <paketname>
    ```
* **Nach einem Paket in den Quellen suchen:**
    ```bash
    pacman -Ss <suchbegriff>
    ```
* **Das AUR nutzen (mit einem AUR-Helper wie `yay`):**
    ```bash
    # Installation aus dem AUR (erfordert kein sudo beim Aufruf!)
    yay -S <paketname-aus-aur>
    ```

---

## 3. Systemverwaltung mit Systemd

Sowohl Ubuntu als auch Arch nutzen **systemd** zur Verwaltung von Hintergrunddiensten (Services), wie z.B. Docker oder SSH. Die Befehle sind auf beiden Systemen absolut identisch.

* **Einen Dienst sofort starten:**
    ```bash
    sudo systemctl start docker
    ```
* **Einen Dienst stoppen:**
    ```bash
    sudo systemctl stop docker
    ```
* **Einen Dienst beim Systemstart automatisch aktivieren:**
    ```bash
    sudo systemctl enable docker
    ```
* **Einen Dienst aus dem Systemstart entfernen:**
    ```bash
    sudo systemctl disable docker
    ```
* **Den Status eines Dienstes prüfen (Läuft er? Gibt es Fehler?):**
    ```bash
    sudo systemctl status docker
    ```
* **Die Log-Einträge eines Dienstes live einsehen:**
    ```bash
    sudo journalctl -u docker -f
    ```

---

## 4. Wichtige Netzwerk-Befehle (CLI)

Wenn du im Terminal die IP-Adresse prüfen oder Verbindungen testen musst:

* **IP-Adresse und Netzwerk-Schnittstellen anzeigen:**
    ```bash
    ip a
    # oder kompakter:
    ip -c a
    ```
* **Prüfen, ob ein Server/PC erreichbar ist (Ping):**
    ```bash
    ping -c 4 google.com
    ```
* **Offene Ports und aktive Verbindungen anzeigen (sehr nützlich für Docker-Troubleshooting):**
    ```bash
    sudo ss -tulpn
    ```
* **Die eigene öffentliche IP-Adresse herausfinden:**
    ```bash
    curl ifconfig.me
    ```

---

## 5. Spickzettel: Die universelle Linux-Verzeichnisstruktur

Egal ob Ubuntu oder Arch – die Ordnerstruktur folgt dem FHS (Filesystem Hierarchy Standard):

* `/` - **Root**: Die Wurzel des gesamten Systems. Alles beginnt hier.
* `/home/` - **Home-Verzeichnis**: Hier liegen die privaten Daten der Nutzer (z.B. `/home/linux/Documents`).
* `/etc/` - **Etcetera**: Hier befinden sich fast alle systemweiten **Konfigurationsdateien** (z.B. Netzwerk, SSH, User-Rechte).
* `/var/log/` - **Variable Data**: Der wichtigste Ort für **Fehlersuche**, da hier alle System-Logs liegen.
* `/opt/` - **Optional**: Hier wird oft manuell installierte Software von Drittanbietern abgelegt.
* `/mnt/` oder `/media/` - **Mount**: Hier werden USB-Sticks oder externe Festplatten eingehängt.

---

## 6. Typische Terminal-Tricks für den Schulunterricht

* **Die Befehlshistorie durchsuchen:** Drücke `STRG + R` und tippe Teile eines alten Befehls ein (z.B. `docker`), um ihn sofort wiederzufinden.
* **Ausgabe in eine Datei umleiten (Log erstellen):**
    ```bash
    ip a > netzwerk_info.txt
    ```
* **Einen Befehl als Endlosschleife alle 2 Sekunden ausführen (z.B. zur Statusüberwachung):**
    ```bash
    watch systemctl status docker
    ```
