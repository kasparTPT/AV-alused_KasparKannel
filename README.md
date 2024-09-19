# AV-alused_KasparKannel
Selles kursus käisin ma põhjalikult läbi erinevad HTTP serveritega eksperimenteerimised ja sain teha mitmeid serveritega näiteid.
Samuti harjutasin ma siin IP aadressidega ja õppisin üleüldist Serverite ja networkingu teemat.


Konspekteeri Github repositooriumisse praktilised käsurea näited ja ülesanded koos enda kommentaaridega ja ka küsimustega

## Udacity konspekt

printf - selle käsuga saame välja printida stringi või käsu mis me selle järele lisame nt HTTP requestid

Layerid: Application, Transport, Internet, Hardware

Protocols: HTTP/SSH, TCP/UDP, IP, Wifi/ethernet/DSL

Muud kospekti mõisted: URL, password, sessioonid, IP aadressid, acces pointid

Pordi numbrid eristavad sama hosti juures erinevaid applikatsioone ja sessioone
    nt: 80 - HTTP, 22 - SSH, 443 - HTTPS
tavaliselt saab ainelt üks program masina peale korraga kuulata ühte porti. Kuid seda saab leevendada sellega kui programm jooksutab mitu thread'i korraga või pidevalt loop'ib erinevate ühenduste vahel.

DNS - Domain Name Registry, selle kaudu saavad kasutajad mingi aadressi kaudu lehekülgedele minna
CNAME - canonical name
AAAA - IPv6 adress
NS - DNS name server

DNS'il on mitu tasemet mis hoiavad erinval tasemel andmeid domeenide ja nimede kohta, nii cache'ist kuni global root serveriteni

subdomainid on täpsustesed erinevate lehtede kohta, mõnikord neid vaja ei ole, kui veebisaiti ei hoita kindlas serveris. nt github'i saab ilma www. ette panemata, sest neid servereid on nii palju

IPv4 vs IPv6 - ipv4 on vanem interneti protokoll, selle aadressid on teistsugused nt . eraldatud 4 numbri kaupa. 

IP aadressid on kõik bit'ides ja baitides

## Käsurea näited
karl@ip-10-20-27-153:~$ man nc - toob ette nc manual page'i, see pakub palju infot kuidas seal asju üles sättida.

lsof kasuga saab näha mis programmid hetkel mingit porti kuulavad lisa -i lõppu, et see näitaks ainult interneti socket'teid
  nt: sudu lsof -i

printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345   -  browser näitab eff.org kodulehte ja prindib sinu browseri requesti terminali
  
karl@ip-10-20-27-153:~$ ping google.com - see hakkab järjest google'it pingima, kui sa just manuaalselt ei sea mitu korda ta seda tegema peab

host -t a google.com - selle kaudu saab näiteks google'i IP aadressi.

dig ww.udacity.com - dig näitab sarnast infot hostile, aga seda rohkem loetavas vormis scriptidele

printf 'HEAD / HTTP/1.1\r\n Host: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80
        ülevaloleva käsuga saame wikipediast HTTP headerid ja palju muud infot ning cookie'si

ping -c4 8.8.8.8 - see saadab siis neli korda sellele aadressile packet'eid

REE
```
