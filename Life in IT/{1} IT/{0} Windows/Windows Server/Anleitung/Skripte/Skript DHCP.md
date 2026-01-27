# DHCP einrichten
```powershell
# Installation DHCP
Install-WindowsFeature -Name "DHCP" -IncludeManagementTools

# Autorisieren (Falls Mitglied einer Domain)
Add-DHCPServerINC -DnsName "Servername.deinedomain.local" -IPAddress "192.168.1.3"

# DHCP Scope anlegen
Add-DhcpServerv4Scope -Name "LAN" -StartRange 192.168.1.100 -EndRange 192.168.1.200 -SubnetMask 255.255.255.0 -State Active

# Standardgateway(Router), DNS und Optionen setzen
Set-DhcpServerv4OptionValue -ScopeId 192.168.1.0 -Router 192.168.1.1 -DnsServer 192.168.1.1 -DnsDomain "deinedomain.local"

# Lease Dauer anpassen (optional)
Set-DhcpServerv4Scope -ScopeId 192.168.1.0 -LeaseDuration 3.00:00:00

# Dienst starten und aktivieren
Start-Service DHCPServer
Set-Service DHCPServer -StartupType Automatic

# Konfiguration prüfen
Get-DhcpServerv4Scope
Get-DhcpServerv4OptionValue -ScopeId 192.168.1.0
```
