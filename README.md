# Command-List

|Bash command | Description|
|-------------|------------|
|pwd					|aktueller Directory|
|cd "C:\Users\Critex\Documents\"	|Directory ändern|
|cd ..	|Directory Ebene down|
|cat ~/.ssh/id_rsa.pub		|Überprüfung ob schon ein SSH Key pair existiert|
|ssh-keygen -t rsa -C "your.email@example.com" -b 4096					|erstellt einen neuen SSH Key nach rsa Verfahren und 4096 bit Länge|
|ssh -T git@gitlab.com		|Überprüfung einer SSH-Verbindung auf ein gitlab repo|

### Git Basic commands
|git command | Description|
|------------|------------|
|git config --global user.name "Pascal Schaffner"				|Name des Benutzers einstellen (global über alle Projekte)|
|git config --global user.email "pschaffner@foo.com"		|E-Mail des Benutzers einstellen (global über alle Projekte)|
|git config --global --list		|Listet alle Global Konfigurationen auf|
|git config --list		|Listet alle Konfigurationen innerhalb eines Projekts auf. Wenn man für ein bestimmtes Projekt einen andere email verwenden möchte, kann man den oberen Befehl ohne "--global" verwenden|
|git init				|initialisiert ein lokales Repository. Erzeugt .git Datei|
|git status				|zeigt aktuellen Status an|
|git add [dateiname]			|added eine veränderte oder neue Datei|
|git add --all oder * oder .			|added alle veränderten oder neuen Dateien|
|git add docs/\*.txt			|added alle txt-files im "docs" Ordner|
|git add docs/						|added alle files im "docs" Ordner|
|git add -u			|added alle deleted files|
|git reset [HEAD] [dateiname]		|macht "add" wieder rückgänging|
|git reset --hard		|⚠️ setzt den aktuellen branch wieder auf den letzten commit (Achtung, löscht alle Änderungen)|
|git clean -n	-f	|Zeigt an welche Files gelöscht werden würden, wenn man "git clean -f" benutzt|
|git clean -f		|⚠️ löscht alle untracked files|
|git clean -d -f	|⚠️ löscht alle untracked files in allen Subfolders|
|git checkout -- \*		|setzt den Branch wieder zurück auf den letzten Commit|
|git rm "\*.txt"		|removed alle txt-files auf der harddisk, sowie im stage|
|git commit -m "commit nachricht"	|commit erzeugen|
|git branch                             |zeigt alle branches an|
|git branch -r                          |zeigt alle remote branches an|
|git branch featureFoo                  |Erstellt ein branch mit dem Namen "featureFoo"|
|git branch -d featureFoo                  |⚠️Löscht den branch "featureFoo"|
|git push origin --delete featureFoo       |⚠️Löscht den branch "featureFoo" auf dem remote repository|
|git fetch                             |Ladet alle Objects und Refs von den remote repositorys herunter|
|git fetch origin                            |Ladet alle Objects und Refs vom "origin"-repository herunter|
|git checkout -t origin/branch-name         |Holt den Branch aus dem remote repository. Hierfür muss aber zuerst git fetch ausgeührt werden.|
|git checkout featureFoo                |Wechselt den Zeiger (Kopf bzw HEAD) auf den Branch "featureFoo"|
|git checkout -b BranchFoo          |Shorthand für:<br/>git branch BranchFoo  <br/>git checkout BranchFoo|
|git merge featureFoo                |Dieser Befehl wirkt sich immer auf den Branch aus, auf dem man den HEAD hat. Wenn mann auf den Master sitzt und diesen Befehl ausführt, wird alles was im featureFoo ist, ins Master gemerged|
|git clone "addresse"			|Holt eine Kopie des Repositorys|
|git log				|Zeigt alle commits|
|git remote add origin [github addresse]|verbindet das lokale repository mit gibhub. Im Prinzip ist das nichts anderes als ein Link-Bookmark|
|git remote -v  |Zeigt alle remote repositories an|
|git remote update  |Holt alle remote branches auf das Local system|
|git remote rm originFoo  |Löscht den remote Eintrag "originFoo"|
|git push -u origin master		|origin ist der remote name und master der branch name|
|git push		|wenn man einmal den befehl mit -u gemacht hat, merkt sich git die Einstellung und es reicht "git push" einzugeben|
|git pull origin master |Ladet die neuste Version herunter und merged sie automatisch mit dem lokalen Projekt|
|git tag -a v1.0 -m "first version"	|erzeugt ein versions Tags|
|git push origin v1.0 |pusht den Tag zum Server|
|git diff HEAD |zeigt Änderung der letzten commits an (HEAD ist die Referenz der letzten Änderung auf der Time-Line, in der man sich befindet|
|git diff --staged |zeigt Änderung der letzten stage an (was man ge'added hat)|
|git tag				|zeigt alle vorhandenen Tags|
|git log --graph	|Visualisiert den Branchverlauf|
|git log --oneline --graph	|oneline bewirkt, dass pro Log-Eintrag nur eine Row geschrieben wird|
|git --version	|Zeigt die aktuelle Git-Version an|
|git stash	|Versetzt die aktuellen Änderungen in ein "Lager", um an einem anderen Zeitpunkt daran weiter zu arbeiten|
|git stash list	|Zeigt alle "Stashes" an|
|git stash apply	|Holt den letzten Änderungen aus dem "Lager" heraus|
|git stash pop	|Holt den letzten Änderungen aus dem "Lager" heraus und löscht den Eintrag aus der Stash List|
|git stash clear	|Löscht alle Stash-Einträge|
|git cherry-pick d42c389f	|Es wird der Commit "d42c389f" eines anderen Branchs in den aktuellen Branch eingefügt. Alle Änderungen aus früheren Commits werden **nicht** übernommen.|

### Git commands für fixes
|git command | Description|
|------------|------------|
|git commit --amend				|Öffnet ein Editor um den Commit zu editieren|

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
