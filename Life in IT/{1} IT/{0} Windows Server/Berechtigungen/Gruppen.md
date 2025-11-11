#Windows #Windows-Server 
# Der Einsatz von Gruppen
Die Gruppen werden in  einer Domäne ähnlich wie User vom Active Directory verwaltet. In Windows nutzt man Gruppen um User zu sortieren und ihnen Berechtigungen effizient zuzuweisen. 
## Gruppen Struktur
Es gibt verschiedene Arten von Gruppen, sie haben unterschiedliche Anwendungsbereiche.
### Globale Gruppen
Nur Benutzer der eigenen Domäne können hier eingefügt werden. Jedoch kann man mit Berechtigungen Ressourcen aus jeder Domain der Gesamtstruktur zuweisen.
### Domain Lokale Gruppen
Können Nutzer aus jeder Domain der Gesamtstruktur aufnehmen. Diese Gruppenform kann nur Ressourcen der eigenen Domain zuweisen.
### Universelle Gruppen
Diese Gruppenform kann sowohl User aus allen Domains der Gesamtstruktur aufnehmen als auch Ressourcen für alle Domains der Gesamtstruktur freigeben.
## AGDLP Strategie
Diese Strategie besagt das User einer Domäne zunächst in Globale Gruppen eingeordnet werden, damit kann man der Gruppe Ressourcen der Gesamtstruktur zuweisen.
Dann wird in der Domain des File Servers eine Domain Lokale Gruppe eingerichtet welche den Globalen Gruppen dann Rechte auf den File Server geben. 
Der Sinn der Strategie ist es die User soweit es geht in Kategorien zu packen um den Administrativen Aufwand so gering wie möglich zu halten. Außerdem trennt man hiermit klar Zugriffsrechte von User Verwaltung.
Universelle Gruppen kommen hier nicht zum Einsatz da man damit sehr leicht zu viele Rechte erteilen kann.