- Homebrew bietet neuere Software als Apple
- `/opt/homebrew/` ist nicht standardmäßig im Pfad enthalten
- Daher müssen wir die Shell-Umgebung anpassen

- Homebrew-Pakete haben Vorrang vor Vorinstallierten

- Umgebungsvariablen sind wie Zettel, die an Schränken kleben und auf denen steht, was in den Schränken ist

- Homebrew kann nur eine Version eines Programms installieren

- MacPorts braucht `sudo` im Gegensatz zu Homebrew

## Homebrew Nomenklatur 2.0
- Formulae sind Ruby-Skripte, die Pakete installieren
- Ein Tab (Register) ist ein Repo, das Formeln enthält
- Ein Keg (Fass) ist ein Ordner auf deinem Computer, in dem ein Paket gespeichert ist
- Wenn ein Programm "keg-only" installiert wird, wird kein Symlink zu `opt/homebrew/` erstellt
- Keg-only-Pakete sind normalerweise Abhängigkeiten
