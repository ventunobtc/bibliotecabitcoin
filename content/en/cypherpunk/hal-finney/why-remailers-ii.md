---
title: "Why Remailers II"
description: "Hal Finney - 24 Febbraio, 1993"
date: 2023-03-10T03:08:32+01:00
draft: false
weight: 310
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20050122144215/http://finney.org/~hal/why_rem2.html) - 24 Febbraio, 1993

Paul Ferguson chiede:
<blockquote style="font-size:16px">
    Ora, vorrei chiedere ai lettori cypherpunk di chiarire la necessità (o forse un termine migliore potrebbe essere "desiderio") dei remailer anonimi? Forse non sto capendo il "quadro generale", ma mi sembra che la sicurezza delle comunicazioni private sia l'area di interesse qui prevista. So che qualcuno potrebbe affermare ingenua la mia domanda, ma se ti senti abbastanza forte su un argomento, perché non si vorrebbe che il destinatario sapesse chi sei, dove sei e a chi possono rispondere?
</blockquote>

I remailer anonimi offrono diversi vantaggi. Uno dei più semplici e meno controversi è quello di sconfiggere l'analisi del traffico sulle e-mail ordinarie.

Due persone che desiderano comunicare privatamente possono usare PGP o qualche altro sistema di crittografia per nascondere il contenuto dei loro messaggi. Ma il fatto che stiano comunicando tra loro è comunque visibile a molte persone: i sysop dei loro siti e forse anche di quelli intermedi, oltre a vari curiosi della rete. Sarebbe naturale per loro desiderare un'ulteriore livello di privacy che nasconda la persona con cui stanno comunicando e ciò che stanno dicendo.

I remailer anonimi lo rendono possibile. Inoltrando la posta tra di loro attraverso i remailer, pur ancora identificandosi nel contenuto del messaggio (crittografato), hanno una privacy di comunicazione ancora maggiore rispetto alla semplice crittografia.

(La visione Cypherpunk prevede un mondo in cui operano letteralmente centinaia o migliaia di remailer di questo tipo. La posta potrebbe essere fatta rimbalzare attraverso decine di questi servizi, mescolandosi con decine di migliaia di altri messaggi, ricifrati a ogni passaggio. Questo dovrebbe rendere praticamente impossibile l'analisi del traffico. Inviando periodicamente messaggi fittizi che a un certo punto vengono inghiottiti, le persone possono persino nascondere il momento in cui comunicano).

La visione più controversa associata ai remailer anonimi è espressa in storie di fantascienza come "True Names", di Vernor Vinge, o "Ender's Game", di Orson Scott Card. Questi racconti descrivono mondi in cui le reti informatiche sono ampiamente diffuse, ma in cui molte persone scelgono di partecipare attraverso pseudonimi. In questo modo, possono sostenere argomenti impopolari o partecipare a transazioni non gradite senza che le loro attività siano collegate alla loro vera identità. Ciò permette anche alle persone di sviluppare una reputazione basata sulla qualità delle loro idee, piuttosto che sul loro lavoro, ricchezza, età o status.

L'idea è che la soluzione definitiva al basso rapporto segnale/rumore delle reti non consiste nel costringere le persone a "sostenere le proprie parole". Le persone possono sostenere ogni tipo di idea idiota. Piuttosto, sarà necessario sviluppare sistemi migliori per filtrare le notizie e la posta, per sviluppare "reputazioni digitali" che possano essere impresse sui propri post per passare attraverso questi filtri intelligenti, e persino applicare queste reputazioni agli pseudonimi. In un sistema di questo tipo, il fatto che qualcuno pubblichi o spedisca messaggi di posta elettronica in forma pseudonima non è un problema, poiché i post fastidiosi non saranno in grado di passare.

Altri vantaggi di questo approccio sono l'estensione alle transazioni elettroniche on-line. Già oggi vengono conservate molti registri delle nostre transazioni finanziarie: ogni volta che acquistiamo un articolo al telefono utilizzando una carta di credito, questo viene registrato dalla società che gestisce la carta di credito. Col tempo, un numero ancora maggiore di questo tipo di informazioni potrebbe essere raccolto ed eventualmente venduto. Una visione Cypherpunk prevede la possibilità di effettuare transazioni in modo anonimo, utilizzando "contanti digitali", che non sarebbero riconducibili ai partecipanti. In particolare, per l'acquisto di prodotti "soft", come musica, video e software (che potrebbero essere consegnati in rete), dovrebbe essere possibile effettuare tali transazioni in modo anonimo. Questo è un altro settore in cui la posta anonima è importante.

Prevediamo che le reti informatiche giocheranno un ruolo sempre più importante in molte parti della nostra vita. Ma questa crescente informatizzazione comporta enormi pericoli di violazione della privacy. I Cypherpunk cercano di mettere in atto strutture che permettano alle persone di preservare la propria privacy, se lo desiderano. Nessuno sarà costretto a usare pseudonimi o a postare in modo anonimo. Ma dovrebbe essere una questione di scelta la quantità di informazioni che una persona decide di rivelare su di sé quando comunica. Al momento, le reti non danno questa possibilità di scelta. Stiamo cercando di dare questo potere alle persone.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](/cypherpunk/hal-finney/hal-finney-home-page)
