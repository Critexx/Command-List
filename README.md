# Command-List

### Allgemeine Git Begriffe
|Begriff | Beschreibung|
|------------|------------|
|Arbeitsverzeichnis (Working Directory)			|Dies ist der Bereich, in dem du deine Dateien tatsächlich bearbeitest. Es zeigt den aktuellen Stand der Dateien auf meinem Dateisystem.|
|Staging-Bereich (Index)			|Dies ist ein Bereich, in dem du Änderungen vorbereitest, bevor sie in einem Commit gespeichert werden. Wenn du git add ausführst, verschiebst du Änderungen von deinem Arbeitsverzeichnis in den Staging-Bereich.|

### Bash commands
|Bash command | Beschreibung|
|-------------|------------|
|pwd					|aktueller Directory|
|cd "C:\Users\Critex\Documents\"	|Directory ändern|
|cd ..	|Directory Ebene down|
|cat ~/.ssh/id_rsa.pub		|Überprüfung ob schon ein SSH Key pair existiert|
|ssh-keygen -t rsa -C "your.email@example.com" -b 4096					|erstellt einen neuen SSH Key nach rsa Verfahren und 4096 bit Länge|
|ssh -T git@gitlab.com		|Überprüfung einer SSH-Verbindung auf ein gitlab repo|

### Git configuration
Sehr viele Devs haben genau dieses Setup:
|Configuration | git command| Beschreibung |
|------------|------------|------------|
|pull.rebase = true				|git config --global pull.rebase true      |Führt bei git pull automatisch ein Rebase statt Merge aus. Dadurch bleibt die Commit-Historie linear und es entstehen keine unnötigen Merge-Commits.|
|rebase.autoStash = true  |git config --global rebase.autoStash true |Wenn beim Rebase lokale (auch gestagte) Änderungen vorhanden sind, werden diese automatisch zwischengespeichert (stash), der Rebase ausgeführt und danach wiederhergestellt. Verhindert Fehler wie "cannot rebase: you have unstaged changes".|
|fetch.prune = true				|git config --global fetch.prune true      |Entfernt lokale Referenzen auf Remote-Branches, die auf dem Server bereits gelöscht wurden. Hält die Remote-Branch-Liste sauber.|

### Git Basic commands

| Befehl | Beschreibung |
|---|---|
| `git config --global user.name "<name>"` | Name des Benutzers einstellen (global über alle Projekte) |
| `git config --global user.email "<email>"` | E-Mail des Benutzers einstellen (global über alle Projekte) |
| `git config --global --list` | Listet alle globalen Konfigurationen auf |
| `git config --list` | Listet alle Konfigurationen auf, die im aktuellen Projekt gelten. Soll ein Projekt eine andere E-Mail verwenden, setzt man sie dort mit dem Befehl oben ohne `--global` |
| `git --version` | Zeigt die aktuelle Git-Version an |
| `git init` | Initialisiert ein lokales Repository. Erzeugt den Ordner `.git` |
| `git clone <url>` | Holt eine Kopie des Repositorys in einen Ordner mit dem Namen des Repos |
| `git clone <url> <ordner>` | Klont in einen Ordner mit eigenem Namen (relativ oder absolut) |
| `git clone <url> .` | Klont in den aktuellen Ordner (dieser muss leer sein) |
| `git status` | Zeigt den aktuellen Status an |
| `git add <datei>` | Staged eine veränderte oder neue Datei |
| `git add --all` | Staged alle Änderungen im ganzen Repo: neue, veränderte und gelöschte Dateien |
| `git add .` | Staged alle Änderungen im aktuellen Ordner und darunter |
| `git add docs/*.txt` | Staged alle txt-Dateien im Ordner `docs` |
| `git add docs/` | Staged alle Dateien im Ordner `docs` |
| `git add -u` | Staged nur Änderungen und Löschungen von bereits getrackten Dateien, keine neuen Dateien |
| `git commit -m "<nachricht>"` | Erzeugt einen Commit |
| `git rm "*.txt"` | Löscht alle txt-Dateien auf der Festplatte und im Stage |
| `git clean -n` | Zeigt an, welche Dateien `git clean -f` löschen würde (Probelauf) |
| `git clean -f` | ⚠️ Löscht alle untracked Dateien |
| `git clean -fd` | ⚠️ Löscht alle untracked Dateien und zusätzlich untracked Ordner |
| `git checkout -- .` | ⚠️ Verwirft alle nicht gestagten Änderungen an getrackten Dateien (neuer: `git restore .`) |
| `git branch` | Zeigt alle lokalen Branches an |
| `git branch -r` | Zeigt alle Remote-Branches an |
| `git branch <branch>` | Erstellt einen Branch mit dem Namen `<branch>` |
| `git branch -d <branch>` | ⚠️ Löscht den lokalen Branch `<branch>` |
| `git push origin --delete <branch>` | ⚠️ Löscht den Branch `<branch>` auf dem Remote-Repository |
| `git checkout <branch>` | Wechselt den Zeiger (HEAD) auf den Branch `<branch>` (neuer: `git switch <branch>`) |
| `git checkout -b <branch>` | Kurzform für:<br/>`git branch <branch>`<br/>`git checkout <branch>` |
| `git checkout -t origin/<branch>` | Holt den Branch aus dem Remote-Repository als lokalen Branch. Vorher muss `git fetch` ausgeführt werden |
| `git merge <branch>` | Merged `<branch>` in den Branch, auf dem HEAD steht. Steht man auf `main`, wird alles aus `<branch>` in `main` gemerged |
| `git cherry-pick <commit>` | Fügt den Commit `<commit>` eines anderen Branches in den aktuellen Branch ein. Änderungen aus früheren Commits werden **nicht** übernommen |
| `git remote add origin <url>` | Verbindet das lokale Repository mit einem Remote-Repository. Im Prinzip ist das nur ein Lesezeichen auf die URL |
| `git remote -v` | Zeigt alle Remote-Repositories an |
| `git remote rm <remote>` | Löscht den Remote-Eintrag `<remote>` |
| `git fetch` | Lädt alle Objekte und Refs vom Remote-Repository herunter, ohne lokal etwas zu mergen |
| `git fetch <remote>` | Lädt alle Objekte und Refs vom Remote `<remote>` herunter, z. B. `origin` |
| `git remote update` | Führt `git fetch` für alle Remotes aus. Lokale Branches werden dabei nicht angelegt |
| `git pull origin <branch>` | Lädt die neuste Version herunter und merged sie automatisch in den lokalen Branch |
| `git push -u origin <branch>` | Pusht den Branch und merkt sich `origin/<branch>` als Upstream. `origin` ist der Remote-Name |
| `git push` | Nach einmal `push -u` merkt sich Git den Upstream, danach reicht `git push` |
| `git tag` | Zeigt alle vorhandenen Tags an |
| `git tag -a <tag> -m "<nachricht>"` | Erzeugt einen Versions-Tag, z. B. `v1.0` |
| `git push origin <tag>` | Pusht den Tag zum Server |
| `git log` | Zeigt alle Commits an |
| `git log --graph` | Visualisiert den Branch-Verlauf |
| `git log --oneline --graph` | Wie oben, aber pro Commit nur eine Zeile |
| `git log --oneline <branchA>..<branchB>` | Zeigt alle Commits, die in `<branchB>` sind, aber nicht in `<branchA>`.<br/>`<branchA>`: Branch, in den du cherry-picken willst.<br/>`<branchB>`: Branch, aus dem du cherry-picken willst. |
| `git diff` | Zeigt die nicht gestagten Änderungen an |
| `git diff --staged` | Zeigt die gestagten Änderungen an (was man mit `add` hinzugefügt hat) |
| `git diff HEAD` | Zeigt alle Änderungen seit dem letzten Commit an, gestagt und nicht gestagt |
| `git stash` | Legt die aktuellen Änderungen in ein «Lager», um später daran weiterzuarbeiten |
| `git stash list` | Zeigt alle Stashes an |
| `git stash apply` | Holt die letzten Änderungen aus dem «Lager» zurück. Der Eintrag bleibt in der Stash-Liste |
| `git stash pop` | Holt die letzten Änderungen aus dem «Lager» zurück und löscht den Eintrag aus der Stash-Liste |
| `git stash clear` | ⚠️ Löscht alle Stash-Einträge |

### Git commands für Fixes

| Befehl | Beschreibung |
|---|---|
| `git commit --amend` | Öffnet einen Editor, um den letzten Commit zu bearbeiten |
| `git reset <datei>` | Macht `add` für die Datei rückgängig. Die Änderung bleibt in der Datei (neuer: `git restore --staged <datei>`) |
| `git reset --soft HEAD~1` | Macht den letzten Commit rückgängig. Die Änderungen bleiben gestagt |
| `git reset --hard` | ⚠️ Setzt den aktuellen Branch auf den letzten Commit zurück. Löscht alle Änderungen an getrackten Dateien, gestagt und nicht gestagt |
| `git clean -fdx` | ⚠️ Im Working Tree bleibt nur, was im Repository getrackt ist. Löscht auch untracked Ordner (`-d`) und Dateien aus `.gitignore` (`-x`) |

### Projekt komplett "auf Werkseinstellungen" zurücksetzen

* git reset --hard
* git clean -fdx

**git clean**
Entfernt Dateien/Ordner aus dem Arbeitsverzeichnis, die nicht von Git getrackt werden.

**-f (force)**
Zwingend nötig – ohne -f macht Git aus Sicherheitsgründen nichts.

**-d (directories)**
Löscht auch Verzeichnisse, nicht nur einzelne Dateien.

**-x (exclude ignorierte Dateien NICHT)**
Löscht auch Dateien aus .gitignore (z. B. node_modules/, dist/, .env, Build-Artefakte).|

### git reset --soft:
* Dieser Befehl verschiebt den HEAD (den Zeiger auf den aktuellen Commit) und den aktuellen Branch auf den angegebenen Commit.
* **Was passiert**: Die Änderungen bleiben im Staging-Bereich und im Arbeitsverzeichnis unverändert. Du kannst die Änderungen sofort erneut committen, da sie noch im Staging-Bereich sind.
* **Verwendung**: Nützlich, wenn du einen Commit rückgängig machen möchtest, aber die Änderungen nicht verlieren willst. Du kannst sie bearbeiten und erneut committen.

**git reset --mixed** (Standardverhalten von git reset ohne Optionen):
* Dieser Befehl verschiebt ebenfalls den HEAD und den aktuellen Branch auf den angegebenen Commit.
* **Was passiert**: Die Änderungen bleiben im Arbeitsverzeichnis erhalten, aber der Staging-Bereich (Index) wird zurückgesetzt. Das bedeutet, dass die Änderungen nicht mehr gestaged sind, aber sie sind noch in den Dateien vorhanden.
* **Verwendung**: Nützlich, wenn du die Änderungen behalten möchtest, aber sie aus dem Staging-Bereich entfernen willst, um sie erneut zu überprüfen oder zu ändern, bevor du sie commitest.


### Git Command Referenzen:
https://git-scm.com/docs

***
### Git Statistics

git log --pretty=format:%an \
| awk '{ ++c[$0]; } END { for(cc in c) printf "%5d %s\n",c[cc],cc; }'\
| sort -r

***
### Bereits existierendes Projekt zum ersten Mal lokal herunterladen:
* git clone [Remote Adresse]

***
### Neuen Projekt erstellen:

* Repository auf Github erzeugen
* .gitignore dateien im lokalen Ordner packen
* git init
* echo "# test" >> README.md			----> erzeugt die README Datei mit dem Titel "test"
* git remote add origin [github addresse]
* git add *
* git commit -m "Initial commit"
* git push -u origin master

***
### Neues File hinzufügen:
* git add foo.txt
* git commit -m "foo.txt hinzugefügt"
* git push -u origin master

***
### Merging im gleichen Branch:
Bei folgender Message: "Please enter a commit message to explain why this merge is necessary,especially if it merges an updated upstream into a topic branch"
* press "i"
* write your merge message
* press "esc"
* write ":wq" (w=write q=quit)
* then press enter

***
### An einem anderen Branch weiterarbeiten, während man noch offene Änderungen hat:
* git stash
* git checkout "newbranch"
* git add .
* git commit -m ""
* git checkout "oldbranch"
* git stash apply

***
### Mein letzter Commit wurde in ein Feature branch gepusht und muss rückgängig gemacht werden:
Um den zuletzt gepushten Commit in Git rückgängig zu machen, gibt es grundsätzlich zwei gängige Vorgehensweisen. Welche Methode geeignet ist, hängt davon ab, ob du den Verlauf umschreiben möchtest (was beim Zusammenarbeiten mit anderen oft problematisch sein kann) oder ob du durch einen neuen Commit einfach die Änderungen rückgängig machen möchtest.
#### 1) Standardmethode mit git revert (empfohlen)
Mit git revert erzeugst du einen neuen Commit, der die Änderungen eines bestimmten Commits rückgängig macht, ohne den Verlauf umzuschreiben. Dadurch vermeidest du Konflikte, wenn andere bereits den (falschen) Commit gepullt haben.
```
# falls du explizit den allerletzten Commit revertest
git revert HEAD

# oder bei einem bestimmten Commit:
git revert <commit-hash>
```
Nun öffnet sich dein Standard-Editor, in dem du die Commit-Message anpassen kannst (optional).

Revert-Commit abschließen und pushen:
```
git push
```

#### 2) Commit aus der History entfernen (Rewrite mit git reset --hard + Force-Push)
Wenn wirklich nötig (z. B. du hast versehentlich Zugangsdaten veröffentlicht o. Ä.) und du bist sicher, dass niemand den falschen Commit weiter verwendet hat, kannst du den letzten Commit aus der History entfernen. Hierbei musst du jedoch bedenken, dass du die Repository-Historie „umschreibst“. Das kann zu Problemen führen, wenn andere Entwickler denselben Stand schon gepullt haben.

Zurückspringen um einen Commit (lokal):
```
git reset --hard HEAD~1
```

Erzwungener Push (Achtung!):
```
git push --force
```
Damit überschreibst du den Remote-Stand. Jeder, der in der Zwischenzeit von diesem Repository gepullt hat, wird Konflikte bekommen, da sich der Commit-Verlauf geändert hat.

**Nicht empfohlen**, wenn ihr in einem Team arbeitet oder ein offizielles Repository habt, das andere schon nutzen. Dann lieber Methode 1 (mit git revert) verwenden.
