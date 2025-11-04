#Windows 
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
- ## CD Syntax: 
	- 
	  ```cmd
	  cd [/d] [<Laufwerk>:][<Pfad>]
	  cd [..]
	  chdir [/d] [<Laufwerk>:][<Pfad>]
	  chdir [..]
		```

- ## CD Parameter

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

- # CLS (Clear)
	- Löscht das Eingabeaufforderungsfenster

- # DIR(Directory)
	- Zeigt eine Liste der Dateien und Unterverzeichnisse eines Verzeichnisses an
	- ## Syntax:
		- ```cmd
			dir [<drive>:][<path>][<filename>] [...] [/p] [/q] [/w] [/d] [/a[[:] <attributes>]
			[/o[[:]<sortorder>]] [/t[[:]<timefield>]] [/s] [/b] [/l] [/n] [/x] [/c] [/4] [/r]
			```
			
- ## DIR Parameter:

| **Parameter** | **Beschreibung**                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------ |
| `[:]`         | Gibt das Laufwerk an, für das eine Auflistung angezeigt werden soll                              |
| `[`           | Gibt das Verzeichnis an, für das eine Auflistung angezeigt werden soll                           |
| `[]`          | Gibt eine bestimmte Datei an, die für die Auflistung angezeigt werden soll                       |
| `/p`          | Zeigt jeweils einen Bildschirm der Auflistung an                                                 |
| `/q`          | Zeigt Dateibesitzinformationen an                                                                |
| `/w`          | Zeigt die Auflistung im breiten Format an                                                        |
| `/d`          | Zeigt die Liste im gleichen Format wie `/w` an, aber die Dateien sind spaltenweise sortiert      |
| `/a[[:] ]`    | Zeigt nur Dateien und Verzeichnisse mit den angegebenen Attributen an                            |
| `/o[[:]`      | Sortiert die Ausgabe nach sortorder, die eine beliebe Kombination der fehlenden Werte sein kann: |

## zu /a

| `h` | Versteckte Dateien                       |
| --- | ---------------------------------------- |
| `d` | Verzeichnisse                            |
| `s` | Systemdateien                            |
| `I` | Punkte reparsieren                       |
| `r` | Schreibgeschützte Dateien                |
| `a` | Dateien, die zu Archivierung bereit sind |
| `i` | nicht inhaltlich indizierte Dateien      |

## zu /o

| `n` | Alphabetisch nach Namen            |
| --- | ---------------------------------- |
| `e` | Alphabetisch nach Erweiterung      |
| `g` | Gruppenverzeichnisse zuerst        |
| `s` | Nach Größe, kleinste zuerst        |
| `d` | Nach Datum/Uhrzeit, älteste zuerst |

# exit
- Beendet den Befehlsinterpreter oder das aktuelle Batchskript

| **Parameter** | **Description**                  |
| ------------- | -------------------------------- |
| `/b`          | Beendet das aktuelle Batchskript |
| `<exitcode>`  | Gibt eine numerische Zahl an.    |

- # find
	- Sucht nach einer Textzeichenfolge in einer Datei oder Dateien und zeigt Textzeilen an, die die angegebenen Zeichenfolgen enthalten.`
- ## find Syntax:`
```cmd
find [/v] [/c] [/n] [/i] [/off[line]] <"string">
[[<drive>:][<path>]<filename>[...]]
```

## find Parameter:

| **Parameter**                     | **Description**                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------- |
| `/v`                              | Zeigt alle Zeilen an, die nicht die angegebene enthalten                              |
| `/c`                              | Zählt die Zeilen, die die angegebene enthalten, und zeigt die Summe an                |
| `/n`                              | Steht vor jeder Zeile mit der Zeilennummer der Datei.                                 |
| `/i`                              | Gibt an, dass bei der Suche die Groß-/Kleinschreibung nicht beachtet wird             |
| `/off[line]`                      | Überspringt keine Datei, für die der Offline-Attributsatz festgelegt ist              |
| `<"string">`                      | required. Gibt die Gruppe von Zeichen an, nach denen Sie suchen möchten               |
| `[<drive:>:] [<path>] <filename>` | Gibt den Speicherort und den Namen der Datei an, in der die Zeichenfolge gesucht wird |

# hostname:
- Zeig den Hostnamenteil des vollständigen Computernamens an.
## hostname Syntax:

```cmd
hostname
```

# pause
- Hält die Verarbeitung eines Batchprogrammes an, zeigt die Eingabeaufforderung an.
## pause Syntax:
```cmd
pause
```

# runas (Changed to Run as administrator)`

- Ermöglicht es einem Benutzer, bestimmte Tools und Programme mit anderen Berechtigungen als denen auszuführen, die die aktuelle Anmeldung des Benutzers bietet.
## runas Syntax:
```cmd
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


# shutdown
- Ermöglicht das Herunterfahren oder Neustarten von jeweils einem lokalen Computer oder Remotecomputer
## shutdown Sytax
```cmd
shutdown [/i | /l | /s | /sg | /r | /g | /a | /p | /h | /e | /o]
[/hybrid] [/soft] [/fw] [/f] [/m \\computer][/t xxx][/d [p|u:]xx:yy [/c "comment"]]
```

## shutdown Parameter

| **Parameter**           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/i`                    | Zeigt das Feld **Fernabschaltung an** . Die Option **/i** muss der erste Parameter nach dem Befehl sein. Wenn **/i** angegeben ist, werden alle anderen Optionen ignoriert.                                                                                                                                                                                                                                                                                                                                                                                |
| `/I`                    | Meldet den aktuellen Benutzer sofort und ohne Zeitüberschreitung ab. Der / **l-Parameter** funktioniert unabhängig und kann nicht mit anderen Parametern kombiniert werden. Versuche, **/l** mit einem anderen Parameter zu kombinieren, werden ignoriert.                                                                                                                                                                                                                                                                                                 |
| `/s`                    | Fährt den Computer herunter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `/sg`                   | Fährt den Computer herunter. Wenn beim nächsten Start die Option **Automatic Restart Sign-On** (Automatische Anmeldung nach einem Neustart) aktiviert ist, meldet sich das Gerät automatisch an und sperrt es basierend auf dem letzten interaktiven Benutzer. Nach der Anmeldung werden alle registrierten Anwendungen neu gestartet.                                                                                                                                                                                                                     |
| `/r`                    | Startet den Computer nach dem Herunterfahren neu.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `/g`                    | Fährt den Computer vollständig herunter und startet ihn neu. Wenn beim Neustart die Option **Automatische Anmeldung beim Neustart** aktiviert ist, meldet sich das Gerät automatisch an und sperrt es basierend auf dem letzten interaktiven Benutzer. Nach der Anmeldung werden alle registrierten Anwendungen neu gestartet.                                                                                                                                                                                                                             |
| `/a`                    | Bricht das Herunterfahren des Systems ab. Kann nur während des Timeoutzeitraums verwendet werden. Kombinieren Sie mit **/fw** , um alle ausstehenden Starts in der Firmware zu löschen.                                                                                                                                                                                                                                                                                                                                                                    |
| `/p`                    | Deaktiviert nur den lokalen Computer (keinen Remotecomputer) ohne Zeitüberschreitung oder Warnung. Sie können **/p** nur mit **/d** oder **/f** verwenden. Wenn Ihr Computer die Ausschaltfunktion nicht unterstützt, wird er heruntergefahren, wenn Sie **/p** verwenden, aber die Stromversorgung des Computers bleibt eingeschaltet.                                                                                                                                                                                                                    |
| `/h`                    | Versetzt den lokalen Computer in den Ruhezustand, wenn der Ruhezustand aktiviert ist. Der Schalter **/f** kann mit dem Schalter **/h** verwendet werden.                                                                                                                                                                                                                                                                                                                                                                                                   |
| `/hybrid`               | Fährt das Gerät herunter und bereitet es für den schnellen Start vor. Diese Option muss mit der Option **/s** verwendet werden.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `/soft`                 | Ermöglicht das ordnungsgemäße Schließen von ausgeführten Prozessen und Anwendungen anstatt einer Zwangsbeendigung.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `/fw`                   | Die Kombination dieser Option mit einer Option zum Herunterfahren führt dazu, dass der nächste Neustart zur Firmware-Benutzeroberfläche wechselt.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `/e`                    | Ermöglicht es Ihnen, den Grund für ein unerwartetes Herunterfahren eines Computers in der Ereignisprotokollierung dokumentieren.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `/o`                    | Wechselt zum Menü **Erweiterte Startoptionen** und startet das Gerät neu. Diese Option muss mit der Option **/r** verwendet werden.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `/f`                    | Erzwingt, dass aktive Anwendungen ohne Vorwarnung geschlossen werden.  <br>**Vorsicht:** Die Verwendung der Option **/f** kann zum Verlust nicht gespeicherter Daten führen.                                                                                                                                                                                                                                                                                                                                                                               |
| `/m \\<computername>`   | Legt den Zielcomputer fest.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `/t <xxx>`              | Legt die Zeitüberschreitung vor dem Herunterfahren auf _xxx_ Sekunden fest. Der gültige Bereich ist 0 bis 315360000 (10 Jahre), und der Standardwert ist 30. Wenn der Timeoutzeitraum größer als 0 ist, wird der Parameter **/f** impliziert.                                                                                                                                                                                                                                                                                                              |
| `/d [p \| u:]<xx>:<yy>` | Listet den Grund für den Neustart oder das Herunterfahren des Systems auf. Die unterstützten Parameterwerte sind:  <br><br>- **P** - Gibt an, dass der Neustart oder das Herunterfahren geplant ist.<br>- **U** - Gibt an, dass der Grund benutzerdefiniert ist.  <br>    Wenn **p** oder **u** nicht angegeben sind, ist der Neustart oder das Herunterfahren nicht geplant.<br>  <br>- _xx_ - Gibt die Hauptgrundzahl an (eine positive ganze Zahl, kleiner als 256).<br>- _Yy_ Gibt die Nebengrundzahl an (eine positive ganze Zahl kleiner als 65536). |
| `/c <comment>`          | Ermöglicht es Ihnen, einen benutzerdefinierten Grund für das Herunterfahren oder Neustarten des Systems zu erstellen. Dieser muss in doppelte Anführungszeichen eingeschlossen werden. Sie können maximal 512 Zeichen verwenden. Kann auch mit dem Parameter **/d** verwendet werden.                                                                                                                                                                                                                                                                      |

# sort
- Liest Eingaben, sortiert Daten und schreibt die Ergebnisse auf den Bildschirm, in eine Datei oder auf ein anderes Gerät.
- ## sort Syntax
	- ```cmd
	  sort [/r] [/+<N>] [/m <kilobytes>] [/l <locale>] [/rec <characters>]
	  [[<drive1>:][<path1>]<filename1>] [/t [<drive2>:][<path2>]] [/o [<drive3>:]
	  [<path3>]<filename3>]
	  ```
## sort Parameter

| Parameter                            | Description                                                                                                                                                                                                                                           |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/r`                                 | Umkehrt die Sortierreihenfolge (d. a. sortiert von Z zu A und von 9 bis 0).                                                                                                                                                                           |
| `/+<N>`                              | Gibt die Nummer der Zeichenposition an, an der **die Sortierung** bei jedem Vergleich beginnt. _N_ kann eine beliebige gültige ganze Zahl sein.                                                                                                       |
| `/m<kilobytes>`                      | Gibt die Menge an Arbeitsspeicher an, die für die Sortierung in Kilobyte (KB) verwendet werden soll.                                                                                                                                                  |
| `/l <Gebietsschema->`                | Überschreibt die Sortierreihenfolge von Zeichen, die durch das Standardgebietsschema des Systems definiert werden (d. a. die Sprache und das Land/die Region, die während der Installation ausgewählt sind).                                          |
| `/Rec <characters>`                  | Gibt die maximale Anzahl von Zeichen in einem Datensatz oder einer Zeile der Eingabedatei an (der Standardwert ist 4.096 und der Maximalwert beträgt 65.535).                                                                                         |
| `[<drive1>:][<path1>]<filename1>`    | Gibt die zu sortierende Datei an. Wenn kein Dateiname angegeben ist, wird die Standardeingabe sortiert. Die Angabe der Eingabedatei ist schneller als das Umleiten derselben Datei wie die Standardeingabe.                                           |
| `/t [<drive2>:][<path2>]`            | Gibt den Pfad des Verzeichnisses an, in dem der Arbeitsspeicher des **Sortierbefehls** gespeichert werden soll, wenn die Daten nicht in den Hauptspeicher passen. Standardmäßig wird das temporäre Systemverzeichnis verwendet.                       |
| `/o [<drive3>:][<path3>]<filename3>` | Gibt die Datei an, in der die sortierte Eingabe gespeichert werden soll. Wenn nicht angegeben, werden die Daten in die Standardausgabe geschrieben. Die Angabe der Ausgabedatei ist schneller als das Umleiten der Standardausgabe an dieselbe Datei. |
| `/unique`                            | Gibt nur eindeutige Ergebnisse zurück.|                                                                                                                                                                                                                                                                                                                                         

# taskkill
- Beendet eine oder mehrere Aufgaben oder Prozesse. Prozesse können nach Prozess-ID oder Imagename beendet werden. Mit dem [Befehl tasklist](https://learn.microsoft.com/de-de/windows-server/administration/windows-commands/tasklist) können Sie die Prozess-ID (PID) für den zu beendenden Prozess ermitteln.
- ## taskkill Syntax
- ```cmd
  taskkill [/s <computer> [/u [<domain>\]<username> [/p [<password>]]]] {[/fi 
  <filter>] [...] [/pid <processID> | /im <imagename>]} [/f] [/t]
  ```

## taskkill Parameter
| Parameter                | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/s <computer>`          | Gibt den Namen oder die IP-Adresse eines Remotecomputers an (keine umgekehrten Schrägstriche verwenden). Die Standardeinstellung ist der lokale Computer.                                                                                                                                                                                                                                                            |
| `/u <domain>\<username>` | Führt den Befehl mit den Kontoberechtigungen des Benutzers bzw. der Benutzerin aus, der bzw. die durch `<username>` oder `<domain>\<username>` angegeben wird. Der Parameter **/u** kann nur angegeben werden, wenn **/s** ebenfalls angegeben ist. Die Standardeinstellung sind die Berechtigungen des Benutzers bzw. der Benutzerin, der bzw. die aktuell bei dem Computer angemeldet ist, der den Befehl ausgibt. |
| `/p <password>`          | Gibt das Kennwort des Benutzerkontos an, das im Parameter **/u** angegeben ist.                                                                                                                                                                                                                                                                                                                                      |
| `/Fi <filter>`           | Wendet einen Filter an, um eine Gruppe von Aufgaben auszuwählen. Sie können mehrere Filter oder das Platzhalterzeichen (`*`) verwenden, um alle Aufgaben oder Imagenamen anzugeben. Die gültigen Filter sind im Abschnitt **Filternamen, Operatoren und Werte** dieses Artikels aufgeführt.                                                                                                                          |
| `/Pid <processID>`       | Gibt die Prozess-ID des zu beendenden Prozesses an.                                                                                                                                                                                                                                                                                                                                                                  |
| `/im <imagename>`        | Gibt den Imagenamen des zu beendenden Prozesses an. Verwenden Sie das Platzhalterzeichen (`*`), um alle Imagenamen anzugeben.                                                                                                                                                                                                                                                                                        |
| `/f`                     | Gibt an, dass Beenden von Prozessen erzwungen wird. Dieser Parameter wird für Remoteprozesse ignoriert. Das Beenden von Remoteprozessen wird immer erzwungen.                                                                                                                                                                                                                                                        |
| `/t`                     | Beendet den angegebenen Prozess und alle von ihm gestarteten Unterprozessse.                                                                                                                                                                                                                                                                                                                                         |
# tasklist
- Zeigt eine Liste der derzeit ausgeführten Prozesse auf dem lokalen Computer oder auf einem Remotecomputer an. **Tasklist** ersetzt das **tlist-Tool** .
## tasklist Syntax:
```cmd 
tasklist [/s <computer> [/u [<domain>\]<username> [/p <password>]]]
[{/m <module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <filter> [/fi <filter> [ ... ]]]
```

## tasklist Parameter:

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/s <computer>`              | Gibt den Namen oder die IP-Adresse eines Remotecomputers an (verwenden Sie keine umgekehrten Schrägstriche). Der Standardwert ist der lokale Computer.                                                                                                                                                                                                     |
| `/u <domain>\<username>`     | Führt den Befehl mit den Kontoberechtigungen des Benutzers aus, der von `<username>` oder von `<domain>\<username>`angegeben wird. Der Parameter **/u** kann nur angegeben werden, wenn **/s** ebenfalls angegeben ist. Die Standardeinstellung ist die Berechtigungen des Benutzers, der derzeit auf dem Computer angemeldet ist, der den Befehl ausgibt. |
| `/p <password>`              | Gibt das Kennwort des Benutzerkontos an, das im Parameter **/u** angegeben ist.                                                                                                                                                                                                                                                                            |
| `/m <module>`                | Listet alle Aufgaben mit geladenen DLL-Modulen auf, die dem angegebenen Musternamen entsprechen. Wenn der Modulname nicht angegeben ist, zeigt diese Option alle Module an, die von den einzelnen Vorgängen geladen wurden.                                                                                                                                |
| `svc`                        | Listet alle Dienstinformationen für jeden Prozess ohne Abkürzung auf. Gültig, wenn der Parameter **/fo** auf **table** gesetzt ist.                                                                                                                                                                                                                        |
| `/Fo {table \| list \| csv}` | Gibt das format an, das für die Ausgabe verwendet werden soll. Gültige Werte sind **table**, **list** und **csv**. Das Standardformat für die Ausgabe ist **Tabelle**.                                                                                                                                                                                     |
| `/nh`                        | Unterdrückt Spaltenüberschriften in der Ausgabe. Gültig, wenn der Parameter **/fo** auf **table** oder **csv** festgelegt ist.                                                                                                                                                                                                                             |
| `/Fi <filter>`               | Gibt die Typen von Prozessen an, die in die Abfrage eingeschlossen oder ausgeschlossen werden sollen. Sie können mehrere Filter verwenden oder das Wildcardzeichen (`\`) verwenden, um alle Aufgaben oder Bildnamen anzugeben. Die gültigen Filter werden im Abschnitt **Filternamen, Operatoren und Werte** Abschnitt dieses Artikels aufgeführt.         |
