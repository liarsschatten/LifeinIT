# Zonen nur mit Powershell einrichten

```powershell
# Forward Lookup Zone
dnscmd /zoneadd example.local /primary /file example.local.dns

# Erklärungen
# dnscmd - Windows Command-line tool
# /zoneadd — creates a new DNS zone
# example.local — the zone name
# /primary — creates a primary zone
# /file example.local.dns — specifies the zone file name

# Create a Reverse Lookup Zone
dnscmd /zoneadd 1.168.192.in-addr.arpa /primary /file 1.168.192.in-addr.arpa.dns

# Erklärungen
# 1.168.192.in-addr.arpa corresponds to the 192.168.1.0/24 network

# Add Record for Forward-Lookup Zones
dnscmd /recordadd example.local server1 A 192.168.1.10

# Add Record for Reverser-Lookup Zones
dnscmd /recordadd 1.168.192.in-addr.arpa 10 PTR server1.example.local

# View all Zones
dnscmd /enumzones
```

# DNS auswählen über Powershell
```powershell
# DNS-Konfiguration

# Zeigt alle Netzwerkadapter an
netsh interace ipv4 show interfaces

# DNS-Server für Ethernet-Adapter setzen
netsh interface ipv4 set dns name="Ethernet" static 192.168.1.2

# Alternativer DNS setzten
netsh interface ipv4 add dns name"Ethernet" 192.68.1.3 index=2
```
