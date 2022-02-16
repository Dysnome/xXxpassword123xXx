- Analyser le PCAP et voir qu'il y a un payload ICMP
- Comprendre le format et extraire le payload :
```bash
$ tshark -r older_trick.pcap -Y "icmp.type == 8" -T fields -e data | cut -c 17- | cut -c -32 | xxd -r -p > data.bin
$ file data.bin
$ unzip data.bin
```
- Analyser le contenu : `cat logins.json | jq .` <- encryptedPassword à déchiffrer
- Créer un nouveau profile Firefox
- Dans firefox : about:profiles > Create New Profiles
- Checker le Root Directory du profile
- Copier le contenu du zip dans le profil : `cp fini/* ~/.mozilla/firefox/4k2urvyr.CTF2`
- Run firefox_decrypt (https://github.com/unode/firefox_decrypt) :
```bash
$ cd firefox_decrypt
$ python3 firefox_decrypt.py 
Select the Mozilla profile you wish to decrypt
1 -> 4k99lrp2.default-esr-1
2 -> ctf
3 -> 6rn31nps.default
4 -> szyfr5h1.default-esr
5 -> 4k2urvyr.CTF2
6 -> fd8m3fro.default-esr-2
5

Website:   https://rabbitmq.makelarid.es
Username: 'Frank_B'
Password: 'CHTB{long_time_no_s33_icmp}'
```