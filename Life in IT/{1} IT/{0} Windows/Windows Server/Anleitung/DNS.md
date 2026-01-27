#Windows-Server 
# DNS Erstellen

Im `Server-Manager` auf `Tools` und dann `DNS` klicken

## IPv4-Zonen erstellen

Klicken Sie auf `DNS-Server konfigurieren`
Wählen Sie die mittlere Option für das Einstellen von einer Forward- und Reverse-Lookupzone via GUI
Bestätigen Sie das erstellen einer Forward Lookup Zone
Erstellen Sie eine primäre Zone
Der Zonenname ist der Domainname
Daraufhin wird automatisch eine Zonendatei mit dem Domainnamen und der Endung .dns erstellt
Lassen Sie zunächst sowohl sichere als auch unsichere Aktualisierungen zu
Bestätigen Sie das Erstellen einer Reverse-Lookupzone
Legen Sie den Zonentyp als primär fest
Wählen Sie aus, eine IPv4 Lookup Zone zu erstellen
Tragen Sie den Netzteil der IP-Adresse ein
Übernehmen Sie den vorgeschlagenen Namen
Lassen Sie zunächst sowohl sichere als auch unsichere Aktualisierungen zu

## IPv6-Zonen erstellen

Gehen Sie auf den Reiter `Reverse Lookup Zonen`
Klicken Sie auf neue Zone
Wählen Sie die primäre Zone aus
Erstellen Sie nun eine IPv6-Reverse-Lookupzone und klicken sie auf `Weiter`
Geben Sie die korrekte IPv6-Adresse einschließlich Bit-Maske an
Tragen Sie das Präfix der Domain ein
Geben Sie einen Dateinamen ein, z. B. ipv6._domain_.dns
Lassen Sie sichere und unsichere dynamische Updates zu
Klicken Sie auf `Fertig stellen`, um den Assistenten zu beenden

## DNS aktivieren

Um den DNS auf einem Computer zu aktivieren, müssen sie in CMD den folgenden Befehl eingeben.:
```
ipconfig -registerdns
```
Dieser Befehl übergibt die DNS-Einträge dem DNS-Server

Das sollte man bei allen Servern im Netzwerk machen

## Mit fernem DNS-Server verbinden

Im DNS-Manager auf `Connect to DNS Server klicken`. 
Geben sie den Servernamen an.
