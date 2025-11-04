#Windows-Server 
# Domain Controller

Ein Domain Controller, kurz 'DC', sorgt dafür, dass man sich nahtlos mit jedem in der Domäne eingebundenen Rechner verbinden kann.
Er stellt in der Domäne die Anmeldedaten und die Berechtigungen für jeden Nutzer domänenweit ein.

---
## Einführung

Ausfallsicherheit ist ein wichtiges Thema in der IT-Infrastruktur
Es geht dabei darum sicherzustellen, dass wichtige Infrastruktur keine Totalausfälle hat
Es wird auch Redundanz genannt
Bedeutet, dass ein Ersatz bereitsteht, um zu übernehmen, wenn der erste ausfällt
## Gesamtstruktur, Struktur & Domäne
Die Gesamtstruktur bezeichnet einen Forest, also die Gesamtheit aller Strukturen
Strukturen bezeichnen eine Baumstruktur aus z. B. einer Second-Level-Domain und mehreren Unterdomains (firma.intern + abteilung.firma.intern)
Eine Domäne bezeichnet einen abgekapselten Bereich mit einheitlicher Berechtigungsverwaltung
Mehrere Domänen lohnen sich nur bei großen Firmen mit vielen Standorten, wo Millionen von Objekten verwaltet werden
## Domain Name
Der Domain Name muss mindestens eine Second-Level-Domain sein (z.B. firma.local)
Hierbei handelt es sich um einen vollqualifizierten Domainnamen

---
# DNS
DNS steht für **Domain Name System** und ist für die Namensauflösung zuständig
Übersetzt Namen zu IP-Adressen und umgekehrt
Wird in einer internen Tabelle gespeichert
Beispiel: google.com Google = DNS (IP: 8.8.8.8)
## Rolle
Der DNS-Server pflegt eine Tabelle, in welcher IP-Adressen zu Host-Namen zugeordnet werden
Identifiziert alle Computer in einer Domäne - unter anderem den DC - über einen Namen anstatt einer IP-Adresse
Die Internet Domain sollte nicht mit dem internen Domain-Namen übereinstimmen
## Forward Lookup Zones
Der DNS Server erhält eine Anfrage mit einem Namen
DNS schaut in seiner Tabelle nach und gibt die IP zurück
## Reverse Lookup Zones
Der DNS Server erhält eine Anfrage mit einer IP-Adresse
DNS schaut in seiner Tabelle nach und gibt den Namen zurück
## Zusammenspiel mit DHCP-Server
Der Client übermittelt seinen Namen an den DHCP-Server. Daraufhin weist er ihm eine IP-Adresse zu und kommuniziert diese mit dem Client
Der DHCP-Server leitet die zugewiesene IP-Adresse auch an den DNS-Server weiter
## Aufbau der DNS-Dateien
In der Forward Lookup Zone gibt es eine Datei mit dem vollständigen Hostnamen der Domain mit der Endung .dns
In der Reverse Lookup Zone gibt es das Gegenstück dazu, der Dateiname ist wie folgt aufgebaut: umgedrehter Netzteil der IP Adresse und .in-addr.arpa.dns
Die Datei **cache.dns** enthält die Stammserver des Internets
Sie liegt unter **%WINDIR%\System32\dns\cache.dns**
Einträge in der Zonen Datenbank:

**Host, A**
Ressourceneintrag für IPv4-Adressen, kann dynamisch aktualisiert werden

**Host, AAAA**
Ressourceneintrag für IPv6-Adressen, kann dynamisch aktualisiert werden

**Zeiger, PTR**
Ressourceneintrag für die Namensauflösung im Reverse Lookup
Es werden der Hostanteil einer IP-Adresse und der Hostname gespeichert

**Dienst, SRV**
Damit werden Netzwerkdienste vermerkt wie bspw. ein Domaincontroller
### DNS Zonenübertragung
Der SOA /Start of Authority gibt den primären DNS Server an.

Die Zonenübertragung übergibt die DNS-Einträge an alle DNS-Server in der Domäne.

---

# DHCP
 DHCP steht für **Dynamic Host Configuration Protocol** und beschreibt die dynamische IP Adressvergabe.

| Schritt 1 - 4 | Beschreibung                                                         |
| ------------- | -------------------------------------------------------------------- |
| Discover      | Der Client fragt nach einer IP Adresse                               |
| Offer         | Der DHCP Server gibt eine IP Adresse zurück                          |
| Request       | Der Client fragt ob er diese IP erhalten hat                         |
| Acknowledge   | Der DHCP Server gibt die IP Adresse an den Client und reserviert sie |
 Ein DHCP-Server kann mehr als nur eine IP-Adresse vergeben. Typischerweise sendet er:
- **IP-Adresse** (z.B. 192.168.0.10)
- **Subnetzmaske** (z.B. 255.255.255.0)
- **Standard-Gateway** (z.B. 192.168.0.1 – also der Router)
- **DNS-Server** (z.B. 8.8.8.8 oder der Router selbst)
- **Lease Time** (Gültigkeitsdauer der Adresse, z. B. 24 Stunden)
