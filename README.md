README - Sistema d'Alertes d'Emergència
=======================================

Descripció general
------------------
El Sistema d'Alertes d'Emergència és una aplicació per a Windows dissenyada per enviar i rebre alertes crítiques entre diversos dispositius d'una mateixa xarxa. Està pensada per a entorns on es necessita una resposta ràpida davant situacions de risc.

El sistema funciona en segon pla i només mostra una finestra quan:
- L'usuari envia una alerta (contador discret)
- Un altre dispositiu rep una alerta (pantalla vermella a pantalla completa)

Funcions principals
-------------------

1) Enviament d'alertes
----------------------
Quan l'usuari prem la hotkey configurada (per defecte: Ctrl + Alt + F12), s'obre una finestra petita amb un comptador.

- El comptador NO està en primer pla
- L'usuari pot cancel·lar l'enviament
- Si el temps s'esgota, l'alerta s'envia automàticament

2) Enviament seqüencial a múltiples dispositius
------------------------------------------------
El sistema envia l'alerta a les IP configurades en ordre:

1. Envia a la primera IP
2. Espera 30 segons
3. Si no premen "REBUT", envia a la següent
4. Continua fins que algun dispositiu confirmi

Això garanteix que sempre hi hagi una resposta.

3) Recepció d'alertes
---------------------
Quan un dispositiu rep una alerta:

- S'obre una pantalla vermella a pantalla completa
- Sempre queda al davant de totes les finestres
- No es pot minimitzar ni amagar
- Mostra:
  - Nom d'usuari de Windows del dispositiu emissor
  - Nom de la màquina del dispositiu emissor
- Només desapareix quan es prem "REBUT"

4) Configuració centralitzada
------------------------------
Mitjançant Config.exe, l'usuari pot configurar:

- Temps del compte enrere
- Hotkey d'activació
- Llista d'IPs destinatàries

El fitxer config.json es genera automàticament i manté una estructura simple.

5) Funcionament en segon pla
-----------------------------
L'aplicació:

- S'executa a la safata del sistema
- No molesta l'usuari
- Només mostra finestres quan és necessari
- Manté un servidor intern per rebre alertes

Fitxers principals
------------------

Alerta.exe
- Programa principal
- Envia i rep alertes
- Mostra la pantalla vermella
- Gestiona la hotkey
- S'executa en segon pla

Config.exe
- Editor gràfic de configuració
- Guarda els paràmetres a config.json

config.json
Exemple:

{
    "destinos": ["192.168.1.20", "192.168.1.21"],
    "hotkey": "ctrl+alt+f12",
    "countdown": 15
}

Seguretat i privacitat
----------------------
El sistema:
- No envia dades fora de la xarxa local
- No guarda informació personal
- Només transmet:
  - Nom d'usuari de Windows
  - Nom de la màquina
- No requereix Internet
- No utilitza serveis externs

AVÍS IMPORTANT — Limitació de responsabilitat
---------------------------------------------
En instal·lar i utilitzar aquesta aplicació, l'usuari accepta expressament
les condicions següents:

El desenvolupador NO es fa responsable de cap filtratge, exposició o
accés no autoritzat a dades generades o transmeses per aquesta aplicació,
incloent-hi, sense limitació: noms d'usuari, noms de màquina, adreces IP,
o qualsevol altra informació present al fitxer config.json o als registres
de l'aplicació.

La seguretat de la xarxa local, dels dispositius i de la configuració del
sistema és responsabilitat exclusiva de l'usuari o administrador que
instal·la l'aplicació.

L'ús d'aquesta aplicació implica l'acceptació íntegra d'aquesta limitació
de responsabilitat. Si no esteu d'acord, desinstal·leu l'aplicació
immediatament.

Requisits
---------
- Windows 10 o superior
- Xarxa local amb IPs accessibles
- Port 5005 obert per comunicació interna

Copyright
---------
© 2026 Kimi. Tots els drets reservats.

Aquest programari és propietat exclusiva del seu autor.
No es permet copiar, modificar, distribuir o utilitzar aquest programari
amb finalitats comercials sense autorització expressa i per escrit.

Suport
------
Per millores, errors o noves funcions, contacta amb el desenvolupador original.
