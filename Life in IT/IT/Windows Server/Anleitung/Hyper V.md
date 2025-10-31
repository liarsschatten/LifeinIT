# Allgemeines

Hyper V ist ein Manager für Virtuelle Maschinen kurz VMs. Es können virtuelle Switches konfiguriert werden, um ein internes Netzwerk aufzubauen, wodurch alle Funktionen von Windows Server virtuell getestet werden kann, ohne tatsächlich ein eigenes Netzwerk aufbauen zu müssen.

Für jede VM können separat Snapshots, sogenannte **'Checkpoints'** erstellt werden, um einen gewissen Stand einer VM zu sichern.
# Hyper-V Installation

- Über das oben beschriebene Feature-Menü unter 'Manage', klicken Sie auf 'Add Roles and Features' und fügen Hyper-V hinzu
- Nach der Installation, starten Sie den 'Hyper-V Manager'

# Einrichten virtueller Switch

## Allgemein

Sofern keine Verbindung aus dem Netzwerk heraus nötig/erwünscht ist, sollte unbedingt ein virtueller Switch erstellt werden, der intern arbeitet. Dies ist wichtig um den Zugang zum externen Netzwerk zu verhindern, was den Schutz des Netzwerkes dramatisch erhöht.
Außerdem sollte jedes Subnetz an einen eigenen Switch angeschlossen sein, um sie klar zu trennen.

Unter 'Aktionen/Actions' finden Sie den 'Virtual Switch Manager'
Im obersten Menü wählen Sie die gewünschte Konnektivität aus. z.B. 'Intern/Internal'.
Danach wählen Sie einen Namen wenden die Einstellungen unter 'Anwenden/Apply' an

Als nächstes stellt man auf dem Hostcomputer den Virtuellen Switch ein. 
Suchen sie in Windows nach Control Panel
Klicken sie auf **View Network Status and Tasks**
Klicken sie dort auf **Change Adapter Settings**
Wählen sie den Virtuellen Switch an und danach Properties
Und stellen dann IPv4 Settings ein

# Erstellen virtueller Computer

Im ersten Schritt, klicken Sie im Hauptmenü von Hyper-V unter der Kategorie 'Aktionen/Actions' auf 'Neu/New' um den Assistenten für virtuelle Computer zu starten.

- Als erstes müssen wir der VM einen Namen vergeben und den Speicherort angeben
- Danach kann man die Generation auswählen wobei Generation 2 die neuere und bessere Version ist (64bit statt 32bit)
- Dann muss man RAM zuweisen, man kann auch dynamisch RAM zuweisen lassen.
- Das heißt das genau soviel RAM zur Verfügung gestellt wird wie benötigt wird
- Als nächstes gibt man an zu welchem Netzwerk die Maschine gehören soll
- Hier gibt man den zuvor erstellten Switch an
- Im fünften Schritt wird eine Virtuelle Festplatte zugewiesen
- Zuletzt gibt man an welches Betriebssystem man verwenden möchte. Hier direkt die ISO von dem gewünschten System auswählen.