# DC nur mit Powershell einrichten

```powershell
# Computername ändern
Rename-Computer -NewName "DC01" -Restart
```

```powershell
#Statische IP setzen
netsh interface ipv4 show interfaces #Zeigt alle Netzwerkadapter
netsh interfaces ipv4 set address name"Ethernet" static 192.168.1.2 255.255.255.0  192.168.1.1

# Installation Active Directory Domain Services
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools

# Installation Forest (firma.local ist der Beispielhafte Domainname)
Install-ADDSForest -DomainName "firma.local" -DomainNetbiosName "FIRMA" -InstallDns
# Wirst nach Kennwort gefragt (DSRM-Kennwort (Domain Services Restore Mode))
```

# DC auf Funktion überprüfen
```powershell
# Nach Neustart überprüfen, ob DC korrekt eingerichtet ist
Get-Services adws, kdc,netlogon,dns
# Alle sollten den Status "Running" haben
```
# Neuen DC hinzufügen
```powershell
# Weiteren DC zu Domain hinzufügen
Install-ADDSDomainController -DomainName "firma.local" -InstallDns
```
