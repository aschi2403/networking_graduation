# DHCP
## Wofür wir DHCP verwendet?
DHCP wird verwendet um Clients innerhalb eines Netzes IP-Adressen dynamisch zuzuordnen
Dafür besitzt jeder DHCP Server einen Bereichen (auch Pool genannt) von IP-Adressen.
Der DHCP Server speichert in einer Tabelle, welche IP-Adressen aktuell vergeben sind und
die MAC-Adresse des jeweiligen Clients.
DHCP kann einem Client noch viele weitere Netzwerkinformationen bereitstellen
- Default Gateway
- DNS Server
- Broadcast
- Subnetmask

## grundlegender Ablauf
![A test image](images/dhcp-ablauf.png)
- ein Client ohne IP-Adresse (welcher noch keinen DHCP-Server kennt) sendet einen Broastcast ins Netzwerk (MAC-Broadcastadresse)
dieser bleibt im Netzwerk, da ein Router keine Broadcasts weiterleitet
- wenn ein DHCP Server das Packet erhält sendet er ein sogenanntes DHCP-Offer an den Client
also ein Angebot dem Client eine gewisse IP-Adresse zur Verfügung zu stellen
- Wenn ein Client mehrere DHCP-Offers erhält entscheidet er welches er annehmen möchte, er versendet dazu einen DHCP-Request an den Server dessen DHCP-Offer er annehmen möchte.
- Dadurch dass der Client dies wiederum als Broadcast versendet wissen die anderen DHCP-Server, dass der Client ihr Angebot nicht angenommen hat.
- Zum Schluss versendet der DHCP-Server noch eine Bestätigung(DHCP-Acknoledge, Unicast) an den Client, dass er das DHCP-Request erhalten hat

## Einstellungen am DHCP Server
### verpflichtend
- Bereich der zu vergebenden Adressen
- Subnetmask
### optional
- Default Gateway
- DNS Server
- Broadcast

## DHCP Modi
Es gibt 3 DHCP Modi.

### Manuell
Dabei wird einem bestimmten Client immer dieselbe IP-Adresse zugeordnet.
Dazu muss vorher angegeben werden, welche IP-Adresse einer bestimmten MAC-Adresse zugeordnet werden soll.
### Automatisch
Es wird ein bestimmter Bereich von IP-Adressen definiert.
Der Server wählt für jeden Client automatisch eine IP-Adresse aus.
#### Nachteil
- da es bei diesem Modi keine zeitlich begrenzte Gültigkeitsdauer gibt
- kann es passieren, dass dem Server die IP-Adressen ausgehen
### Dynamisch
das Grundprinzip ist dasselbe wie bei Automatisch
jedoch wird zusätzlich zu jeder Adresse eine sogenannte Lease Time vergeben
nach Ablauf der Hälfte der Lease Time muss der Client nachfragen ob er die Adresse behalten darf.
Nach 80% der Zeit muss er sich endgültig entscheiden ob er sie weiterhin verwenden möchte.
Wenn die Lease Time vollständig abgelaufen ist, darf der Client die IP-Adresse nicht mehr verwenden.

## Vorgänger von DHCP
### R-ARP und TFTP Kombination
### BootP
- statisches Protokoll
- MAC-Adresse wird benötigt um IP-Adresse zu bekommen
- Administrator muss Liste führen