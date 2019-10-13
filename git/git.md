# Git

VCS ... Version Contol System (Versionierungssystem)

## Probleme / Anforderungen

- Die Codebasis muss regelmäßig gesichert werden.
- Der Entwickler möchte Zugriff auf ältere Versionen seines Programms haben.
- Meistens werden Softwareprodukte in Teams erstellt; jedes Teammitglied braucht Zugriff auf den Sourcecode
- Teammmitglieder arbeiten oft gleichzeitig an den selben Sourcecode-Files. Sämtliche Änderungen müssen in die Codebasis eingepflegt werden.
- Separates Entwickeln von neuen Features, bis diese fehlerfrei sind und anschließendes Einfügen dieser neuen Funktionen in die Codebasis

## Alternativen

Sind ungenügend:

- regelmäßiges zippen der Codebasis und sichern
- zur Verfügung stellen der Codebasis auf einem File-Server und /oder auf der Dropbox (oder vergleichbare Dienste)

## Aufbau

- zentrale VCS zB Subversion
- dezentrale VCS zB Git

Provider: GitHub, Bitbucket, Gitlab


## Anwendungsfälle

### Erstellen eines Projekts

#### Leeres Projekt aus Git-Repo clonen


```
git remote add origin https://github.com/htl-leonding/my-project.git
git push -u origin master
```

#### Bereits bestehendes Projekt ins Git-Repo commiten

```
echo "# delete-me-please" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/htl-leonding/my-project.git
git push -u origin master
```

### Ein Projekt aus dem Repos downloaden (clonen)

`git clone https://github.com/htl-leonding/1920-4ahitm-itp.git`

### Neue und/oder geänderte Dateien ins das Repo einpflegen

#### Alle Dateien in die Staging Area einpflegen

```
git add .
```
#### Nur bestimmte Datein in die Staging Area einpflegen

```
git add file.md
```

#### Alle Dateien aus der Staging Area entfernen die zuvor mit git add hinzugefügt wurden

```
git reset HEAD .
```
#### Bestimmte Datei aus der Staging Area entfernen die zuvor mit git add hinzugefügt wurde

```
git reset HEAD file.md
```

#### Dateien in das local-repo einpflegen

```
git commit -m"first commit"
```

#### Dateien aus dem local-repo entfernen

```
git reset --soft HEAD^
```

#### Dateien in das remote-repo einpflegen

```
git push origin master
```

### Status des Git-Working-Directories ansehen

```
git status
```

### Pretty Printing für Git-Logs

<https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs>

 mit Verwendung von .gitconfig
``` $ nano ~/.gitconfig```
```
[alias]
lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
lg = !"git lg1"
```
```git lg```/ ```git lg1```

### Zweige für eigene Features erstellen

````
git branch new-branch
````

### Branch wechseln

```
$ git checkout new-branch
Switched to branch 'new-branch'
```

In einem Zweig Daten ändern und anschließend im anderen Zweig Daten ändern und beide Änderungen commiten / pushen

### Branch mergen

merge the new-feature into the master branch
```
git checkout master
git merge new-branch
```

### Pull requests durchführen

- Jemand besitzt ein Repo
- Ein anderer cloned dieses Repo und möchte etwas im Original Repo ändern
- Er/Sie führt einen Pull Request durch

### Commits taggen

Szenario: Die einzelnen Releases (zB bei Auslieferung an den Kunden) sollen getagged werden

Begriff der Baseline

### Einen Release-Eintrag im Github erstellen (inkl. Doku)

### Verwerfen der lokalen Änderungen

Was bedeutet `stash`
