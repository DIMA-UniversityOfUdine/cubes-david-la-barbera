# Journal Di Sviluppo #

### 20 - 03 - 2017 ###

Come prima cosa provo a costruire una matrice di cubi, dapprima di altezza 1 e poi via crescendo. Per questo task provo a creare una prima commit per vederne l'utilizzo.

la matrice di cubi cresce in altezza formando un edificio in modo non frame indipendent, fornendo un risultato non bello da vedere

### 21 - 03 - 2017 ###

Ho infine sistemato la sezione di codice che mi consente di aggiungere elementi ad intervalli regolari.
A questo punto procedo con l'idea da sviluppare: costruire un castello un livello alla volta.
Tale castello è costituito da una cinta muraria esterna più bassa, una interna alta 2 volte quella esterna e delle torri nel cortile interno, da posizionare in posizioni da decidere in un secondo momento.

L'idea è quella di implementare in un secondo momento le seguenti feature:
- pavimento in ciottoli all'interno del castello;
- Cancello (se possibile con una animazione che lo fa alzare ed abbassare);
- Torri con eventuali feritoie;
- Una merlatura per l'ultimo livello del castello (semplicemente modificando il codice che crea il muro attuale);

### 22 - 03 - 2017 ###
Il tetto sulla torre rende la scena più brutta, lo sostituisco con le merlature già usate per le mura. Ho creato due ingressi nelle mura, facendo in modo che le matrici fino ad una certa altezza contenessero dei buchi nell'intorno di dim_j/2.
Ho definito un contenitore globale per traslare ogni componente in alto, così da poter inserire un terreno che fa da basamento alla struttura.
Ho definito inoltre il ponte levatoio per i due ingressi. Probabilmente solamente uno dei due verrà animato, lasciando l'altro chiuso una volta completata la sua costruzione in real time.
