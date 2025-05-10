## Git & Symlinks

### Wozu brauchen wir Git?
- Wir wollen nicht nur die letzte Version unserer Dotfiles sichern, sondern auch Schnappschüsse aller unserer Änderungen

### Command Line Developer Tools
- Unter macOS braucht man die Command Line Developer Tools, um Git zu benutzen.
- Diese können mit `xcode-select --install` installiert werden

### Git einstellen
- `git confic` ist ein Beispiel für einen Subbefehl
- Wir ändern hier die globalen Einstellungen ( man kann auch projektspezifische Einstellungen vornehmen)
- Die Einstellungen werden in der `gitconfig` gespeichert
- Man kann auf GitHub eine private E-Mail-Adresse (einen Alias) einrichten
- Man sollte 2FA für GitHub einrichten

### SSH einrichten
- Mit SSH müssen wir nicht jedes Mal unser Passwort eingeben, wenn wir Code pushen
- Zuerst müssen wir lokal SSH-Schlüssel erzeugen (folge der Anleitung auf github.com)
- Speichere die Schlüssel im Standardspeicherort

#### SSH-Agent einrichten
- __Wichtig: Github empfiehlt den auf macOS vorinstallierten SSH-Agent zu verwenden, nichts von z.B. Homebrew__
- Zuerst die für den Agenten notwendigen Umgebungsvariablen setzen
- Dann einige Einstellungen vornehmen (in der SSH-Konfigurationsdatei)
- __Achtung: Github empfiehlt das Speichern der Passphrase in Apple Keychain. Ich habe das `--apple-use-keychain` weggelassen und die Passphrase stattdessen in KeePassXC gespeichert.__

#### Verbindung zu GitHub einrichten
- Den öffentlichen Schlüssel auf github.com eingeben
- Die Verbindung getestet und den Fingerabdruck mit github.com verglichen
- Tipp: Du kannst Signaturen/Fingerabdrücke (die z.B. die Shell ausgibt) mit Strg+F auf der entsprechenden Webseite vergleichen
- Durch den Test wird die Datei `kown_hosts` erstellt. Die IP-Adressen unserer SSH-Verbindungen landen dort.

### GitHub Repo erstellt
- Nach der Erstellung haben wir das Remote-Repo geklont
- D.h. alles es wird alles kopiert und eine permanente Kommunikation eingerichtet
- Für das Klonen haben wir SSH verwendet
- Gits Magie findet im `git`-Ordner statt; dort werden u.a. die Snapshots unseres Codes gespeichert
- Regelmäßig `git status` eingeben und die Hinweise lesen
- Eine Datei muss im Repo sein, damit Git sie verfolgen kann, aber `zshrc` muss in `~` sein, die Lösung...

### Symlinks
- Mit Symlinks kann man Kopien von Dateien an verschiedenen Orten haben; ein Link zeigt auf das Original
- Symlinks = symbolische Links, das Gegenteil sind Hardlinks
- Der Name der Originaldatei und des Symlinks müssen nicht übereinstimmen
- Verwende beim Erstellen von Symlinks absolute Pfade, sonst kann es zu Problemen kommen
- Man kann das Symlinken automatisieren mit...

## Dotbot
- Dotbot muss nicht wie andere Programme installiert werden
- Wir fügen Dotbot als Submodul zu unserem Repo hinzu (gemäß der offiziellen Anleitung)

### Dotbot einstellen
- Mit Directives kannst du festlegen, was passieren soll, wenn Dotbot ausgeführt wird
- Die Directives stehen in der `.yaml`-Datei

#### Was die Directives machen
- `link`: Dotbot erstellt Symlinks
- `create`: Leere Verzeichnisse werden erstellt
- `shell`: Befehle, die ausgeführt werden, wenn Dotbot läuft (z.B. um die Standard-Shell zu ändern)
- `clean`: Löscht automatisch tote (ins Leere zeigende) Symlinks
- `defaults`: Globale Voreinstellungen für andere Directives (um Wiederholungen zu vermeiden)
