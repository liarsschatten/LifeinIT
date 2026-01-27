#Windows-Server 
# DC erstellen

## DC-Server vorbereiten

In den Windows-Einstellungen unter `System/Info`, klicken Sie auf `Advanced System Settings`, navigieren Sie zu `Computer Name` und ändern Sie den Namen des Computers auf den gewünschten (finalen) Namen -> Dies ist immer der erste Schritt weil es später sehr viel schwieriger ist und meist Probleme verursacht. Benennen Sie den Computer so, dass der Name eindeutig ist und Sie ihn sich merken können.

Weisen sie dem DC eine statische IPv4-Adresse zu.

Erstellen Sie, wenn noch nicht gemacht, ein lokales Admin-Kontom um einen Zugriff auf den Computer zu gewährleisten, selbst wenn die Domäne nicht erreichbar ist. Dieses Konto agiert somit als Fallback-System.

Danach wäre es hilfreichm einen Ping-Test im Netzwerk durchzuführen. Bitte bedenken, dass ICMP zu den Firewall-Regeln hinzugefügt werden muss.
## DC erstellen

Im Server-Manager auf `Verwalten` klicken

`Rollen und Funktionen hinzufügen`

`Rollenbasierte Installation`

`Active Directory Domain Services hinzufügen`

---

Auf die Fahne klicken
Via den Link den Server zum DC promoten
`Add new Forest`

**Root Domain Name** festlegen, dieser muss mindestens eine **Second Level Domain** sein
Zum Beispiel firma.local, hier ist "firma" der Hostname.


Dann muss das **Directory Service Restore Mode Passwort** festgelegt werden.
Daraufhin muss man den NetBIOS Domain Name festlegen, wobei standardmäßig der Hostname in Capslock angegeben wird.

Hiernach kann man bei Bedarf die Pfade zur AD DS-Datenbank, den Protokolldateien und zum SYSVOL-Ornder anpassen. **Das sollte man im Normalfall nicht machen und eine Anpassung ist auch i. d. R. nicht nötig.**
SYSVOL enthält unter anderem die Group Policies und den Domain Folder.

Dann kommt noch das Review wo, man alle Einstellungen noch einmal überprüfen kann
Im nächsten Schritt prüft Windows die Voraussetzungen.
Solange ganz unten bestätigt wird, dass alle Checks erfolgreich abgeschlossen wurden, kann man die anderen Warnungen ignorieren und die Installation beginnen.
## In Domain einpflegen

Stellen Sie sicher, dass sich der PC im selben Subnetz befindet, also den gleichen IP-Präfix verwendet wie die restlichen Geräte in der Domäne.

Öffnen Sie die **System Settings** unter _About > Advanced Settings > Computer Name > Change_.  
Sobald Sie den Namen geändert haben und der PC zur Domäne hinzugefügt wurde, kann sich der Administrator nur noch über die Domäne anmelden.

Einen neuen Domain Controller hinzufügen. Öffnen Sie den **Server-Manager** und klicken Sie auf **Verwalten > Rollen und Funktionen hinzufügen**. Wählen Sie die Option **"Rollenbasierte oder featurebasierte Installation"** und fahren Sie fort. Wählen Sie die Rolle **Active Directory Domain Services** aus und installieren Sie diese.

Klicken Sie oben rechts im Server-Manager auf die Fahne und folgen Sie dem Link, um den Server in die Domäne aufzunehmen.

Wählen Sie die Option **"Domain Controller zu einer bestehenden Domäne hinzufügen"** aus.  
Geben Sie den vollständigen **Root Domain Name** (z. B. `firma.local`) ein.

Melden Sie sich anschließend über das Domain-Administrator Konto an.

Aktivieren Sie **DNS-Server** und **Globaler Katalog** (Global Catalog).  
Die Warnung unter **DNS-Options** kann in der Regel ignoriert werden.

Wählen Sie unter _Replication_ die Option **"Replicate from: DC1"**, um die Replikation von einem bestehenden Domain Controller einzurichten.

Bei Bedarf können Sie jetzt die Pfade für die AD DS-Datenbank, die Protokolldateien und den **SYSVOL**-Ordner anpassen. **Das sollte man nur tun, wenn man sie beim DC1 verändert hat**

Im nächsten Schritt folgt eine **Review-Seite**, auf der alle gewählten Optionen zur Kontrolle aufgelistet werden.
Windows prüft nun automatisch die Voraussetzungen für die Installation.  
Solange am unteren Rand des Fensters bestätigt wird, dass **alle Voraussetzungen erfolgreich erfüllt** wurden, können verbleibende Warnungen ignoriert und die Installation gestartet werden.

### Integrierte DNS-Einträge

Die Dienste des Domain Controllers werden im Netzwerk mit Service Resource Records identifiziert
Diese werden beim erstellen des DCs automatisch erstellt
Diese sollten unter Forward-Lookupzonen erscheinen
Beim Hochstufen werden die Zonen automatisch ins Active Directory integriert
Sie werden beim Neustart automatisch aktualisiert

## Zusammenspiel

Man sollte nie einen DC einzeln laufen lassen, wenn man einen replizierten DC hat
Bevor man einen Domain Computer einschaltet, muss ein DC verfügbar sein
Snapshots sollten immer gleichzeitig erstellt werden
Falls ein DC zu einem früheren Zeitpunkt zurückgesetzt wird, muss das bei allen DCs des Netzwerks getan werden
