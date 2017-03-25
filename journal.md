# Journal Di Sviluppo #

### 20 - 03 - 2017 ###

Come prima cosa provo a costruire una matrice di cubi, dapprima di altezza 1 e poi via crescendo. Per questo task provo a creare una prima commit per comprenderne le potenzialità.

La matrice di cubi cresce in altezza formando un edificio in modo non frame indipendent, fornendo un risultato non bello da vedere. Devo fixare questo problema facendo crescere l'edificio ad intervalli regolari, avendo così un miglior impatto visivo.

### 21 - 03 - 2017 ###

Ho infine sistemato la sezione di codice che mi consente di aggiungere elementi ad intervalli più o meno regolari. Tengo un contatore che, avvalendosi del metodo Date.now() (che richiamo anche all'istante di avvio dell'applicazione).Verifico ad ogni frame se dall'avvio dell'applicazione sono passati almeno 200 ms ( è il valore di partenza della variabile che incremento di 200 ogni volta che il test viene superato). Il confronto viene fatto con l'operatore >= poichè può essere che il frame non venga richiamato dopo 200 ms esatti, quindi tecnicamente l'applicazione non è perfettamente sincronizzata, ma a occhio nudo questo problema è impossibile da notare.
A questo punto procedo con l'idea da sviluppare: costruire un castello un livello alla volta.
Tale castello è costituito da una cinta muraria esterna più bassa, una interna alta 2 volte quella esterna e delle torri nel cortile interno, da posizionare in posizioni da decidere in un secondo momento.

L'idea è quella di implementare in un secondo momento le seguenti feature:
- pavimento all'interno del castello;
- Cancello (se possibile con una animazione che lo fa alzare ed abbassare);
- Torri con eventuali feritoie;
- Una merlatura per l'ultimo livello del castello (semplicemente modificando il codice che crea il muro attuale);

### 22 - 03 - 2017 ###
Il tetto sulla torre rende la scena più brutta, lo sostituisco con le merlature già usate per le mura. Ho creato due ingressi nelle mura, facendo in modo che le matrici fino ad una certa altezza contenessero dei buchi nell'intorno di dim_j/2. Ho dovuto "barare" poichè posizionando la merlatura solamente nelle posizioni della matrice pari, per alcune dimensioni della stessa non ottenevo ovviamente alcun merlo.
Ho definito un contenitore globale per traslare ogni componente in alto, così da poter inserire un terreno che fa da basamento alla struttura.
Ho definito inoltre il ponte levatoio per i due ingressi. Probabilmente solamente uno dei due verrà animato, lasciando l'altro chiuso una volta completata la sua costruzione in real time.
Ciascun componente ha un suo contenitore. Questo serve a rendere successive modifiche più agevoli e a consentire future animazioni anche last minute.

### 25 - 03 - 2017 ###
Aggiunta di gate e ponti levatoi con relative animazioni.
Definizione definitiva dello scene graph, per avere una struttura più solida e compatta. Più pivot innestati per creare un sistema di dipendenze coerente.
Riposizionamento della scene camera, per avere una inquadratura iniziale più significativa.
Il bug che non riesco a risolvere è relativo alle ombre. Poichè applico allo stesso modo tale feature per ogni cubo, mi aspetterei lo stesso risultato per ciascuno di loro. Invece inspiegabilmente alcuni cubi proiettano correttamente la loro ombra, mentre la maggior parte di quelli usati non proietta niente.
