- Analyse du PCAP -> Transmission USB
- On remarque une quantité importante de packets URB_INTERRUPT in
- Les paquets de 1.2.2 vers host (le clavier vers l'ordinateur) on un HID Data -> Ca représente une frappe de clavier
- On extrait les HID Data (le sed est utile pour virer les lignes vides des  paquets host -> 1.2.2) (https://gist.github.com/ImAnEnabler/091a9e1ee2d6a0805408e009e2f4a2b5) :
```bash
$ tshark -r key_mission.pcap -T fields -e usbhid.data | sed -r '/^\s*$/d' > payload.bin
$ python3 usb_hid_data_decode.py payload.bin 
Ispaceamspacesendingspacesecretary'sspacelocationspaceoverspacethisspacetotallyspaceencryptedspacechannelspacetospacemakespacesurespacenospaceonespaceelsespacewillspacebespaceablespacetospacereadspaceitspaceexceptspaceofspaceus.spaceThisspaceinformationspaceisspaceconfidentialspaceandspacemustspacenotspacebespacesharedspacewithspaceanyonespaceelse.spaceThespacesecretary'sspacehiddenspacelocationspaceisspaceCHTB{a_plac3_fAr_fAr_away_fr0m_eaedelrth}
```
- Retirer le "adel" du flag dû à un problème de decode
