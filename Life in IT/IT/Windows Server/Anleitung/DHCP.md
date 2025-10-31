# DHCP einrichten

## Erstellung

Im Servermanager auf verwalten klicken

Rollen und Funktionen hinzufügen

Rollen basierte Installation

DHCP hinzufügen

Das Post Deployment geht über die Fahne dabei muss man sich lediglich mit dem Domain Administrator anmelden.

## Einrichtung Scope

<<<<<<< HEAD
`New Scope` einrichten
=======
New Scope einrichten
>>>>>>> felix_cmd
Name angeben
Geben sie die Dynamische IP Reichweite an.

## Einrichtung Failover

Die DHCP Server sind immer paarweise configuriert mit einem Main und einem Failover.

<<<<<<< HEAD
Man klickt auf `Configure Failover.`
<<<<<<< HEAD
=======
Man klickt auf **Configure Failover.**
>>>>>>> felix_cmd
Wähl das Scope aus und bestätigt.
=======
Wähl das Scope aus und bestätigt.
Man wählt den Partnerserver aus

Es gibt zwei Betriebsmodi.
### Load Balance
- Beide Server vergeben Adressen gleichzeitig (Standard: 50/50).
- Bei Ausfall eines Servers übernimmt der andere alle Adressenvergaben.
- Beste Wahl für Standorte im gleichen Netzwerk.
### Hot Standby
- Ein Server (Primary) arbeitet aktiv.
- Der andere (Secondary) steht bereit und übernimmt nur bei Ausfall.
- Ideal für geographisch getrennte Standorte.
>>>>>>> f58be21d6b9874c27276f1a60a6ff45aa1c8cc44
