# 🐦 Volatility

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Volatility needs profiles to work.** When we have the memory image file we want to analyze we first need to use the command **`volatility -f memdump.mem imageinfo`**. Once this command is run, Volatility will identify the system the memory image was taken from, including the operating system, version, and architecture. For example, if we took a memory image from a Windows 7 machine with Service Pack 1 and it had a 64-bit architecture, Volatility would tell us the best profile to use is Win7SP1x64. In the below screenshot, we can see that this memory image has been given a suggested profile of WinXPSP2x86 (Windows XP, Service Pack 2, 32-bit architecture). When running any other command on this memory image we need to provide the profile somewhere, in the format **`--profile=WinXPSP2x86`**, otherwise, the command will not run.

### **Liste des commandes (Version 2.7)**

**`volatility -f memdump.mem imageinfo`//** Prend l'image mémoire "memdump.mem" et détermine le profil suggéré pour l'analyse. Le profil est le système d'exploitation, la version et l'architecture.

**`volatility -f memdump.mem --profile=PROFILE pslist`** **//** Prend l'image mémoire, fournit le profil, puis utilise le plugin **pslist** pour imprimer une liste de processus sur le terminal.

**`volatility -f memdump.mem --profile=PROFILE pstree`** **//** Utilise le plugin **pstree** pour imprimer une arborescence de processus sur le terminal.

**`volatility`` ``-f memdump.mem --profile=PROFILE psscan`** **//** Utilise le plugin **psscan** pour afficher tous les processus disponibles, y compris les processus cachés souvent utilisés par les malwares (comparez ceci à pslist pour voir s'il y a des différences !).

**`volatility -f memdump.mem --profile=PROFILE psxview`** **//** Utilisez le plugin psxview pour afficher les processus attendus et cachés. Il s'agit d'une combinaison des plugins pslist et psscan.

**`volatility`` ``-f memdump.mem --profile=PROFILE netscan`** **//** Utilisez le plugin **netscan** pour identifier toutes les connexions réseau actives ou fermées.

**`volatility`` ``-f memdump.mem --profile=PROFILE timeliner`** **//** Utilisez le plugin **timeliner** pour créer une chronologie des événements à partir de l'image mémoire.

**`volatility`` ``-f memdump.mem --profile=PROFILE iehistory`** **//** Utilise le plugin **iehistory** pour extraire l'historique de navigation sur internet.

**`volatility -f memdump.mem --profile=PROFILE filescan`** **//** Utilise le plugin **filescan** pour identifier les fichiers présents sur le système à partir de l'image mémoire.

**`volatility -f memdump.mem --profile=PROFILE dumpfiles -n --dump-dir=./`** // Utiliser le plugin **dumpfiles** pour récupérer les fichiers de l'image mémoire. Dans ce cas, notre terminal est ouvert sur le bureau (root@kali:\~/Desktop) et nous utilisons l'emplacement de sortie `./` qui indique à Volatility de placer les fichiers dans notre emplacement actuel, le bureau.
