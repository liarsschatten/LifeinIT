#Windows-Server 
# DNS Erstellen

Im Server Manager auf Tools und dann DNS klicken

## IPv4 Zonen erstellen

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

## IPv6 Zonen erstellen

Gehen sie auf den Reiter Reverse Lookup Zonen
Klicken sie auf neue Zone
Wählen sie die primäre Zone aus
Erstellen sie nun eine IPv6-Reverse-Lookupzone und klicken sie auf weiter
Geben sie die korrekte IPv6 Adresse einschließlich Bit-Maske an
Tragen sie den Präfix der Domain ein
Geben sie einen Dateinamen ein z.B. ipv6._domain_.dns
Lassen sie sichere und unsichere Dynamische Updates zu
Klicken sie auf fertigstellen um den Assistenten zu beenden

## DNS aktivieren

Um den DNS auf einem Computer zu aktivieren müssen sie in CMD den folgenden Befehl eingeben.
```
ipconfig -registerdns
```
Dieser Befehl übergibt die DNS Einträge dem DNS Server

Das sollte man bei allen Servern im Netzwerk machen

## Mit fernem DNS Server verbinden

Im DNS Manager auf `Connect to DNS-Server klicken`. 
Geben sie den Servernamen an.