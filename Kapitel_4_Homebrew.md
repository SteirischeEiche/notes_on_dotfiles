- Homebrew bietet neuere Software als Apple
- `/opt/homebrew/` ist nicht standardmäßig im Pfad enthalten
- Daher müssen wir die Shell-Umgebung anpassen

---

- Homebrew-Pakete haben Vorrang vor Vorinstallierten
- __Umgebungsvariablen__ sind wie Zettel, die an Schränken kleben und auf denen steht, was in den Schränken ist
- Homebrew kann nur eine Version eines Programms installieren
- MacPorts braucht `sudo` im Gegensatz zu Homebrew

## Homebrew Nomenklatur 2.0
- Formulae sind Ruby-Skripte, die Pakete installieren
- Ein Tab (Register) ist ein Repo, das Formeln enthält
- Ein Keg (Fass) ist ein Ordner auf deinem Computer, in dem ein Paket gespeichert ist
- Wenn ein Programm "keg-only" installiert wird, wird kein Symlink zu `opt/homebrew/` erstellt
- Keg-only-Pakete sind normalerweise Abhängigkeiten
- Eine Bottle ist ein vorkompiliertes Programm (binary)
- Die Installation ist schneller
- Der Cellar ist der Ordner, in dem die Homebrew-Pakete gelagert (gespeichert) werden

---

- Du kannst Homebrew nicht installieren, wenn dein Benutzer kein (ein leeres) Passwort hat
- Das Homebrew-Installationsskript installiert `xcode-select`, wenn du es noch nicht hast

## Füge `/opt/homebrew/` zum Pfad hinzu
- `$PATH` ist eine Shell-Umgebungsvariable
- Der Befehl `shell eval` führt die Befehle aus, die er in der Datei `shellenv` unter `/opt/homebrew/bin/brew/` findet

## Unterschiede zwischen ZSH-Konfigurationsdateien
### Arten von Shell-Sessions (Sitzungen)
- Wenn du die Terminal- App öffnest, ist das eine _interaktive_ _login_ Shell- Session
- Wenn du dann eine Subshell startest, ist das eine _interaktive_ _non-login_ Shell
- Und wenn du ein Shell-Skript ausführst, ist es eine _nicht-interaktive_ _non-login_ Shell

![ZSH-Konfigurationsdateien](https://mac.install.guide/assets/images/terminal/zsh-configuration.png)

### ZSH-Konfigurationsdateien
- `zshenv` wird für _alle_ Arten von Shell-Sitzungen ausgelesen (allerdings überschreibt macOS Umgebungsvariablen für interaktive Shells, s. unten)
- `zprofile` wird für alle _Login-Shells_ geladen
- Subshells erben die Einstellungen von `zprofile`, aber die Datei wird nicht erneut gesourct
- `zshrc` wird _nur_ für interaktive Shell-Sitzungen geladen

### Beste Verwendung für jede Konfigurationsdatei
- Von `zshenv` besser die Finger lassen
- Wenn du Shell-Skripte schreibst: Setze Umgebungsvariablen in dem Skript und nicht in `zshenv`

#### `zprofile`
- Setze hier die Umgebungsvariablen `$PATH` und `$EDITOR`
- Z.B. wird empfohlen, die Hombrew-Ordner hier zum Pfad hinzuzufügen
- macOS führt `path-helper` (zu finden in `/etc/zprofile/`) aus, bevor `zprofile` geladen wird
- Dadurch werden Umgebungsvariablen überschrieben
- Deshalb setzt man z.B. den Pfad in `zprofile` und nicht in `zshenv`, damit er nicht überschrieben wird

#### `zshrc`
- Hier sollten z.B. Aliase erstellt und der Prompt konfiguriert werden
- Man könnte `$PATH` auch hier setzen
- Es ist jedoch Konvention, `zshrc` nur zu benutzen, um das Aussehen der Shell einzustellen
