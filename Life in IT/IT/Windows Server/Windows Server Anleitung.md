# Windows Server Tutorial

## Installations Medium erstellen

Man startet mit dem erstellen eines Live Mediums (USB Stick).
Dazu benutze ich bevorzugt Ventoy.
Zuerst lädt man sich die ISO Datei von Microsofts offizieller Website herunter.
Dann erstellt man mit dem Ventoy Installer einen Ventoy Stick.
Zuletzt muss man nur noch die ISO auf das Laufwerk ziehen welches Ventoy heißt.
## Betriebssystem Installieren

Zunächst stellt man die präferierte Sprache ein.
Danach klickt man auf Installieren.
Wichtig ist das man hier **Datacenter (mit grafischer Benutzeroberfläche)** wählt.
Akzeptieren der Lizenzbedingungen.
Danach wählt man **Benutzerdefiniert** aus.
Hier stellt man die Partitionen von Windows ein.
Diese lassen sich später nur noch schwer ändern.
Nach diesem Schritt muss der Rechner neu gestartet werden.
Daraufhin muss man zunächst das Kennwort für das Administrator Konto.
Es muss drei der folgenden Kategorien enthalten.
Klein- u. Großbuchstaben, Zahlen und Sonderzeichen.
Navigieren sie in die Einstellungen unter System/Info.
Klicken sie auf **Computername ändern** -> Dies ist immer der erste Schritt weil es später sehr viel schwieriger ist und meist Probleme verursacht.
Benennen sie den Computer so das der Name eindeutig ist und sie ihn sich merken können.
Tragen sie den richtigen Domainnamen ein.
Danach kommt ein _wichtiger_ Schritt nämlich das erstellen eines **lokalen Admin** Kontos.
Dazu begibt man sich in die Nutzerverwaltung und erstellt zunächst einen Nutzer, dem gibt man dann Administrator Rechte indem man ihn in die Gruppe Administratoren hinzufügt.
Er kann einen beliebigen Namen haben, aber für Einheitlichkeit würde ich ihn admin nennen.
## Windows Server Interface

### Manage

Hier fügt man neue Features hinzu bspw.:
- DNS
- Hyper V
- Administrative Domain und User Services
### Tools

Hier findet man alle Tools zu Verwaltung der einzelnen Dienste.
Einige wichtige Tools im Schnellüberblick:
- HyperV Manager für VMs
- Active Directory Domain Services für die Verwaltung von der Domäne
- DNS für die Einstellung der Domainnamen und die Address Auflösung

---

## Hyper V Installation

### Allgemeines

Hyper V ist ein Manager für Virtuelle Maschinen kurz VMs
In Hyper V kann man außerdem über einen Virtuellen Switch ein internes Netzwerk aufbauen
Dadurch kann man alle Funktionen von Windows Server virtuell testen ohne tatsächlich ein eigenes aufbauen zu müssen
### Hyper V einstellen

Zunächst startet man den 'Hyper V Manager'
#### Einen virtuellen Switch einrichten

Wichtig man sollte unbedingt einen neuen Virtuellen Switch erstellen der intern arbeitet.
Das ist wichtig um das interne Netzwerk vom externen Netzwerk zu trennen für bessere Sicherheit.
Außerdem macht man pro Subnetz einen eigenen Switch um diese klar zu trennen.

Unter 'Aktionen/Actions' finden Sie den 'Virtual Switch Manager'
Im obersten Menü wählt man 'Intern/Internal' aus
Danach wählen Sie einen Namen wenden die Einstellungen unter 'Anwenden/Apply' an

Als nächstes stellt man auf dem Hostcomputer den Virtuellen Switch ein.
Suchen sie in Windows nach Control Panel
Klicken sie auf **View Network Status and Tasks**
Klicken sie dort auf **Change Adapter Settings**
Wählen sie den Virtuellen Switch an und danach Properties
Und stellen dann IPv4 Settings ein

#### Einen virtuellen Computer erstellen

Als nächstes klickt man unter 'Aktionen/Actions' auf 'Neu/New' um den Assistenten für virtuelle Computer zu starten
Als erstes müssen wir der VM einen Namen vergeben und den Speicherort angeben
Danach kann man die Generation auswählen wobei Generation 2 die neuere und bessere Version ist (64bit statt 32bit)
Dann muss man RAM zuweisen, man kann auch dynamisch RAM zuweisen lassen.
Das heißt das genau soviel RAM zur Verfügung gestellt wird wie benötigt wird
Als nächstes gibt man an zu welchem Netzwerk die Maschine gehören soll
Hier gibt man den zuvor erstellten Switch an
Im fünften Schritt wird eine Virtuelle Festplatte zugewiesen
Zuletzt gibt man an welches Betriebssystem man verwenden möchte
Man benötigt hier keinen Installations USB Stick sondern die ISO-Datei

---
## DC erstellen

### DC Server Vorbereiten

Navigieren sie in die Einstellungen unter System/Info
Klicken sie auf **Advanced System Settings**, navigieren sie unter **Computer Name** und ändern sie den Namen auf den finalen Namen -> Dies ist immer der erste Schritt weil es später sehr viel schwieriger ist und meist Probleme verursacht
Benennen sie den Computer so das der Name eindeutig ist und sie ihn sich merken können
Weisen sie dem DC eine statische IPv4 Adresse zu
Erstellen sie wenn noch nicht gemacht ein lokales Admin Konto um falls der Zugriff auf die Domäne nicht funktioniert einen Rückfall Admin zu haben
Danach sollte man einen Pingtest im Netzwerk durchführen wobei man ICMP in der Firewall freischalten muss.
### DC Erstellen

Im Servermanager auf verwalten klicken
Rollen und Funktionen hinzufügen
Rollen basierte Installation
Active Directory Domain Services hinzufügen
Auf die Fahne klicken
Via den Link den Server zum DC promoten
Add new Forest
**Root Domain Name** festlegen dieser muss mindestens eine **Second Level Domain** sein
Zum Beispiel firma.local hier ist firma der Hostname
Dann muss das Directory Service Restore Mode Passwort festgelegt werden
Daraufhin muss man den NetBIOS Domain Name festlegen wobei standardmäßig der Hostname in Capslock angegeben wird
Hiernach kann man bei Bedarf die Pfade zur AD DS-Datenbank, den Protokoll Dateien und zum SYSVOL Folder anpassen
SYSVOL enthält unter anderem die Group Policies und den Domain Folder
Dann kommt noch das Review wo man alle Einstellungen noch einmal überprüfen kann
Im nächsten Schritt prüft Windows die Voraussetzungen
Solange ganz unten bestätigt wird dass alle Checks erfolgreich abgeschlossen wurden kann man die anderen Warnungen ignorieren und die Installation beginnen
### In Domain einpflegen

Muss im selben Subnetz sein (Selber IP Präfix)
Unter System Settings/About/Advanced Settings/Computer Name/Change
Sobald das geschehen ist können sie sich mit dem Administrator nur noch in der Domäne anmelden
DC hinzufügen
Im Servermanager auf verwalten klicken
Rollen und Funktionen hinzufügen
Rollen basierte Installation
Active Directory Domain Services hinzufügen
Auf die Fahne klicken
Via den Link den Server in die Domäne heben
Domain Controller zu einer existierenden Domain hinzufügen
Geben sie den **Root Domain Name** an
Danach muss man sich als Domain Administrator anmelden
Aktivieren sie DNS-Server und Globaler Katalog
Ignoriere die Warnung bei DNS Options
Replicate from DC 1
Hiernach kann man bei Bedarf die Pfade zur AD DS-Datenbank, den Protokoll Dateien und zum SYSVOL Folder anpassen
SYSVOL enthält unter anderem die Group Policies und den Domain Folder
Dann kommt noch das Review wo man alle Einstellungen noch einmal überprüfen kann
Im nächsten Schritt prüft Windows die Voraussetzungen
Solange ganz unten bestätigt wird dass alle Checks erfolgreich abgeschlossen wurden kann man die anderen Warnungen ignorieren und die Installation beginnen

#### Integrierte DNS Einträge

Die Dienste des Domaincontrollers werden im Netzwerk mit Service Resource Records identifiziert
Diese werden beim erstellen des DCs automatisch erstellt
Diese sollten unter forward lookup zonen erscheinen
Beim Hochstufen werden die Zonen automatisch ins Active Directory integriert
Sie werden beim Neustart automatisch aktualisiert

### Zusammenspiel

Man sollte nie einen DC einzeln laufen lassen wenn man einen replizierten DC hat
Bevor man einen Domain Computer einschaltet muss ein DC verfügbar sein
Snapshots sollten immer gleichzeitig erstellt werden
Falls ein DC zu einem früheren Zeitpunkt zurückgesetzt wird muss das bei allen DCs des Netzwerks getan werden

---
## DNS Erstellen

Im Server Manager auf Tools und dann DNS klicken

### IPv4 Zonen erstellen

Klicken sie auf DNS-Server konfigurieren
Wählen sie die mittlere Option für das einstellen von einer Forward und Reverse Lookup Zone via GUI
Bestätigen sie das erstellen einer Forward Lookup Zone
Erstellen sie eine primäre Zone
Der Zonenname ist der Domainname
Daraufhin wird automatisch eine Zonendatei mit dem Domainnamen und der Endung .dns erstellt
Lassen sie zunächst sowohl sichere als auch unsichere Aktualisierungen zu
Bestätigen sie das erstellen einer Reverse Lookup Zone
Legen sie den Zonentyp als primär fest
Wählen sie aus eine IPv4 Lookup Zone zu erstellen
Tragen sie den Netzteil der IP Adresse
Übernehmen die den vorgeschlagenen Namen
Lassen sie zunächst sowohl sichere als auch unsichere Aktualisierungen zu

### IPv6 Zonen erstellen

Gehen sie auf den Reiter Reverse Lookup Zonen
Klicken sie auf neue Zone
Wählen sie die primäre Zone aus
Erstellen sie nun eine IPv6-Reverse-Lookupzone und klicken sie auf weiter
Geben sie die korrekte IPv6 Adresse einschließlich Bit-Maske an
Tragen sie den Präfix der Domain ein
Geben sie einen Dateinamen ein z.B. ipv6._domain_.dns
Lassen sie sichere und unsichere Dynamische Updates zu
Klicken sie auf fertigstellen um den Assistenten zu beenden

---
## DHCP einrichten

