# security

Multirepo athanos

#Recon Pentest Tools

##ASN - Información IP - Whois - DNS

*(https://bgp.he.net "BGP")
*https://centralops.net/co/
*https://www.robtex.com/
*https://dnsdumpster.com/
*https://mxtoolbox.com
*dig

##Escaneo de puertos - red

*Zenmap - nmap
    ```bash
    nmap -T4 -A -v -Pn domain (Intense scan, no ping)
    nmap -f --open -sV domain (Quick scan, open ports)
    nmap -f --script discovery -sV domain
    nmap -f --script intrusive domain```
*https://hackertarget.com/nmap-online-port-scanner/
*https://shodan.io

*SypapsInt
*NetCraft
*Striker

#3Certificados

*https://crt.sh
*https://www.ssllabs.com
*ssl-cert 
    `nmap -sT -p 443 --script ssl-cert domain`
*ssl-enum-ciphers
	`nmap -sT -p 443 --script ssl-enum-ciphers domain`
*script ssl-dh-params
	`nmap -sT -p 443 --script ssl-dh-params domain`

##Enumeración de subdominios

*Sublist3r
	```bash
    apt install sublist3r
	sublist3r -d domain -t 3 -e engine```
*Findomain
    https://github.com/Findomain/Findomain
*Massdns
*knockpy

##Búsqueda de contenido

###Tecnologías utilizadas

*Wappalyzer
*Cabeceras de la respuestas

###Métodos habilitados

`nmap -sT -p 443 domain --script http-methods`

###Directorios

*dirsearch
	https://github.com/maurosoria/dirsearch

###Keys

*Secretfinder
