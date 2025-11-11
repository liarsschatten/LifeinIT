#Windows-Server 
# Installationsmedium erstellen

1. Erstellen eines Live Mediums (USB Stick) - Empfehlung 'Ventoy'
	1. ISO-Datei von Microsoft-Website beziehen.
	2. Mit Ventoy-Installer einen Ventoy Stick erstellen.
	3. Windows-Server-ISO auf den USB-Stick, jetzt mit dem Namen 'Ventoy', übertragen.

---------------------------------------------------
# Betriebssystem Installieren

1. Wählen der präferierten Sprache
2. Wähle die Version ``Datacenter (mit grafischer Benutzeroberfläche)``
3. Akzeptieren Sie die Lizenzbedingungen und bestätigen Sie.
4. Klicken Sie auf ``Benutzerdefiniert``.
5. Einrichten der Partitionen und Auswählen von der gewünschten Windows-Partition
6. Nach diesem Schritt muss der Rechner neu gestartet werden
7. Einrichten des Kennwortes für das Administrator-Konto
8. Es muss drei der folgenden Kategorien enthalten:
	- Klein- u. Großbuchstaben, Zahlen und Sonderzeichen.

---------------------------------------------------

# Ersteinrichtung

1. Navigieren sie in die Einstellungen unter System/Info
	1. Klicken sie auf ``Erweiterte Systemeinstellungen`` 
	2. Wechseln sie zum Reiter ``Computer Name`` und klicken sie auf ``Computername Ändern`` 
		-> Dies sollte immer der erste Schritt sein, da sonst gerne Probleme entstehen.
2. Benennen sie den Computer mit einem möglichst eindeutigen Namen und melden Sie sich in der Domäne an.
3. Danach kommt ein _wichtiger_ Schritt nämlich das erstellen eines **lokalen Admin** Kontos.
4. Dazu begibt man sich in die Nutzerverwaltung und erstellt zunächst einen Nutzer, dem gibt man dann Administrator Rechte indem man ihn in die Gruppe Administratoren hinzufügt.
5. Er kann einen beliebigen Namen haben, aber für Einheitlichkeit würde ich ihn admin nennen.

---------------------------------------------------
# Windows Server Interface

## Manage

Hier fügt man neue Features hinzu. Beispielsweise:
- [[Hyper V]]
- [[Domain Controller]]
- Administrative Domain und User Services
## Tools

Hier findet man alle Tools zu Verwaltung der einzelnen Dienste.
Einige wichtige Tools im Schnellüberblick:
- HyperV Manager für VMs
- Active Directory Domain Services für die Verwaltung von der Domäne
- DNS für das Einstellen von Domainnamen und die Auflösung der IP-Adressen