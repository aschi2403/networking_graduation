# Netzwerkdienste

## DHCP
### Wof�r wir DHCP verwendet?
DHCP wird verwendet um Clients innerhalb eines Netzes IP-Adressen dynamisch zuzuordnen
Daf�r besitzt jeder DHCP Server einen Bereichen (auch Pool genannt) von IP-Adressen.
Der DHCP Server speichert in einer Tabelle, welche IP-Adressen aktuell vergeben sind und
die MAC-Adresse des jeweiligen Clients.
DHCP kann einem Client noch viele weitere Netzwerkinformationen bereitstellen
- Default Gateway
- DNS Server
- Broadcast
- Subnetmask

### grundlegender Ablauf
- ein Client ohne IP-Adresse (welcher noch keinen DHCP-Server kennt) sendet einen Broastcast ins Netzwerk (MAC-Broadcastadresse)
dieser bleibt im Netzwerk, da ein Router keine Broadcasts weiterleitet
- wenn ein DHCP Server das Packet erh�lt sendet er ein sogenanntes DHCP-Offer an den Client
also ein Angebot dem Client eine gewisse IP-Adresse zur Verf�gung zu stellen
- wenn ein Client mehrere DHCP-Offers erh�lt entscheidet er welches er annehmen m�chte