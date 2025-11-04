#Netzwerke 
# Installation
1. Installieren sie eine neue Linux VM
	1. Wählen sie IP-Fire ISO aus
2. Gehen sie auf ändern unter Netzwerk Adapter und fügen sie zwei neue hinzu
	1. Der erste sollte bereits auf NAT stehen
	2. Die anderen stellen sie jeweils 
	3. auf internes Netzwerk und die Farben auf _green_ für LAN und _orange_ für DMZ 
3. Dann startet man die VM 
4. Der Installer startet
	1. Klicken sie auf installieren 
	2. Wählen sie die Sprache aus
	3. Wählen sie alle Daten löschen
	4. Nehmen sie das Dateisystem ext4
	5. Danach erstellt er automatisch die Firewall
	6. Neustarten auswählen

---
## Initial Konfiguration
1. Tastatur Layout einstellen
	1. Zeitzone angeben
	2. Hostname einstellen
	3. Dann muss man die Domain angeben für eine Lokale Domäne: localdomain
	4. Root Passwort festlegen
	5. Webadmin Passwort festlegen 

---
## Netzwerk Konfiguration einstellen
1. Typ der Netzwerk Konfiguration = GREEN RED ORANGE
2. Netzwerkkartenzuordnung: hier muss man die Typen von eben den Netzwerk Adaptern zuordnen
3. Adresseinstellungen: hier muss man die Internen IP-Adressen einstellen für die separaten Netzwerke (die Netzadapter sind quasi der Switch in der Virtuellen Umgebung) 
	1. RED erhält DHCP weil es die Verbindung ins Internet ist und wir in einem internen Netzwerk sind und er dann beim Router eine IP Adresse anfragt
	2. ORANGE ist die DMZ wichig ist hier das das Netzwerk einen anderen Netzteil hat als GREEN was das interne Netzwerk ist damit sie nicht direkt miteinander kommunizieren können
4. Danach muss man den DHCP Server konfigurieren
	1. Den dynamischen Adressraum angeben 
	2. Den DNS Server angeben
	3. Die Domain angeben
5. Dann startet die Firewall und ist dann aktiv