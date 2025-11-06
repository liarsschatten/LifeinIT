#Windows-Befehle  
#Windows 
## Erklärung
- Eine **Batch-Datei (.bat oder .cmd)** ist ein Skript für die Windows-Eingabeaufforderung (CMD). 
Damit kannst du Abläufe **automatisieren**, z. B.:
- Benutzer anlegen oder löschen
- Netzlaufwerke verbinden
- Backups ausführen
- Logs schreiben
- Dienste starten/stoppen
## Grundaufbau
Eine Batch-Datei kann mit jedem Texteditor (z. B. Notepad) erstellt werden. Speichere sie anschließend mit der Endung `.bat`, z. B. `meinScript.bat`.
```cmd
@echo off
echo Hallo! Dies ist mein erstes Batch-Skript.
pause
```
- **`@echo off`** → unterdrückt die Anzeige der Befehle.
- **`echo`** → gibt Text in der Konsole aus.
- **`pause`** → wartet auf eine Taste, bevor das Skript fortfährt.

## Wichtige Befehle

| Befehl  | Bedeutung                   |
| ------- | --------------------------- |
| `echo`  | Text anzeigen               |
| `pause` | Wartet auf Tastendruck      |
| `cls`   | Bildschirm löschen          |
| `rem`   | Kommentar                   |
| `start` | Programm/Datei starten      |
| `cd`    | Verzeichnis wechseln        |
| `dir`   | Dateien/Ordner anzeigen     |
| `copy`  | Dateien kopieren            |
| `del`   | Dateien löschen             |
| `if`    | Bedingung prüfen            |
| `for`   | Schleife                    |
| `set`   | Variable setzen             |
| `call`  | Andere Batch-Datei aufrufen |
| `exit`  | Skript beenden              |
## Variablen erstellen
```cmd
set name=Lisa
echo Hallo %name%!
```

**`set name`**  = Erstellt eine Variable namens **`name`**  und weißt ihm ein Wert zu
## Benutzereingabe:

```cmd
set /p name=Wie heißt du? 
echo Hallo %name%!
```

**`set /p`** = Fragt den Benutzer nach einer Eingabe und speichert die in der Variable
**`echo`** = Ausgabe auf CMD(wie z.B. print, System.out.println())
## Schleifen und Bedingungen
```cmd
@echo off
echo Dateien im aktuellen Ordner:
for %%f in (*.*) do (
    echo %%f
)
pause

```

**`%%f`** ist die Variable für jeden Dateinamen.
**`*.*`** bedeutet alle Dateien.