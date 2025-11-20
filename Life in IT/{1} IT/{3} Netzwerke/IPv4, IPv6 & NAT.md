#Network-Layer 
# IP-Adresse 
Die IPv4-Adresse besteht aus **32 Bit**, aufgeteilt in **4 Oktette zu je 8 Bit**. Sie wird meist in **dezimaler Punktnotation** geschrieben, z. B. `192.168.1.1`.

**Fakten:**
- Gesamtadressraum: ~4,3 Milliarden Adressen (2³²)    
- Private IPv4-Adressen (RFC 1918, nicht im Internet routbar):    
    - 10.0.0.0/8 → 16.777.216 Adressen        
    - 172.16.0.0/12 → 1.048.576 Adressen        
    - 192.168.0.0/16 → 65.536 Adressen        

**CIDR (Classless Inter-Domain Routing):**

- Moderne Methode zur Netzaufteilung, ersetzt alte Klassen    
- Schreibweise: **Adresse/Präfix**, z. B. `192.168.1.0/24`    
    - `/24` → 24 Bits Netzanteil, 8 Bits Hostanteil        
    - 2⁸ − 2 = 254 nutzbare Hosts        

Vorteil ist, Netzwerke können exakt nach Bedarf dimensioniert werden.

# Subnetzmaske
Die Subnetzmaske gibt an, welcher Teil der IP-Adresse zum Netzteil und welcher zum Host-Teil gehört. Man legt sie wie eine Maske über die IP-Adresse. Sie besteht aus 32 Bit und startet immer mit Einsen und endet immer mit Nullen, dabei gibt es nur einen Sprung. Man kann sie auch als Slash Notation schreiben **(IP-Adresse/24)** als Beispiel oder in Dezimal (255.255.255.0).
Der Netzteil gehört zum Netzwerk und und ist innerhalb des Netzwerks bei allen Geräten gleich.
Der Host-Teil identifiziert den Host und ist für jedes gerät im Netzwerk einzigartig.

---
# Network Address Translation
**Network Address Translation (NAT)** ist ein Verfahren, bei dem ein Gerät (z. B. Router) eine Verbindungstabelle mit den internen IP-Adressen eines Netzwerks führt. Die internen IP-Adressen werden **in eine oder mehrere routbare öffentliche IP-Adressen umgewandelt**, die vom Internetanbieter (ISP) dem Kunden zugewiesen wurden. NAT ermöglicht so, dass mehrere Geräte innerhalb eines privaten Netzwerks über eine einzige öffentliche IP-Adresse kommunizieren können, während die internen Adressen verborgen bleiben.
# IPv6
128-Bit lang und wird im Hexadezimal-System niedergeschrieben. 
Genug IP-Adressen, dass kein NAT mehr nötig ist.

(Imagine man hätte es im Unterricht gehabt - bitte ergänzen :D)


