---
title: "The Beauty of ECash"
description: "Hal Finney - 16 Marzo, 1994"
date: 2023-03-10T03:06:45+01:00
draft: false
weight: 365
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206185841/http://finney.org/~hal/beauty_ecash.html) - 16 Marzo, 1994

Mi viene in mente che il denaro digitale potrebbe diventare un oggetto da collezione. La cartamoneta è ampiamente collezionata, così come le monete. Ho preso un libro in biblioteca sulla vecchia cartamoneta americana e molte delle vecchie banconote sono di una bellezza sorprendente. È interessante notare che la vecchia moneta ha ancora corso legale, quindi il valore delle banconote collezionate è inferiore.

Fino al 1861, gli Stati Uniti non emettevano cartamoneta, ma solo monete. A quei tempi, la cartamoneta era emessa da banche private (di solito con statuto statale). Il denaro era sostenuto da dollari, monete, che la banca possedeva. Sfortunatamente, il capitalismo è un sistema dinamico e a quei tempi i fallimenti delle banche non erano più insoliti di quanto lo siano oggi i fallimenti delle aziende. Quando ciò accadeva, le banconote della banca diventavano prive di valore. Anche la contraffazione era un grosso problema con le migliaia di diverse banche che emettevano banconote. È interessante ipotizzare che il contante digitale possa portare a un sistema elettronico simile a quello di un tempo.

Il collezionismo del contante digitale presenta alcuni problemi. I collezionisti sono generalmente attratti da oggetti belli, interessanti e rari. Il contante digitale è abbastanza interessante, ma la sua bellezza è piuttosto astratta. Anche la rarità è difficile da valutare; ogni singola banconota ha un numero di serie unico e ciò che ha in comune con le altre banconote del suo taglio è la chiave bancaria e l'esponente. Le banconote non circolate sono generalmente più preziose delle altre nel mondo cartaceo; con le banconote digitali, l'unico modo per sapere se sono state "circolate" sarebbe quello di avere accesso al database delle banconote esaurite della banca, per verificare che la banconota non sia mai stata depositata.

La rarità potrebbe essere determinata dalla chiave e dall'esponente della banca. Il sistema Magic Money prevede che la banca passi periodicamente a un'altra serie di esponenti per rappresentare gli stessi tagli (per evitare che il database delle banconote diventi troppo grande). Se le banche facessero questa operazione a intervalli regolari, allora soprattutto le prime emissioni sarebbero relativamente rare. Si potrebbe persino far autenticare una prima banconota (con timbro digitale) per poterne dimostrare il valore negli anni successivi.

La bellezza è più difficile da gestire. Rigorosamente parlando, il contante digitale è invisibile, consistendo solo in uno schema di informazioni nei chip RAM o su un disco. I numeri che rappresentano il contante possono però essere stampati, e questa rappresentazione potrebbe forse avere una certa bellezza. Sfortunatamente, a mio parere, diverse righe di cifre esadecimali casuali non sono belle.

Ho lavorato a delle idee per visualizzare le informazioni del contante digitale in qualche altro modo che sia più estetico. Sarebbe bello se la visualizzazione funzionasse in qualche modo solo per le banconote firmate correttamente, mentre i contanti contraffatti non mostrerebbero nulla di bello. La mia idea generale è quella di visualizzare un'"impronta digitale" di ogni singola banconota, qualcosa che sia unico per quella banconota e che abbia una sorta di bellezza.

Un'idea su cui ho lavorato è quella di selezionare un automa cellulare 1-D con un modello di bit basato sul contante digitale. Questo nodo viene poi elaborato dall'algoritmo di CA per produrre un modello, in cui ogni riga è una funzione della riga precedente. Ho pensato di avviare la CA in cima e in fondo allo schermo con le due diverse funzioni applicate al contante che dovrebbero essere uguali se il contante è valido (portando il numero all'esponente corretto da un lato e applicando l'hash MD5 del numero di serie dall'altro, per il caso del denaro magico). Poi lavoriamo verso l'interno con i due nodi. Il denaro corretto produrrà un modello simmetrico. Scegliendo buone regole di CA, i modelli saranno diversi per ogni banconota, alcuni più belli di altri, portando a modelli attraenti dall'aspetto frattale per molte banconote. Quando si vuole "guardare i propri soldi", si può eseguire il programma sul contante digitale. Le persone potrebbero anche fare scambi per banconote particolarmente attraenti.

Un'idea simile è quella di utilizzare il contante come base per un algoritmo frattale. Molti frattali hanno la proprietà che la maggior parte del piano è semplice, mentre solo una frazione sembra davvero frattale. Il contante digitale ha la proprietà che, se esponenziato, porta a un numero la cui maggior parte dei bit è fissa, ma che ha un piccolo numero di bit variabili. Se avessimo una mappatura che porta i bit fissi del contante digitale sulle parti interessanti del frattale, allora il contante falso non produrrebbe immagini carine, mentre il contante vero produrrebbe una parte di un bellissimo frattale. Anche in questo caso, la convalida e la bellezza sarebbero legate tra loro.

Ho fatto alcuni esperimenti con la prima idea, sperando di produrre qualcosa di bello. Con un po' più di riflessione spero di riuscire a creare un visualizzatore per il vostro Magic Money che ne faccia risaltare la naturale bellezza e rarità. Sarà un must per tutti i collezionisti seri di digicash.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](/cypherpunk/hal-finney/hal-finney-home-page)
