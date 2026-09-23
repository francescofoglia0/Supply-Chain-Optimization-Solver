
# Descrizione

Siete stati incaricati dalla nota azienda avicola *Polli Tech di N.I. &
Co.* di progettare una catena di distribuzione per la
commercializzazione dei suoi prodotti. In particolare, l'azienda vi
richiede di trovare il piazzamento ottimale (tra un insieme possibile di
posizioni) di magazzini per le merci, i quali hanno lo scopo di
distribuire i propri prodotti ai supermercati circostanti.

Ogni magazzino ha un costo di costruzione ed è in grado di servire un
certo sottoinsieme di supermercati. Ogni supermercato non servito da
nessun magazzino costituisce una perdita economica per l'azienda.
Infine, il piazzamento dei magazzini deve tenere conto del costo di
trasporto delle merci dall'azienda ai magazzini stessi, che viene
effettuato con un unico mezzo che parte dall'azienda, visita ogni
magazzino e ritorna all'azienda ogni giorno.

# Dati

Ogni istanza del problema è composta dai seguenti files:

-   `weights.json`: contiene i costi che l'azienda può sostenere, che
    sono:

    -   `’construction’`: costo giornaliero dovuto alla costruzione e
        alla manutenzione di un magazzino (immaginiamo che la
        costruzione non sia pagata una tantum ma sia ammortizzata nel
        tempo)

    -   `’missed_supermarket’`: penalità giornaliera per un supermercato
        non servito da nessun magazzino

    -   `’travel’`: costo del carburante per ciascun chilometro di
        distanza percorso

-   `service.csv`: matrice in cui ogni riga si riferisce a una possibile
    posizione dei magazzini e ogni colonna a un supermercato. Se un
    magazzino può servire un certo supermercato l'elemento della matrice
    corrispondente è pari a 1, 0 altrimenti.

-   `distances.csv`: matrice delle distanze tra le possibili posizioni
    dei magazzini e tra le possibili posizioni dei magazzini e
    l'azienda. Sia sulle colonne che sulle righe, il primo elemento fa
    riferimento all'azienda, mentre gli altri ai magazzini, nello stesso
    ordine in cui si trovano in `service.csv`. Ciascun elemento della
    matrice (che non è necessariamente simmetrica) rappresenta la
    distanza in chilometri dal luogo sulla riga al luogo sulla colonna.

# Richiesta

Utilizzando **python** come linguaggio di programmazione e **GUROBI**
come solver, si sviluppi un modello di programmazione lineare per
risolvere il problema.



# Deadline

Il progetto deve essere consegnato tramite la sezione **Elaborati** del
Portale della didattica (uno solo per gruppo) entro le 23:59 del giorno
30/06/2025.
