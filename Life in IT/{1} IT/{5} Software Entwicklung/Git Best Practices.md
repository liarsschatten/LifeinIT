#Git  
# Reihenfolge der Merge Strategie
## Branch erstellen und nutzen
Zunächst erstellt man einen eigenen Branch. 
```git
git branch Branchname
```

Dann arbeitet man im eigenen Branch.
```git
git add .
```

Dann erstellt man einen Commit mit einer aussagekräftigen Commit Message
```git
git commit -m "Eine sinnvolle commit message"
```

## Den Main Branch Updaten
Dann wechselt man in den main branch.
```git
git checkout main
```

Danach updatet man den eigenen **main branch** indem man sich die neuesten Änderungen aus dem Remote pullt.
```git
git pull
```

## Mergen und Konflikte lösen
Dann merged man mit dem feature branch.
```git
git merge
```

Hier können merge Konflikte auftreten. Als erstes schaut man welche Dateien Konflikte haben.
``` git
git status
```
Dieser Befehl zeigt an welche Dateien Unterschiede haben.

Man schaut sich die Dateien an welche Konflikte haben die Unterschiede sind wie folgt markiert. 
```datei
<<<<<<< HEAD
Code aus deinem aktuellen Branch
=======
Code aus dem Branch, den du mergen willst
>>>>>>> feature-branch
```
Jetzt kannst du die Konflikte bearbeiten.
Du kannst auch entscheiden eine Version zu behalten. 
Danach schließt man den Commit wie folgt ab.
```git 
git add Datei
```

```git 
git commit
```
## Ins Remote Hochladen
Dann wird ins Remote Repository gepushed.
```git
git push
``` 