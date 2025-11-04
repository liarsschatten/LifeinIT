#Network-Layer 
# IP Adresse 
Die IPv4 Adresse besteht aus 4 Oktetten mit jeweils 8 Bit das heißt sie ist insgesamt 32 Bit lang. 

---
# Subnetzmaske
Subnetzmaske gibt an welcher Teil der IP-Adresse zum Netzteil und welcher zum Hostteil gehört. Man legt sie wie eine Maske über die IP-Adresse. Sie besteht aus 32 Bit und startet immer mit Einsen und Endet immer mit Nullen dabei gibt es nur einen Sprung. Man kann sie auch als Slash Notation schreiben **(IP-Adresse/24)** als Beispiel oder in Dezimal (255.255.255.0).
Der Netzteil gehört zum Netzwerk und und ist innerhalb des Netzwerks bei allen Geräten gleich.
Der Hostteil identifiziert den Host und ist für jedes gerät im Netzwerk einzigartig.

---
# Network Adress Translation
NAT steht für **Network Adress Translation**.
Der **Standardzeitraum** für eine IP Adresse vom Internet Provider ist normalerweise **24 Stunden**.
