# Installation Windows-Server
## Installationsmedium erstellen

1. Erstellen eines Live Mediums (USB Stick) - Empfehlung 'Ventoy'
	1. ISO-Datei von Microsoft-Website beziehen.
	2. Mit Ventoy-Installer einen Ventoy Stick erstellen.
	3. Windows-Server-ISO auf den USB-Stick, jetzt mit dem Namen 'Ventoy', übertragen.

---------------------------------------------------
## Betriebssystem Installieren

1. Wählen der präferierten Sprache
2. Wähle die Version **Datacenter (mit grafischer Benutzeroberfläche)**
3. Akzeptieren Sie die Lizenzbedingungen und bestätigen Sie.
4. Klicken Sie auf **Benutzerdefiniert**.
5. Einrichten der Partitionen und Auswählen von der gewünschten Windows-Partition
6. Nach diesem Schritt muss der Rechner neu gestartet werden
7. Einrichten des Kennwortes für das Administrator-Konto
8. Es muss drei der folgenden Kategorien enthalten:
	- Klein- u. Großbuchstaben, Zahlen und Sonderzeichen.

---------------------------------------------------

## Ersteinrichtung

1. Navigieren sie in die Einstellungen unter System/Info
2. Klicken sie auf **Computername ändern** -> Dies ist immer der erste Schritt weil es später sehr viel schwieriger ist und meist Probleme verursacht
3. Benennen sie den Computer mit einem möglichst eindeutigen Namen und melden Sie sich in der Domäne an.
4. Danach kommt ein _wichtiger_ Schritt nämlich das erstellen eines **lokalen Admin** Kontos.
5. Dazu begibt man sich in die Nutzerverwaltung und erstellt zunächst einen Nutzer, dem gibt man dann Administrator Rechte indem man ihn in die Gruppe Administratoren hinzufügt.
6. Er kann einen beliebigen Namen haben, aber für Einheitlichkeit würde ich ihn admin nennen.

---------------------------------------------------
## Windows Server Interface

### Manage

Hier fügt man neue Features hinzu. Beispielsweise:
- DNS
- Hyper V
- Administrative Domain und User Services
### Tools

Hier findet man alle Tools zu Verwaltung der einzelnen Dienste.
Einige wichtige Tools im Schnellüberblick:
- HyperV Manager für VMs
- Active Directory Domain Services für die Verwaltung von der Domäne
- DNS für das Einstellen von Domainnamen und die Auflösung der IP-Adressen

---

# Hyper V Installation & Einrichtung

### Allgemeines

Hyper V ist ein Manager für Virtuelle Maschinen kurz VMs. In Hyper V kann man außerdem über einen Virtuellen Switch ein internes Netzwerk aufbauen, wodurch man alle Funktionen von Windows Server virtuell testen kann, ohne tatsächlich ein eigenes Netzwerk aufbauen zu müssen.
### 

- Über das oben beschriebene Feature-Menü unter 'Manage', klicken Sie auf 'Add Roles and Features' und fügen Hyper-V hinzu
- Nach der Installation, starten Sie 'Hyper-V Manager'

#### Einrichten virtueller Switch

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

#### Erstellen virtueller Computer

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

Navigieren sie in die Einstellungen unter System/Info, klicken sie auf **Advanced System Settings**, navigieren sie unter **Computer Name** und ändern sie den Namen auf den finalen Namen -> 
Dies ist immer der erste Schritt weil es später sehr viel schwieriger ist und meist Probleme verursacht. Benennen sie den Computer so das der Name eindeutig ist und sie ihn sich merken können.

Weisen sie dem DC eine statische IPv4 Adresse zu.

Erstellen sie wenn noch nicht gemacht ein lokales Admin-Konto um einen Zugriff auf den Computer zu gewährleisten, selbst wenn die Domäne nicht erreichbar ist. Dieses Konto agiert somit als Fallback-System.

Danach sollte man einen Pingtest im Netzwerk durchführen wobei man ICMP in der Firewall freischalten muss.
### DC Erstellen

Im Servermanager auf verwalten klicken

Rollen und Funktionen hinzufügen

Rollen basierte Installation

Active Directory Domain Services hinzufügen

---

Auf die Fahne klicken
Via den Link den Server zum DC promoten
Add new Forest

**Root Domain Name** festlegen dieser muss mindestens eine **Second Level Domain** sein
Zum Beispiel firma.local hier ist "firma" der Hostname.


Dann muss das Directory Service Restore Mode Passwort festgelegt werden.
Daraufhin muss man den NetBIOS Domain Name festlegen wobei standardmäßig der Hostname in Capslock angegeben wird.

Hiernach kann man bei Bedarf die Pfade zur AD DS-Datenbank, den Protokoll Dateien und zum SYSVOL Folder anpassen. **Das sollte man im Normalfall nicht machen und eine Anpassung ist auch i.d.R. nicht nötig.**
SYSVOL enthält unter anderem die Group Policies und den Domain Folder.

Dann kommt noch das Review wo man alle Einstellungen noch einmal überprüfen kann
Im nächsten Schritt prüft Windows die Voraussetzungen.
Solange ganz unten bestätigt wird dass alle Checks erfolgreich abgeschlossen wurden kann man die anderen Warnungen ignorieren und die Installation beginnen.
### In Domain einpflegen

Stellen Sie sicher, dass sich der PC im selben Subnetz befindet, also den gleichen IP-Präfix verwendet wie die restlichen Geräte in der Domäne.

Öffnen Sie die **System Settings** unter _About > Advanced Settings > Computer Name > Change_.  
Sobald Sie den Namen geändert haben und der PC zur Domäne hinzugefügt wurde, kann sich der Administrator nur noch über die Domäne anmelden.

Einen neuen Domain Controller hinzufügen. Öffnen Sie den **Server-Manager** und klicken Sie auf **Verwalten > Rollen und Funktionen hinzufügen**. Wählen Sie die Option **"Rollenbasierte oder featurebasierte Installation"** und fahren Sie fort. Wählen Sie die Rolle **Active Directory Domain Services** aus und installieren Sie diese.

Klicken Sie oben rechts im Servermanager auf die Fahne und folgen Sie dem Link, um den Server in die Domäne aufzunehmen.

Wählen Sie die Option **"Domain Controller zu einer bestehenden Domäne hinzufügen"** aus.  
Geben Sie den vollständigen **Root Domain Name** (z. B. `firma.local`) ein.

Melden Sie sich anschließend über das Domain-Administrator Konto an.

Aktivieren Sie **DNS-Server** und **Globaler Katalog** (Global Catalog).  
Die Warnung unter **DNS-Options** kann in der Regel ignoriert werden.

Wählen Sie unter _Replication_ die Option **"Replicate from: DC1"**, um die Replikation von einem bestehenden Domain Controller einzurichten.

Bei Bedarf können Sie jetzt die Pfade für die AD DS-Datenbank, die Protokolldateien und den **SYSVOL**-Ordner anpassen. **Das sollte man nur tun wenn man sie beim DC 1 verändert hat**

Im nächsten Schritt folgt eine **Review-Seite**, auf der alle gewählten Optionen zur Kontrolle aufgelistet werden.
Windows prüft nun automatisch die Voraussetzungen für die Installation.  
Solange am unteren Rand des Fensters bestätigt wird, dass **alle Voraussetzungen erfolgreich erfüllt** wurden, können verbleibende Warnungen ignoriert und die Installation gestartet werden.

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

### DNS aktivieren

Um den DNS auf einem Computer zu aktivieren müssen sie in CMD den folgenden Befehl eingeben.
```
ipconfig -registerdns
```
Dieser Befehl übergibt die DNS Einträge dem DNS Server

Das sollte man bei allen Servern im Netzwerk machen

### Mit fernem DNS Server verbinden

Im DNS Manager auf `Connect to DNS-Server klicken`. 
Geben sie den Servernamen an.

---
## DHCP einrichten

### Erstellung

Im Servermanager auf verwalten klicken

Rollen und Funktionen hinzufügen

Rollen basierte Installation

DHCP hinzufügen

Das Post Deployment geht über die Fahne dabei muss man sich lediglich mit dem Domain Administrator anmelden.

### Einrichtung Scope

New Scope einrichten
Name angeben
Geben sie die Dynamische IP Reichweite an.

### Einrichtung Failover
