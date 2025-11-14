#Transport-Layer
# Allgemeines
Ports sind eine Programmadresse, welche auf Ebene 4 des OSI-Modells eingesetzt wird.
Sie sagen aus, an welches Programm das Paket gehen soll.  
# UDP
**UDP** ist ein **Übertragungsprotokoll**, welches hauptsächlich eingesetzt wird, um **schnell** Daten zu übertragen, bei denen es **nicht entscheidend ist**, dass sie **vollständig und fehlerfrei** ankommen – wie zum Beispiel bei **Video-Calls** oder **Live-Streams**. Der **UDP-Header** ist **relativ kurz**, er besteht nämlich nur aus dem **Quell-Port** (Angabe, von welchem Programm gesendet wurde), dem **Ziel-Port** (Angabe, welches Programm angesprochen wird), der **Länge des Headers** (gibt an, wo die eigentlichen Daten beginnen) und der **Checksumme**. Die **Checksumme** besteht aus **16 Bit** und wird **meistens mitgesendet**, um Übertragungsfehler zu erkennen. Wenn **keine Checksumme** verwendet werden soll, **muss sie auf 0 gesetzt** werden.

![[UDP Header.png]]
# TCP
TCP ist ein Übertragungsprotokoll, das vor allem eingesetzt wird, wenn eine **zuverlässige und geordnete Datenübertragung** wichtig ist – zum Beispiel beim **Abrufen von Webseiten**, **E-Mails** oder **Dateidownloads**.  
Im Gegensatz zu UDP stellt TCP sicher, dass **keine Daten verloren gehen** und **in der richtigen Reihenfolge** ankommen. Dafür ist der TCP-Header deutlich umfangreicher.

TCP baut **vor der Übertragung eine Verbindung auf**, überprüft kontinuierlich die Daten und sendet verlorene Pakete erneut – dadurch ist es **langsamer als UDP**, aber **deutlich zuverlässiger**.

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
