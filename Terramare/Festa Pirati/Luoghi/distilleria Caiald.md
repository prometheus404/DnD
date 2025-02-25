Formata da quattro zone fondamentali:
- [[distilleria Caiald#Portico|portico]] fuori dal quale i giocatori faranno conoscenza con [[Caio Barrelman]]
- [[distilleria Caiald#negozio|negozio]] prima parte della distilleria subito dopo l'ingresso
- [[distilleria Caiald#laboratorio|laboratorio]] in cui viene distillato e imbottigliato il rhum
- [[distilleria Caiald#Laboratorio abbandonato|laboratorio abbandonato]] che viene usato come sistema di protezione per il la cassaforte contenente i rum pregiati.
I laboratori sono seminterrati e sopra di essi c'è la casa di Caio.
# Portico
>[!warning]
>ricordati di dire:
>"ricordo che mio figlio aveva detto che gli elementi per ricordare la password saranno tutti **letteralmente** nella stanza"

Nonappena i giocatori raggiungono la distilleria notano, subito dopo l'enorme insegna con scritto "distilleria Caiald", un piccolo portico dove ,su una sedia a dondolo, sonnecchia un vecchio.
Se lo svegliano direttamente o in seguito al suono della campanella della porta d'ingresso del negozio, questo si presenterà loro come [[Caio Barrelman]], proprietario della distilleria. Una volta che i giocatori gli diranno di essere stati mandati da [[Amanda Steel-heart]] per prendere le botti della festa smetterà di parlare a ruota libera e li condurrà nel negozio
# Negozio
![[negozio_caiald.jpg]]
La parte del negozio è abbastanza piccola, ogni muro è coperto da scaffali che arrivano fino al soffitto colmi di bottiglie di vetro ripiene di liquidi di varie sfumature di colori che vanno dal trasparente al marrone scuro.
Caio conduce i giocatori dietro al bancone, apre una botola e fa cenno di seguirlo mentre si dirige nel seminterrato tramite una piccola scala a chiocciola.
# Laboratorio
```leaflet
id: leaflet-map
image: [[laboratorio.png]]
height: 500px
lat: 50
long: 50
minZoom: 12
maxZoom: 16
defaultZoom: 5
zoomDelta: 0.5
unit: meters
scale: 100
darkMode: false

```

Scesa una scalinata a chiocciola dietro al bancone del negozio si arriva nel laboratorio seminterrato.
È una stanza lunga una decina di metri, con quattro aperture di due metri ciascuna separate da muri abbastanza spessi e ripieni di botti di rum.
Una fioca luce penetra in fasci dalle piccole finestre poste nella parte superiore delle aperture e sui muri che le separano sono accese delle lampade a olio che illuminano la stanza.
sulla parte destra della stanza sono presenti altrettante aperture con degli alambicchi enormi per distillare il rum.
In fondo alla stanza un portone in legno porta al laboratorio abbandonato. Caio fa entrare i giocatori nella stanza e chiude loro la porta alle spalle per una questione di sicurezza (la sua ovviamente)
# Laboratorio abbandonato
Stessa struttura della stanza precedente ma nessuna botte né attrezzi per distillare.
Le lampade a olio sono spente e l'unica luce proviene dalle finestrelle in alto.


Appena entrati i giocatori sono accolti da un forte odore di sangue e possono facilmente notare due **cadaveri** in fondo alla stanza: uno è il cadavere dell'altra persona che stava cercando di prendere le botti.
Il **secondo corpo** è solo apparentemente morto, ma può essere rianimato e inizierà a fare parte della squadra. Ha con sé una fiala per curarsi.

Per terra c'è dell'acqua che sembra provenire dalla prima apertura.
Quando si avvicinano vedono solo tre armature.
Se ispezionano le armature possono notare che la spada di quella più in fondo è sporca di sangue, ma proprio mentre se ne rendono conto l'armatura cerca di colpire la persona che sta indagando. Si tratta di [[armatura animata|armature animate]].
In caso invece non ci facciano troppo caso e proseguano, l'armatura colpirà alle spalle la persona più vicina di quelle che si trovano in fondo al gruppo.


Una volta sconfitta i giocatori possono esplorare in tranquillità la stanza. Quello che notano è che nelle altre nicchie sono presenti altri mostri intrappolati in enormi blocchi di ghiaccio. In ordine di nicchia:
- una lumaca mazzafrusto
- un diavolo
- un ogre trebbiatore

Questi sono gli unici elementi presenti con i quali i giocatori dovranno tentare di risolvere l'enigma della [[password dimenticata]]. Ogni tentativo fallimentare di indovinare la password libererà il mostro successivo.

Ricordare ai giocatori che il tastierino valuta solo le ruote che sono state cambiate e solo dopo che il giocatore che le ha mosse toglie la mano dal quadrante. Hanno tempo di cambiare la propria risposta finché rimangono con le mani sul quadrante.



```encounter
name: armatura
creatures:
  - 3: Animated Armor
---
name: lumaca
creatures:
  - Flail Snail
---
name: diavolo
creatures:
  - Spined Devil
---
name: ogre
creatures:
  - Ogre Battering Ram
```

In caso anche l'ogre venga liberato, questo procederà all'abbattimento del muro dove si trovava la ruota e successivamente caricherà i giocatori.

In teoria l'ogre dovrebbe essere un livello di difficoltà adeguato per i giocatori, ma nel caso questi siano stremati dai combattimenti precedenti e finiscano per essere sconfitti, Caio cercherà di aiutare i giocatori aprendo la porta. In questo modo però l'ogre vedrà l'opportunità di scappare e, dopo averlo travolto con una carica, lascerà il corpo del vecchio senza vita e si dileguerà nella campagna vicina. In questo secondo caso [[Aldo Barrelman]] sarà attivamente ostile nei confronti dei giocatori.

In ogni caso i giocatori otterranno le loro botti e torneranno da [[Amanda Steel-heart]] per la seconda parte della [[Festa di pirati]]