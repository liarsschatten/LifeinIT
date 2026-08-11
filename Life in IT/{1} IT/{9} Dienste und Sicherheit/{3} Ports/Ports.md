# Zweck von Ports

Ein **Port** ist eine logische Nummer innerhalb einer Netzwerkverbindung. Er dient dazu, auf einem Gerät verschiedene Netzwerkdienste bzw. Anwendungen voneinander zu unterscheiden.

- Portnummern reichen von **0 bis 65535** (16 Bit).
- Zusammen mit einer IP-Adresse identifizieren sie einen bestimmten Netzwerkendpunkt.
- Beispiel: `192.168.1.10:443` → Gerät `192.168.1.10`, Port `443`.
## Portbereiche

| Bereich | Bezeichnung | Verwendung |
|---|---|---|
| **0–1023** | Well-Known Ports | Standardisierte, allgemein bekannte Dienste |
| **1024–49151** | Registered Ports | Für bestimmte Anwendungen/Hersteller registrierbar |
| **49152–65535** | Dynamic/Private Ports | Dynamisch bzw. temporär verwendbar, z. B. als Client-Port |
Die Bereiche beschreiben hauptsächlich die vorgesehene Vergabe und Verwendung. Technisch kann ein Dienst grundsätzlich auch einen anderen Port verwenden.
# Port-Kennnummern

| Port | Protokoll/Dienst |
|---:|---|
| **20/21** | FTP – Daten / Steuerung |
| **22** | SSH |
| **23** | Telnet |
| **25** | SMTP |
| **53** | DNS |
| **67/68** | DHCP – Server / Client |
| **80** | HTTP |
| **110** | POP3 |
| **123** | NTP |
| **143** | IMAP |
| **161/162** | SNMP – Abfragen / Traps |
| **389** | LDAP |
| **443** | HTTPS |
| **445** | SMB |
| **636** | LDAPS |
| **3389** | RDP |
