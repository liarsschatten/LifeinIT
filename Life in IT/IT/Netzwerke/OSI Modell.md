# Schichten
Das OSI Modell ist ein Standard für Datenübertragung im Netzwerk Datentransfer. 
Es wird weltweit genutzt und ist als gängiger Standard unerlässlich. Es besteht aus sieben Layern auch Schichten genannt. Bei einer Datenübertragung werden die schichten immer der Reihenfolge nach durchlaufen. Das heißt wenn ein Gerät bis Schicht 4 kommuniziert werden auch Schicht 1 - 3 durchlaufen. In jeder Schicht wird ein Zusatz vorne drangehängt außer beim Physical Layer.
## Layer 1
Der **Physical Layer** hier werden die Daten in Bits übertragen. In dieser Schicht gibt es kein Übertragungsprotokoll.
## Layer 2
Der **Data Link Layer** verwendet hauptsächlich das Ethernet Protokoll dieses nutzt die MAC-Adresse als eindeutige Identifikation eines Gerätes/ Netzwerk Adapters. Der Zusatz wird Frame genannt. Es wird sichergestellt das die Daten an das richtige Gerät gesendet werden. 
Switches arbeiten auf dieser Ebene.
## Layer 3
Der **Network Layer** nutzt das IP-Protokoll und die dazugehörige IP-Adresse um das Daten Paket an die richtige IP-Adresse zu senden. Dieser Layer spielt eine essentielle Rolle bei der Datenübertragung zwischen Netzwerken. Der Zusatz wird Packet genannt. 
Router arbeiten auf dieser Ebene.
### IPv4
Die Adresslänge beträgt 32 Bit, diese werden in 4 Oktette unterteilt. Jedes Oktett geht von 0 - 255 heißt es gibt 4.294.967.296 IPv4 Adressen.
### IPv6
Die  Adresslänge beträgt 128 Bit, diese bestehen aus 8 Blöcken bestehend aus jeweils 4 Hexa-Dezimal-Zahlen.
## Layer 4
Der **Transport Layer** nutzt die Protokolle TCP und UDP um das Datenpaket dem richtigen Dienst zuzuordnen. Der Zusatz heißt Segment. TCP Segmente haben zusätzlich zum Quell- und Zielport einige eingebaute Sicherheitsfunktionen um fehlerhafte Übertragungen zu verhindern, außerdem wird ein Handshake durchgeführt heißt es wird eine Verbindung hergestellt welche Übertragungsfehler verhindern soll.
Dieser Layer wird von Paketfiltern genutzt um unerwünschte Zugriffe zu blockieren. 
## Layer 5
Der **Session Layer** verwaltet die Verbindung zwischen Endgeräten. 
## Layer 6
Der **Presentation Layer** ist dazu da um die Daten in ihr richtiges Format zu konvertieren. 
## Layer 7
Der **Application Layer** ist für die korrekte Darstellung der Daten verantwortlich. 