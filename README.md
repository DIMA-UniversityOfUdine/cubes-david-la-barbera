# Descrizione Introduttiva

Per questo progetto ho deciso di creare una scena seguendo delle idee ben precise. Ho pensato di creare una applicazione che, nell'arco di una ventina di secondi costruisca un pezzo alla volta un castello composto da mattoncini. L'idea è quella di emulare la costruzione di un edificio con il lego in maniera progressiva con la scena che acquisisce senso ed elementi con il passare del tempo sotto agli occhi dell'utente. La scena come già detto viene costruita per livelli, questo perchè ho utlizzato per la struttura globale del castello solamente box di dimensioni 1x1x1, così da rendere la crescita omogenea in termini di tempo e di altezza.
Per la realizzazione del progetto ho usato pochi file esterni, solamente tre texture per la pietra, il legno e la base d'erba.
 - La texture per la pietra è stata ottenuta da [Minecraft Texture Pack](http://www.minecrafttexturepacks.com/), un sito web che fornisce texture gratuite da utilizzare come mod sostitutive per quelle originariamente presenti nel gioco, fornendo texture in HD e generalmente diverse da quelle standard. Tale texture è stata applicata ad ogni cubo che fa parte del castello.
 - La texture per il legno a sua volta fa parte dello stesso pack della precedente. Questa texture è stata applicata ai cubetti che compongono i ponti levatoi e ai parallelepipedi che invece sono stati istanziati per le porte ed il pavimento della sommità della torra.
 - Essendo il cubo usato come base molto più largo rispetto agli altri, ho optato per una texture con risoluzione maggiore rispetto a quelle presenti nel pack precendente. Tale texture è stata ottenuta dal sito web [goodtextures](http://goodtextures.deviantart.com/art/Seamless-Green-Grass-Texture-01-271356478) , ed è senza licenza e quindi gratuitamente utilizzabile.

# Risultati

Al fine di meglio spiegare la struttura e quindi la logica dell'applicazione sviluppata, ho creato una sintesi globale dello scenegraph costruito.

![Scenegraph Prodotto](https://github.com/DIMA-UniversityOfUdine/cubes-david-la-barbera/blob/master/images/scenegraph.jpg?raw=true)

Come si può vedere ho usato una semplice struttura definendo un pivot globale (**contenitore_castello_globale**) che mi consente in caso di aggiunte future di agire sulla struttura nella sua interezza. In sintesi ciascun pivot contiene:
- **contenitore_ponte1** e **contenitore_ponte2** contengono le matrici di cubi 1x1x1 che compongono i ponti di accesso alla struttura. Tali cubi si sviluppano in altezza per formare un ponte levatoio alzato ma, durante la costruzione del castello i due contenitori subiscono una rotazione attorno al proprio asse z globalmente di 90 gradi, per aprire il ponte levatoio. Ho implementato volutamente due container distinti tenendo sempre a mente l'eventualità di modifiche successive.
-  **contenitore_gate_1** e **contenitore_gate_2** contengono ciascuno un parallelepipedo che costituisce la porta di accesso ad un lato del castello. Tale porta viene visualizzata solo quando le mura sono state costruite nella loro interezza e, una volta costruito completamente il castello, traslano rispettivamente lungo -z e +z per aprirsi e consentire l'accesso. Per ragioni estetiche e per rompere un poco la monotonia creata dalla presenza di sole matrici di cubi della stessa dimensione ho creato una geometria unica per questi due elementi.
- **contenitore_muro_esterno** e **contenitore_muro_interno** sono composti entrambi da una matrice i cui bordi contengono cubi 1x1x1. Sfruttando il metodo Render tali matrici vengono posizionate una sopra l'altra fino ad altezze predefinite andando a costruire le due cinti murarie. Nell'ultimo livello ho istanziato una matrice di cubi posizionati nei bordi in posizioni pari, così da avere una merlatura e rendere il tutto esteticamente più attraente.
- **contenitore_torre** contiene matrici di cubi come al punto precedente infine contiene un parallelepipedo che crea un pavimento nella sua sommità.
- **contenitore_terreno** contiene un parallelepipedo usato per posizionare la struttura creata su qualcosa di più solido rispetto al ground già presente.

![Risultato in Costruzione](https://github.com/DIMA-UniversityOfUdine/cubes-david-la-barbera/blob/master/images/risultato_in_costruzione.png?raw=true)

Come si può vedere nella figura sopra, pochi secondi dopo aver inizializzato l'applicazione i livelli di matrici hanno iniziato a posarsi ad altezza crescente uno sopra l'altro. Si distinguono chiaramente le due cinte murarie, la torre e si può vedere come l'animazione che apre i cancelli sia già stata avviata.

![Risultato con Porte Chiuse](https://github.com/DIMA-UniversityOfUdine/cubes-david-la-barbera/blob/master/images/risultato_porte_chiuse.png?raw=true)

A questo punto le mura e la torre sono state costruite e si vede le due porte bloccare l'accesso al castello, posizionate nella loro configurazione iniziale.

![Risultato Finale](https://github.com/DIMA-UniversityOfUdine/cubes-david-la-barbera/blob/master/images/risultato_finale.png?raw=true)

Come si può vedere in figura infine, la struttura finale del castello prevede che le porte si aprano traslando, restituendo il castello nella sua configurazione finale.

# Considerazioni

Prima di costruire la scena ho lavorato con Unity per avere una idea a grandi linee del risultato voluto. Su Unity non ho implementato il risultato completo ma questa fase introduttiva mi è servita a sviluppare l'idea di crescita incrementale verso l'alto che ho poi implementato in three.js.
Dopo questa breve fase sono passato allo sviluppo su three.js implementando le prime funzioni che mi consentissero di costruire la scena per livelli. In generale non mi sono servito di alcun tool o assets, gli unici elementi esterni che la scena include sono le texture utilizzate.

Ho preferito implementare delle animazioni sensate nel contesto che ho voluto ideare, facendo in modo che esse vengano avviate automaticamente in momenti ben precisi durante l'esecuzione della scena e prevedendo un inizio ed una fine delimitati da vincoli logici e di buon senso inerenti al contesto. La scena costruita è quinda da intendersi come una prima fase di una esperienza più vasta da espandere dopo la scadenza della deadline:
- Il castello è composto prevalentemente da cubi di dimensioni 1x1x1 e questa è una scelta fortemente voluta poichè mi piacerebbe implementare in un secondo momento delle funzionalità che consentono la sua distruzione, con ciascun mattoncino che subisce l'applicazione di forze fisiche o impatti. Pertanto ho scelto di realizzare la struttura composta da mattoncini singoli di dimensioni regolari ottenendo tra l'altro un effetto grafico più appagante.
- Ciascuna animazione potrebbe venir istanziata separatamente.
- Potrebbe essere interessante prevedere una modalità di navigazione della scena più immersiva.

David La Barbera
