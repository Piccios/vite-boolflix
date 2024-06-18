1. Configuro il componente principale:
    - creo un metodo per l'invio della richiesta tramite axios all'indirizzo https://api.themoviedb.org/3/search/movie
    -nei parametri inserisco:
        - API key: 62e3cbd4b6904ca7307e4b3b03e03a2a
        - il tipo di richiesta: query
        - la lingua: it-IT

2. Creo il componente per la searchbar
    - creo un metodo per la ricerca sfruttando $emit

3. Creo il componente 'MovieCard' che conterra' le info che il db ci avra' consegnato come risultato della ricerca

4. Creo il componente 'MovieList' che conterra' la lista dei film trovati


Milestone 1:
    1. creo nel componente SearchBar.vue un input e un bottone con il quale l'utente potra' interagire per la ricerca:
        - tramite il metodo search, sfruttando l'$emit invio la richiesta tramite l'input al database

    2. nel componente MovieItem tramite i props movie riporto i dati nell'HTML: 
        - Titolo
        - Titolo originale
        - Lingua originale
        - Valutazione media


Milestone 2:
    1. L'API mi rende la lingua originale del film e serie tv
        - tramite npm installo flag icons
        
    2. In MovieItem aggiungo un'img che prenda la lingua di provenienza dall'array di dati rilasciato dall'API

    3. nei metodi creo una funzione per cogliere dall'API la lingua originale del film o serie tv

    4. Aggiorno il componente Vue per gestire due chiamate API per ricevere anche le serie TV oltre ai film

    5. Unifico i risultati in un formato coerente.

    6. Modifico il template per visualizzare i risultati combinati.


Milestone 3:    
    1. Aggiungo l'URL base delle immagini e la dimensione desiderata:
        - L'url base e'  https://image.tmdb.org/t/p/  
        - Scelgo la dimensione con la width: es. w350
        - aggiungo la parte finale dell'URL passata dall'API
    
    1.2 Modifico `MediaItem.vue` per includere l'immagine

    2. Modifico il voto numerico fornito dal db in un voto da 1 a 5

    2.1 Tramite FontAwesome utilizzo le icone delle stelle per rappresentare il voto

Milestone 4:
    1. Elaboro il layout e lo stile della web app
    2. Creo un layout completo simil-Netflix:
        - Un header che contiene logo e search bar

    3. Dopo aver ricercato qualcosa nella searchbar, i risultati appaiono sotto forma di “card” in cui lo sfondo è rappresentato dall’immagine di copertina

    4. Andando con il mouse sopra una card (on hover), appaiono le informazioni aggiuntive già prese nei punti precedenti più la overview

