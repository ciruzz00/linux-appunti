# Cisco IOS Cheatsheet

## Comandi Generali

| Comando | Descrizione |
|---------|-------------|
| `enable` | Modalità privilegiata |
| `configure terminal` | Modalità configurazione |
| `end` | Torna a modalità privilegiata |
| `exit` | Esci da modalità corrente |
| `write memory` | Salva configurazione |
| `copy running-config startup-config` | Salva configurazione |
| `wr` | Salva configurazione (abbreviato) |
| `write erase` | Cancella startup-config |
| `erase startup-config` | Cancella startup-config |
| `delete vlan.dat` | Cancella database VLAN |
| `reload` | Riavvia dispositivo |
| `show running-config` | Configurazione attiva |
| `show startup-config` | Configurazione salvata |
| `show version` | Versione IOS e hardware |
| `show mac address-table` | Tabella MAC |
| `show arp` | Tabella ARP |
| `show ip arp` | Tabella ARP IP |

## Amministrazione Porte

| Comando | Descrizione |
|---------|-------------|
| `interface port-channel [number]` | Configura port-channel |
| `show interfaces status` | Stato interfacce |
| `show interfaces [int]` | Dettagli interfaccia |
| `show interfaces description` | Descrizioni interfacce |

## Configurazione IP e Subnet

| Comando | Descrizione |
|---------|-------------|
| `ip address [ip] [mask]` | Configura IP su interfaccia |
| `ip address [ip] [mask] secondary` | IP secondario |
| `no shutdown` | Attiva interfaccia |
| `shutdown` | Disattiva interfaccia |
| `description [text]` | Descrizione interfaccia |
| `show ip interface brief` | Riepilogo IP interfacce |
| `show ip interface [int]` | Dettagli IP interfaccia |
| `show running-config interface [int]` | Configurazione interfaccia |


## VLAN

| Comando | Descrizione |
|---------|-------------|
| `vlan [number]` | Crea/modifica VLAN |
| `name [name]` | Assegna nome alla VLAN |
| `no vlan [number]` | Elimina VLAN |
| `show vlan brief` | Mostra VLAN configurate |
| `show vlan id [number]` | Dettagli VLAN specifica |
| `interface vlan [number]` | Configura SVI |
| `ip address [ip] [mask]` | IP su interfaccia VLAN |

## Porte Access

| Comando | Descrizione |
|---------|-------------|
| `interface [type] [number]` | Seleziona interfaccia |
| `interface range [type] [range]` | Seleziona range interfacce |
| `switchport mode access` | Imposta porta in modalità access |
| `switchport access vlan [number]` | Assegna porta a VLAN |

## Porte Trunk

| Comando | Descrizione |
|---------|-------------|
| `switchport mode trunk` | Imposta porta in modalità trunk |
| `switchport trunk encapsulation dot1q` | Encapsulation 802.1Q |
| `switchport trunk allowed vlan [list]` | VLAN permesse sul trunk |
| `switchport trunk allowed vlan all` | Permetti tutte le VLAN |
| `switchport trunk allowed vlan add [list]` | Aggiungi VLAN al trunk |
| `switchport trunk allowed vlan remove [list]` | Rimuovi VLAN dal trunk |
| `switchport trunk native vlan [number]` | Imposta native VLAN |
| `show interfaces trunk` | Stato porte trunk |
| `show interfaces [int] switchport` | Dettagli switchport |

## Routing

| Comando | Descrizione |
|---------|-------------|
| `ip routing` | Abilita routing (switch L3) |
| `ip route [network] [mask] [next-hop]` | Rotta statica |
| `ip route [network] [mask] [interface]` | Rotta statica via interfaccia |
| `ip route 0.0.0.0 0.0.0.0 [next-hop]` | Default route |
| `no ip route [network] [mask] [next-hop]` | Rimuovi rotta |
| `version 2` | RIP versione 2 |
| `show ip route` | Tabella routing |
| `show ip route [network]` | Dettagli rotta specifica |

## SSH

| Comando | Descrizione |
|---------|-------------|
| `hostname [name]` | Imposta hostname |
| `ip domain-name [domain]` | Imposta domain name |
| `crypto key generate rsa` | Genera chiavi RSA |
| `crypto key zeroize rsa` | Elimina chiavi RSA |
| `ip ssh version 2` | Forza SSH v2 |
| `username [name] privilege [level] secret [password]` | Crea utente |
| `line vty 0 15` | Configura linee VTY |
| `transport input ssh` | Permetti solo SSH |
| `login local` | Usa database utenti locale |
| `show ip ssh` | Configurazione SSH |
| `show ssh` | Sessioni SSH attive |
| `show crypto key mypubkey rsa` | Mostra chiave pubblica |

## NAT (Network Address Translation)

| Comando | Descrizione |
|---------|-------------|
| `ip nat inside` | Interfaccia inside |
| `ip nat outside` | Interfaccia outside |
| `ip nat inside source static [local] [global]` | NAT statico |
| `ip nat inside source list [acl] interface [int] overload` | PAT (NAT overload) |
| `ip nat inside source list [acl] pool [name] overload` | NAT dinamico con pool |
| `ip nat pool [name] [start-ip] [end-ip] netmask [mask]` | Crea pool NAT |
| `access-list [number] permit [network] [wildcard]` | ACL per NAT |
| `ip nat inside source static tcp [local-ip] [local-port] [global-ip] [global-port]` | Port forwarding |
| `show ip nat translations` | Traduzioni NAT attive |
| `show ip nat statistics` | Statistiche NAT |

