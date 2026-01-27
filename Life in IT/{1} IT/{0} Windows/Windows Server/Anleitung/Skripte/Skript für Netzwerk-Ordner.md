# Netzwerk Ordner automatisch anzeigen lassen
```powershell
# Die Dienste für Netzwerk Ordner automatisch starten
Set-Service -Name Dnscache -StartupType Automatic
Set-Service -Name fdPHost -StartupType Automatic
Set-Service -Name FDResPub -StartupType Automatic
Set-Service -Name SSDPSRV -StartupType Automatic
Set-Service -Name upnphost -StartupType Automatic

# Firewall exclusion einstellen
Set-NetFirewallRule -Enabled True -Profile Domain,Private
```
