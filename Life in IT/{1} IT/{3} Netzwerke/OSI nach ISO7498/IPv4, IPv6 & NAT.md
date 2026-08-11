# IP-Adresse
Die IPv4-Adresse besteht aus **32 Bit**, aufgeteilt in **4 Oktette zu je 8 Bit**. Sie wird meist in **dezimaler Punktnotation** geschrieben, z. B. `192.168.1.1`.
**Fakten:**
- Gesamtadressraum: \~4,3 Milliarden Adressen (2³²)
- Private IPv4-Adressen (RFC 1918, nicht öffentlich im Internet routbar):
  - 10.0.0.0/8 → 16.777.216 Adressen
  - 172.16.0.0/12 → 1.048.576 Adressen
  - 192.168.0.0/16 → 65.536 Adressen
**CIDR (Classless Inter-Domain Routing):**
- Moderne Methode zur Netzaufteilung, ersetzt alte Klassen
- Schreibweise: **Adresse/Präfix**, z. B. `192.168.1.0/24`
  - `/24` → 24 Bits Netzanteil, 8 Bits Hostanteil
  - 2⁸ − 2 = 254 nutzbare Hosts
Vorteil ist, Netzwerke können exakt nach Bedarf dimensioniert werden.
# Subnetzmaske
Die Subnetzmaske gibt an, welcher Teil der IP-Adresse zum Netzteil und welcher zum Host-Teil gehört. Man legt sie wie eine Maske über die IP-Adresse. Sie besteht aus 32 Bit und beginnt mit Einsen und endet mit Nullen, dabei gibt es nur einen Übergang.
Man kann sie als **CIDR-Präfix** schreiben (`/24`) oder als Dezimalmaske (`255.255.255.0`).
- Der **Netzteil** gehört zum Netzwerk und ist innerhalb des Netzwerks bei allen Geräten gleich.
- Der **Host-Teil** identifiziert einen Host innerhalb des Netzwerks.
## Adressierung
- **Netzwerkadresse:** Identifiziert ein IPv4-Netz und kann keinem Host zugewiesen werden.
- **Hostadresse:** Identifiziert einen einzelnen Host innerhalb eines Netzwerks.
- **Broadcast-Adresse:** Letzte Adresse eines IPv4-Netzes; ermöglicht die Kommunikation mit allen Hosts im jeweiligen Netz.
## DHCP
- **DHCP ist der typische Weg zur automatischen IPv4-Konfiguration.**
- Ein DHCP-Server weist einem Host typischerweise **IP-Adresse, Subnetzmaske, Default Gateway und DNS-Server** zu.
- Die Vergabe erfolgt normalerweise **zeitlich begrenzt (Lease)**.
## Default Gateway
Das **Default Gateway** ist der Router, an den ein Host Pakete für Ziele außerhalb des eigenen IPv4-Netzes sendet.
## Sonderbereiche

- `127.0.0.0/8` → **Loopback**, z. B. `127.0.0.1`
- `169.254.0.0/16` → **Link-Local/APIPA**, wird automatisch verwendet, wenn keine IPv4-Adresse per DHCP bezogen werden konnte.
- `0.0.0.0` → unspezifizierte Adresse, z. B. während der DHCP-Konfiguration.

---
# Network Address Translation

**Network Address Translation (NAT)** ist ein Verfahren, bei dem ein Gerät (z. B. Router) eine Verbindungstabelle mit den internen IP-Adressen eines Netzwerks führt. Die internen IP-Adressen werden **in eine oder mehrere routbare öffentliche IP-Adressen umgewandelt**, die vom Internetanbieter (ISP) dem Kunden zugewiesen wurden. NAT ermöglicht so, dass mehrere Geräte innerhalb eines privaten Netzwerks über eine einzige öffentliche IP-Adresse kommunizieren können, während die internen Adressen verborgen bleiben.
# IPv6
IPv6 ist die Weiterentwicklung von IPv4 und verwendet **128-Bit-Adressen**. Eine Adresse besteht aus **8 Blöcken mit jeweils 16 Bit**, die hexadezimal dargestellt und durch Doppelpunkte getrennt werden.

Beispiel: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
## Adressdarstellung
- Führende Nullen eines Blocks dürfen weggelassen werden:
  - `0db8` → `db8`
- Mehrere aufeinanderfolgende `0000`-Blöcke dürfen einmalig durch `::` ersetzt werden:
  - `2001:db8:0:0:0:0:0:1` → `2001:db8::1`
## Adressarten
- **Unicast:** Kommunikation mit einem einzelnen Ziel
- **Multicast:** Kommunikation mit mehreren Zielen
- **Anycast:** Kommunikation mit dem jeweils nächstgelegenen Ziel aus einer Gruppe
- **Kein Broadcast** bei IPv6
## Unterschiede zu IPv4
- **128 Bit statt 32 Bit** → sehr großer Adressraum
- NAT bei IPv6 grundsätzlich möglich, aber nicht erforderlich, da der große Adressraum öffentliche Adressen für Endgeräte ermöglicht.
- **Kein ARP:** IPv6 verwendet dafür **Neighbor Discovery Protocol (NDP)**
- **Keine Fragmentierung durch Router** → Fragmentierung erfolgt durch den sendenden Host
## Adressvergabe
- **SLAAC:** Automatische Konfiguration einer IPv6-Adresse. Der Router sendet **Router Advertisements (RA)** mit Netzwerkinformationen, z. B. dem IPv6-Präfix, woraus das Gerät dann die IPv6-Adresse bildet. 
- **DHCPv6:** Kann IPv6-Adressen und/oder weitere Netzwerkinformationen bereitstellen.
- **Link-Local:** Automatisch erzeugte Adresse für die lokale Kommunikation (`fe80::/10`).
## Betrieb mit IPv4

IPv4 und IPv6 werden in der Praxis häufig **parallel als Dual Stack** betrieben. Dadurch können beide Protokolle gleichzeitig verwendet werden, während die Umstellung schrittweise erfolgt.