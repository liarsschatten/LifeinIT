# Allgemeines
Eine Firewall ist ein Mittel zur Überprüfung von Paketen welche nach OSI-Standard versendet werden.

# Paketfilter
Die simpelste Form der Firewall sie blockiert alles und lässt nur bestimmte IPs oder bestimmte [[Ports]] durch. Sie ist wegen der der Aufbauweise leistungseffizient. Aufgrund der Funktionsweise benötigt sie einen höheren Administrativen Aufwand. Sie ist zudem unflexibel (kennt nur offen oder zu), heißt sie kann nicht dynamisch Ports öffnen und schließen.
# Stateful Packet Inspection
Öffnet alle Pakete bis Schicht 5 er erstellt eine **Verbindungstabelle** die eine Anfrage von innen speichert und sie nach außen durchlässt, sie öffnet dann den dazugehörigen Port nach innen für die Antwort.
Dabei wird grundsätzlich alles geblockt und nur durchgelassen was in der
**Verbindungstabelle** steht. 
# Application Level Gateway
Öffnet alle Pakete bis Schicht sieben heißt der ALG arbeitet auf allen Schichten des OSI-Modells.
Er schaltet sich wie ein **Proxy** zwischen das **interne Netzwerk** und das **Internet** dadurch _verschleiert_ der ALG die IP des Clients und filtert die durchkommenden Pakete. Das bedeutet auch dass man den Client nicht direkt erreichen kann. 
Der ALG kann nur einen Dienst betreuen heißt für jeden Server benötigt man eine eigene ALG.    
Zusätzlich zum filtern nach IP und Port wie beim Paketfilter kann die ALG auch auf Befehle sowie Inhalte filtern das bedeutet dass sie z.B. alle PUT Befehle blockieren kann.  
## BSI Empfehlung
Das BSI empfiehlt vor und nach dem Application Level Gateway einen Paketfilter zu einzusetzen. 
Diese Kombination sorgt für eine Entlastung des ALG weil falsch adressierte Pakete bereits vorher abgefangen werden.  
# Hochverfügbarkeit
## Einführung
Ausfallsicherheit ist ein wichtiges Thema in der IT Infrastruktur
Es geht dabei um das Sicherstellen das wichtige Infrastruktur keine Totalausfälle hat
Es wird auch Redundanz genannt
## Passive Redundanz
Bedeutet das ein Ersatz bereitsteht um zu übernehmen wenn der erste ausfällt
## Aktive Redundanz
Bei aktiver Redundanz wird ein Load Balancer davor geschaltet und verteilt die Last auf mehrere Einheiten
# DMZ

## Allgemeines
Die DMZ beschreibt eine Zone die vom Lokalen Netzwerk getrennt ist. Dort stehen z.B. Fileserver welche man von außen erreichbar sein sollen.

Die DMZ ist ein eigenes Subnetz

Diese Server sind vom Rest des Netzwerkes getrennt damit Angriffe nicht den Rest des Netzwerkes betreffen können.
Die DMZ kann in verschiedenen Arten vom eigenen Netzwerk getrennt sein