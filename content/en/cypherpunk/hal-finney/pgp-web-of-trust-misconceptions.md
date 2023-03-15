---
title: "PGP Web of Trust Misconceptions"
description: "Hal Finney - 30 Marzo, 1994"
date: 2023-03-10T03:03:33+01:00
draft: false
weight: 375
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206213359/http://finney.org/~hal/web_of_trust.html) - 30 Marzo, 1994

Uno dei concetti chiave ampiamente utilizzati per descrivere PGP è la "rete di fiducia". Questo concetto richiama alla mente una rete di connessioni tra persone che si conoscono e comunicano tra loro. Due persone che vogliono comunicare possono farlo in modo sicuro se esiste un percorso di connessioni sotto forma di chiavi firmate che le unisce.

Ma questo non è del tutto corretto. Il fatto fondamentale delle firme delle chiavi PGP, che spesso viene frainteso, è questo:

Si può comunicare in modo sicuro solo con qualcuno la cui chiave è firmata da una persona che si conosce, personalmente o per reputazione.

In altre parole, se voglio comunicare con joe@abc.com, posso farlo solo se uno dei firmatari della sua chiave è una persona che conosco. In caso contrario, non ho modo di giudicare la validità della sua chiave.

Ciò smentisce le semplici interpretazioni della "rete di fiducia". Posso aver firmato la chiave di A, A ha firmato quella di B, B ha firmato quella di C, C ha firmato quella di D e D ha firmato quella di Joe, ma questo non ha alcun valore se non conosco D. Solo allora posso fidarmi della chiave di Joe.

Ciò significa che, nell'immagine della "rete", posso comunicare in modo sicuro solo con persone che si trovano al massimo a due hop di distanza nella rete di connessioni. Posso comunicare con le persone che conosco, e posso comunicare con le persone che loro conoscono, ed è tutto.

Questo è un peccato, perché il modello di rete semplice si ricollega a una famosa ricerca che suggerisce che due persone scelte a caso sono distanti solo una mezza dozzina di passi nella rete di connessioni tra chi sa chi. (Da questo risultato deriva il titolo del film "Sei gradi di separazione"). Se si disponesse di un sistema che supportasse effettivamente le comunicazioni attraverso un tale modello di rete, si potrebbe sperare di far comunicare due persone che non hanno una catena molto lunga tra loro. Ma PGP, con una catena di lunghezza massima di due, non lo permette.

Cosa bisognerebbe aggiungere per consentire l'uso di un vero modello di rete di fiducia in un programma come PGP? Fondamentalmente è necessario un modo per giudicare l'attendibilità delle firme di persone che non si conoscono. Questo sarebbe plausibilmente fornito dalle persone che hanno firmato le loro chiavi. Ad esempio, se esistesse un altro tipo di firma che non solo garantisse l'identità della persona, ma anche la sua affidabilità e la sua cura nel firmare le chiavi, allora una catena di firme di questo tipo potrebbe servire come base per una vera rete di fiducia. Ovviamente tali firme non potrebbero essere distribuite con la stessa facilità di quelle attuali, dove spesso basta dare un'occhiata alla patente di uno sconosciuto, ma potrebbero essere fornite agli amici più stretti e a coloro che conosciamo e di cui ci fidiamo.

Sistemi più elaborati potrebbero includere valutazioni numeriche di affidabilità che aiuterebbero a stimare la forza di un determinato percorso. Il punto principale è che alcune informazioni di questo tipo sarebbero necessarie per consentire la comunicazione con persone distanti nella rete di connessioni.

Senza questo, credo che continueremo ad avere problemi con PGP che non è in grado di convalidare le chiavi delle persone con cui vogliamo comunicare. Le persone raccoglieranno enormi liste di firme nella speranza che chiunque voglia comunicare con loro conosca una di quelle persone. Appariranno validatori di chiavi centralizzati (come nel caso del servizio SLED in fase di avvio, che firmerà una chiave sulla base di un assegno firmato con il vostro nome). Il risultato potrebbe essere la scelta tra l'utilizzo di una chiave non firmata o di una firmata da una burocrazia senza volto, il che non è meglio della concezione originale PEM.

(Le persone potrebbero essere confuse da questo saggio perché pensavano che PGP funzionasse già in questo modo. PGP ha un modello "follow-the-web", ma solo per seguire le firme. Nell'esempio precedente, in cui volevo parlare con Joe e c'era una catena che portava a lui attraverso A, B, C e D, dobbiamo prima supporre che io conosca e mi fidi di tutti gli A, B, C e D. Dato questo, ciò che PGP può fare è determinare se ho chiavi valide per tutte queste persone. Noterà che A ha firmato la chiave di B, quindi è valida. Conosco B e ho detto a PGP che è affidabile, e ha firmato la chiave di C, quindi è valida. Allo stesso modo, conosco C e conosco D, quindi PGP può seguire la catena attraverso loro. Infine arriviamo a Joe, che non conosco, ma poiché conosco D e PGP ha seguito la rete per determinare che la chiave di D è valida, PGP può determinare che la chiave di Joe è valida. Ma ancora una volta, questo era solo perché conoscevo D e tutti gli altri nella catena. Il punto fondamentale è che posso comunicare solo con persone che conoscono qualcuno che conosco).

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](hal-finney-home-page.md)
