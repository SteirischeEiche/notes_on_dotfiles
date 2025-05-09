Kapitel_1_und_2.md

## Einleitung
- Das erste Zeichen der Ausgabe von `ls -l` gibt an, um was es sich handelt (z.B. "d" für Ordner oder "-" für Datei)
- Cmd+K = Strg+L unter Linux
- In `DS_Store` werden Finder-Einstellungen gespeichert
- Die obere Leiste des Mac-Terminals zeigt den aktuellen Prozess an (kann auch mit `echo $0` angezeigt werden)

### `echo`
- `echo` sendet die (eingetippte) Eingabe an die Ausgabe
- `echo $name`: `echo` sucht nach der Variable "name"

### Was bringen Dotfiles?
- Apple ändert die Namen von Einstellungen mit neuen Updates
- Mit Dotfiles (und einem Skript) können wir einen neuen Computer automatisch einrichten
- Mit Git können werden Änderungen an den Dotfiles über die Zeit verfolgt
- Programme legen ständig Dotfiles im Home-Verzeichnis an (lösche von Zeit zu Zeit die, die du nicht mehr brauchen)

### Unser 1. Dotfile: `zshrc`
- Das `rc` in `zshrc` steht für „run commands“: diese Befehle werden ausgeführt, wenn `zsh` startet
- `rc`-Dateien sind praktisch Skripte
- `source` lädt eine Datei neu

### Subshells
- Benutze `zsh`, um eine Subshell zu starten (ein neuer ZSH-Prozess innerhalb des alten Prozesses)
- `echo $SHLVL`: Shell-Ebene anzeigen
- `exit` beendet den Prozess, dadurch wird zB `zsh_history` aktualisiert

### `which`...
- Zeigt an, wo (und ob) Befehle (Programme) installiert sind
- Zeigt Aliase an
- Zeigt ZSH-Funktionen

### Prompt einstellen
- Mit `echo $PROMPT` kannst du den Prompt anzeigen lassen
- Den Output kannst du dann kopieren, in deine `zshrc` einfügen und nach Belieben ändern
- `%` ist das (Standard-)Prompt-Symbol: es zeigt an: Hier kannst du etwas eingeben