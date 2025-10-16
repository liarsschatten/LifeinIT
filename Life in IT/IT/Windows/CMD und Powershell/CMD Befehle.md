# Netzwerk Befehle
## NS Lookup (nslookup)
Nach dem Eingeben von nslookup kann man DNS Einträge suchen
Man kann nach folgenden Sachen suchen:
- Name eines Rechners
- Name eines Rechners._domain_
- IPv4 Adresse eines Rechners
- IPv6 Adresse eines Rechners
# Filesystem Befehle
## CD

- Der Befehl **cd (change directory)** wird verwendet, um das aktuelle Arbeitsverzeichnis zu ändern
- CD Syntax:    

- CD Parameter:

| Parameter  | Beschreibung                                               |
| ---------- | ---------------------------------------------------------- |
| `[:]`      | Laufwerk für die Auflistung                                |
| `[`        | Verzeichnis für die Auflistung                             |
| `[]`       | Bestimmte Datei für die Auflistung                         |
| `/p`       | Zeigt einen Bildschirm der Auflistung                      |
| `/q`       | Zeigt Dateibesitzinformationen                             |
| `/w`       | Zeigt Liste im breiten Format                              |
| `/d`       | Wie `/w`, aber Spalten-sortiert                            |
| `a[[:] ]`  | Zeigt nur Dateien/Verzeichnisse mit bestimmten Attributen* |
| `/o[[:] ]` | Sortiert nach Kombinationen von `n`, `e`, `g`, `s`, `d`*   |

- CLS (Clear)

- Löscht das Eingabeaufforderungsfenster

- DIR(Directory)

- Zeigt eine Liste der Dateien und Unterverzeichnisse eines Verzeichnisses an
- Syntax:

- 		  dir [:][
    

- DIR Parameter:

| **Parameter** | **Beschreibung**                                                                            |
| ------------- | ------------------------------------------------------------------------------------------- |
| `[:]`         | Gibt das Laufwerk an, für das eine Auflistung angezeigt werden soll                         |
| `[`           | Gibt das Verzeichnis an, für das eine Auflistung angezeigt werden soll                      |
| `[]`          | Gibt eine bestimmte Datei an, die für die Auflistung angezeigt werden soll                  |
| `/p`          | Zeigt jeweils einen Bildschirm der Auflistung an                                            |
| `/q`          | Zeigt Dateibesitzinformationen an                                                           |
| `/w`          | Zeigt die Auflistung im breiten Format an                                                   |
| `/d`          | Zeigt die Liste im gleichen Format wie `/w` an, aber die Dateien sind spaltenweise sortiert |
| `/a[[:] ]`    | Zeigt nur Dateien und Verzeichnisse mit den angegebenen Attributen an                       |
 
   **d** - Verzeichnisse  
   **h** - Versteckte Dateien  
   **s** - Systemdateien  
   **I** - Punkte reparsieren  
   **r** - Schreibgeschütze Dateien  
   **a** - Dateien, die zur Archivierung bereit sind  
   **i** - Nicht inhaltlich indizierte Dateien|  
  
  |`/o[[:]| Sortiert die Ausgabe nach sortorder, die eine beliebe Kombination der fehlenden Werte sein kann:   **n** - Alphabetisch nach Namen   **e** - Alphabetische nach Erweiterung   **g** - Gruppenverzeichnisse zuerst   **s** - Nach Größe, kleinste zuerst   **d** - Nach Datum/Uhrzeit, älteste zuerst|   `

 `exit`

`Beendet den Befehlsinterpreter oder das aktuelle Batchskript`

| **Parameter** | **Description**                  |     |
| ------------- | -------------------------------- | --- |
| `/b`          | Beendet das aktuelle Batchskript |     |
|               | Gibt eine numerische Zahl an.    |     |

- `find`

- `Sucht nach einer Textzeichenfolge in einer Datei oder Dateien und zeigt Textzeilen an, die die angegebenen Zeichenfolgen enthalten.`
- `find Syntax:`
```
find [/v] [/c] [/n] [/i] [/off[line]] <"string"> [[:][
```
`find Parameter:`

| **Parameter** | **Description**                                                                       |
| ------------- | ------------------------------------------------------------------------------------- |
| `/v`          | Zeigt alle Zeilen an, die nicht die angegebene enthalten                              |
| `/c`          | Zählt die Zeilen, die die angegebene enthalten, und zeigt die Summe an                |
| `/n`          | Steht vor jeder Zeile mit der Zeilennummer der Datei.                                 |
| `/i`          | Gibt an, dass bei der Suche die Groß-/Kleinschreibung nicht beachtet wird             |
| `/off[line]`  | Überspringt keine Datei, für die der Offline-Attributsatz festgelegt ist              |
| `<"string">`  | required. Gibt die Gruppe von Zeichen an, nach denen Sie suchen möchten               |
| `[:] [`       | Gibt den Speicherort und den Namen der Datei an, in der die Zeichenfolge gesucht wird |

`hostname`
`Zeigt den Hostnamenteil des vollständigen Computernamens an.`
`hostname Syntax:`

```
hostname
```

`pause`

`Hält die Verarbeitung eines Batchprogrammes an, zeigt die Eingabeaufforderung an.`
`pause Syntax:`
```
pause
```

`runas (Changed to Run as administrator)`

`Ermöglicht es einem Benutzer, bestimmte Tools und Programme mit anderen Berechtigungen als denen auszuführen, die die aktuelle Anmeldung des Benutzers bietet.`
`runas Syntax:`
```
runas [{/profile | /noprofile}] [/env] [{/netonly | /savecred}] [/smartcard]
[/showtrustlevels] [/trustlevel] /user: " "
```

| **Parameter**                            | **Description**                                                                                                                              |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `/profile`                               | Lädt das Benutzerprofil                                                                                                                      |
| `/noprofile`                             | Gibt an, dass das Benutzerprofil nicht geladen werden soll                                                                                   |
| `/env`                                   | Nutzt die aktuelle Netzwerkumgebung statt der lokalen Umgebung                                                                               |
| `/netonly`                               | Nur Remotezugriff                                                                                                                            |
| `/savecred`                              | Zeigt, ob Anmeldedaten gespeichert wurden                                                                                                    |
| `/smartcard`                             | Gibt an, ob die Anmeldedaten von einer Smartcard bereitgestellt werden sollen.                                                               |
| `/showtrustlevels`                       | Zeigt Vertrauensstufen an, die als Argumente für verwendet werden können.                                                                    |
| `/trustlevel`                            | Zeigt Berechtigungsstufe, auf der die Anwendung ausgeführt werden soll.                                                                      |
| `/user:<UserAccountName>"<ProgramName>"` | Gibt den Namen des Benutzerkontos an, unter dem das Programm ausgeführt werden soll, den Namen des Programms und den Pfad zur Programmdatei. |


`shutdown`
`sort`
`taskkill`
`tasklist`