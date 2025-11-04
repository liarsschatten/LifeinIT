#Windows-Server 
# DHCP einrichten

## Erstellung

Im Servermanager auf verwalten klicken

Rollen und Funktionen hinzufügen

Rollen basierte Installation

DHCP hinzufügen

Das Post Deployment geht über die Fahne dabei muss man sich lediglich mit dem Domain Administrator anmelden.

## Einrichtung Scope

`New Scope` einrichten
Name angeben
Geben sie die Dynamische IP Reichweite an.

## Einrichtung Failover

Die DHCP Server sind immer paarweise configuriert mit einem Main und einem Failover.

Man klickt auf `Configure Failover.`
Wähl das Scope aus und bestätigt.

### Load Balance

- Beide Server vergeben Adressen gleichzeitig (Standard: 50/50).
- Bei Ausfall eines Servers übernimmt der andere alle Adressenvergaben.
- Beste Wahl für Standorte im gleichen Netzwerk.

### Hot Standby

- Ein Server (Primary) arbeitet aktiv.
- Der andere (Secondary) steht bereit und übernimmt nur bei Ausfall.
- Ideal für geographisch getrennte Standorte.