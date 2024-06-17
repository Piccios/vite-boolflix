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
        - tramite npm installo language icons
        
    2. In MovieItem aggiungo un'img che prenda la lingua di provenienza dall'array di dati rilasciato dall'API

    3. nei metodi creo una funzione per cogliere dall'API la lingua originale del film o serie tv

Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di risposta diversi, simili ma non sempre identici)
Qui un esempio di chiamata per le serie tv:
https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=scrubs


Milestone 3:
In questa milestone come prima cosa aggiungiamo la copertina del film o della serie al nostro elenco. Ci viene passata dall’API solo la parte finale dell’URL, questo perché poi potremo generare da quella porzione di URL tante dimensioni diverse. Dovremo prendere quindi l’URL base delle immagini di TMDB: https://image.tmdb.org/t/p/ per poi aggiungere la dimensione che vogliamo generare (troviamo tutte le dimensioni possibili a questo link: https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400) per poi aggiungere la parte finale dell’URL passata dall’API.
Esempio di URL:
https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png

Trasformiamo poi il voto da 1 a 10 decimale in un numero intero da 1 a 5, così da permetterci di stampare a schermo un numero di stelle piene che vanno da 1 a 5, lasciando le restanti vuote (troviamo le icone in FontAwesome).
Arrotondiamo sempre per eccesso all’unità successiva, non gestiamo icone mezze piene (o mezze vuote :P)

Milestone 4:
Trasformiamo quello che abbiamo fatto fino ad ora in una vera e propria webapp, creando un layout completo simil-Netflix:
Un header che contiene logo e search bar
Dopo aver ricercato qualcosa nella searchbar, i risultati appaiono sotto forma di “card” in cui lo sfondo è rappresentato dall’immagine di copertina (consiglio la poster_path con w342)
Andando con il mouse sopra una card (on hover), appaiono le informazioni aggiuntive già prese nei punti precedenti più la overview
