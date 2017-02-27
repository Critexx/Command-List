# Command-List
|Command | Description|
|--------|------------|
|pwd					|aktueller Directory|
|cd "C:\Users\Critex\Documents\"	|Directory ändern|
|git config --global user.name "Pascal Schaffner"				|Name des Benutzers einstellen|
|git config --global user.email "pschaffner@foo.com"		|E-Mail des Benutzers einstellen|
|git init				|initialisiert ein lokales Repository. Erzeugt .git Datei|
|git status				|zeigt aktuellen Status an|
|git add [dateiname]			|added eine veränderte oder neue Datei|
|git add --all oder * oder .			|added alle veränderten oder neuen Dateien|
|git add docs/\*.txt			|added alle txt-files im "docs" Ordner|
|git add docs/						|added alle files im "docs" Ordner|
|git add -u			|added alle deleted files|
|git reset [HEAD] [dateiname]		|macht "add" wieder rückgänging|
|git reset --hard		|setzt den aktuellen branch wieder auf den letzten commit (löscht alle Änderungen|
|git clean -f		|löscht alle untracked files|
|git checkout -- \*		|setzt den Branch wieder zurück auf den letzten Commit|
|git rm "\*.txt"		|removed alle txt-files auf der harddisk, sowie im stage|
|git commit -m "commit nachricht"	|commit erzeugen|
|git branch                             |zeigt alle branches an|
|git branch featureFoo                  |Erstellt ein branch mit dem Namen "featureFoo"|
|git branch -d featureFoo                  |Löscht den branch "featureFoo"|
|git push origin --delete featureFoo       |Löscht den branch "featureFoo" auf dem remote repository|
|git checkout -t(-b) origin/branch-name         |Holt den Branch aus dem remote repository|
|git checkout featureFoo                |Wechselt den Zeiger (Kopf bzw HEAD) auf den Branch "featureFoo"|
|git merge featureFoo                |Dieser Befehl wirkt sich immer auf den Branch aus, auf dem man den HEAD hat. Wenn mann auf den Master sitzt und diesen Befehl ausführt, wird alles was im featureFoo ist, ins Master gemerged|
|git clone "addresse"			|Holt eine Kopie des Repositorys|
|git log				|Zeigt alle commits|
|git remote add origin [github addresse]|verbindet das lokale repository mit gibhub. Im Prinzip ist das nichts anderes als ein Link-Bookmark|
|git remote -v  |Zeigt alle remote repositories an|
|git remote update  |Holt alle remote branches auf das Local system|
|git remote rm originFoo  |Löscht den remote Eintrag "originFoo"|
|git push -u origin master		|origin ist der remote name und master der branch name|
|git push		|wenn man einmal den befehl mit -u gemacht hat, merkt sich git die Einstellung und es reicht "git push" einzugeben|
|git pull origin master |holt den aktuellen master|
|git tag -a v1.0 -m "first version"	|erzeugt ein versions Tags|
|git push origin v1.0 |pusht den Tag zum Server|
|git diff HEAD |zeigt Änderung der letzten commits an (HEAD ist die Referenz der letzten Änderung auf der Time-Line, in der man sich befindet|
|git diff --staged |zeigt Änderung der letzten stage an (was man ge'added hat)|
|git tag				|zeigt alle vorhandenen Tags|

### Git Command Referenzen:
https://git-scm.com/docs

***
### Bereits existierendes Projekt zum ersten Mal lokal herunterladen:
* git clone [Remote Adresse]

***
### Neuen Projekt erstellen:

* Repository auf Github erzeugen
* .gitignore dateien im lokalen Ordner packen
* git init
* echo "# test" >> README.md			----> erzeugt die README Datei mit dem Titel "test"
* git add *
* git commit -m "Initial commit"
* git remote add origin [github addresse]		-------> Muss man nur einmal machen
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
