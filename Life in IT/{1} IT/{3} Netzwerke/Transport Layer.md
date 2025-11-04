#Transport-Layer
# Allgemeines
Ports sind eine Programmadresse welche auf Ebene 4 des OSI-Modells eingesetzt wird.
Sie sagen aus an welches Programm das Paket gehen soll.  
# UDP
UDP ist ein Übertragungsprotokoll welches hauptsächlich eingesetzt wird um Videocalls und Live-Streams zu übertragen. Der UDP Header ist relativ kurz er besteht nämlich nur aus Quell-Port (Angabe von welchem Programm gesendet wurde), Ziel-Port (Angabe welches Programm angesprochen wird), Länge des Headers(Gibt an wo die Daten beginnen) und der Checksumme. 
Die Checksumme besteht aus 16 Bit und wird fast immer mitgesendet, wenn man keine Checksumme haben möchte, muss sie auf 0 gesetzt sein.

![[UDP Header.png]]
# TCP

![[TCP Header.png]]
## Meist genutzte Ports
- 20 - FTP: File Transfer Protocol Data Transfer
- 21 - FTP: Control
- 22 - SSH: Secure Shell
- 25 - SMTP: Secure Mail Transfer Protocol
- 53 - DNS: Domain Name System
- 67 - DHCP: Dynamic Host Configuration Protocol Server Side
- 68 - DHCP: Dynamic Host Configuration Protocol Client Side
- 80 - HTTP: Hyper Text Transfer Protocol
- 110 - POP3: Post Office Protocol
- 389 - LDAP: Lightweight Directory Access Protocol
- 443 - HTTPS: Hypertext Transfer Protocol Secure
- 445 - SMB: Server Message Block
- 3306 - MySQL und MariaDB
- 3389 - RDP: Microsoft Terminal Server