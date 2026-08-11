#Firewall 
# Allgemeines
Eine Firewall ist ein Mittel zur Überprüfung von Paketen, welche nach OSI-Standard versendet werden. Die verschiedenen Firewall-Typen arbeiten auf verschiedenen Schichten des ISO/OSI Modells und sind daher in der Lage, entweder mehr oder weniger Informationen zu überprüfen. Prinzipiell zu verstehen ist: je gründlicher, desto leistungsaufwändiger ist es.

---
# Paketfilter
Der Paketfilter ist die simpelste Form der Firewall. Er blockiert alles und lässt nur Pakete in oder aus dem System, die entsprechende Eigenschaften besitzen. Diese werden in den Regeln festgelegt. Der Paketfilter kann nach Quell- und Ziel-IP-Adresse, sowie dem Port filtern ([[Transport Layer]]) durch. Er ist wegen der Aufbauweise sehr leistungseffizient, ist aber nicht . Aufgrund der Funktionsweise benötigt sie einen höheren administrativen Aufwand. Sie ist zudem unflexibel (kennt nur offen oder zu), heißt, sie kann nicht dynamisch Ports öffnen und schließen.

---
# Stateful Packet Inspection
Öffnet alle Pakete bis Schicht 5, erstellt eine **Verbindungstabelle**, die eine Anfrage von innen speichert und sie nach außen durchlässt, sie öffnet dann den dazugehörigen Port nach innen für die Antwort.
Dabei wird grundsätzlich alles geblockt und nur durchgelassen, was in der
**Verbindungstabelle** steht. 

---
# Application Level Gateway
Öffnet alle Pakete bis Schicht sieben, heißt, das ALG arbeitet auf allen Schichten des OSI-Modells.
Es schaltet sich wie ein **Proxy** zwischen das **interne Netzwerk** und das **Internet**, dadurch _verschleiert_ der ALG die IP des Clients und filtert die durchkommenden Pakete. Das bedeutet, auch dass man den Client nicht direkt erreichen kann. 
Das ALG kann nur einen Dienst betreuen, heißt, für jeden Dienst benötigt man ein eigenes ALG.    
Zusätzlich zum Filtern nach IP und Port wie beim Paketfilter kann das ALG auch auf Befehle sowie Inhalte filtern, das bedeutet, dass es z. B. alle PUT-Befehle blockieren kann.  
## BSI-Empfehlung
Das BSI empfiehlt, vor und nach dem Application Level Gateway einen Paketfilter zu einzusetzen. 
Diese Kombination sorgt für eine Entlastung des ALGs, weil falsch adressierte Pakete bereits vorher abgefangen werden.  

---
# Hochverfügbarkeit
## Einführung
**Hochverfügbarkeit** bezeichnet das Ziel, wichtige IT-Systeme und -Dienste auch bei Ausfällen möglichst ohne oder nur mit kurzer Unterbrechung bereitzustellen. Durch präventive Maßnahmen wie **Redundanz**, Überwachung und automatisches Umschalten auf Ersatzsysteme wird die Wahrscheinlichkeit und insbesondere die Dauer von Ausfällen reduziert.
## Passive Redundanz
Bei **passiver Redundanz** steht ein Ersatzsystem bereit, das bei einem Ausfall des aktiven Systems dessen Aufgaben übernimmt. Das Ersatzsystem arbeitet im Normalbetrieb nicht aktiv mit.
Je nach Bereitschaft des Ersatzsystems unterscheidet man:

- **Cold Standby:** Ersatzsystem ist ausgeschaltet und muss im Fehlerfall erst gestartet bzw. eingerichtet werden.
- **Warm Standby:** Ersatzsystem läuft bereits, ist aber noch nicht vollständig betriebsbereit.
- **Hot Standby:** Ersatzsystem ist vollständig betriebsbereit und kann nahezu sofort übernehmen.

Die Umschaltung kann manuell oder automatisch erfolgen. Typisch ist beispielsweise ein **Standby-Server**, der bei einem Ausfall des produktiven Servers dessen Dienste übernimmt.
## Aktive Redundanz
Bei **aktiver Redundanz** arbeiten mehrere Systeme gleichzeitig und übernehmen gemeinsam die Aufgaben. Fällt eine Einheit aus, übernehmen die verbleibenden Systeme deren Last.

Eine typische Umsetzung ist **Load Balancing**: Ein Load Balancer verteilt Anfragen auf mehrere Server und nimmt ausgefallene Server automatisch aus der Verteilung.

Aktive Redundanz wird vor allem bei **hochverfügbaren Diensten und Server-Infrastrukturen** eingesetzt.

---
# DMZ

## Allgemeines
Die DMZ beschreibt eine Zone, die vom lokalen Netzwerk getrennt ist. Dort stehen z. B. Fileserver, welche von außen erreichbar sein sollen.

Die DMZ ist ein eigenes Subnetz

Diese Server sind vom Rest des Netzwerkes getrennt, damit Angriffe schwerer den Rest des Netzwerkes betreffen können.
Die DMZ kann in verschiedenen Arten vom eigenen Netzwerk getrennt sein.




