---
title: "Down with Observers!"
description: "Hal Finney - 2 Agosto, 1993"
date: 2023-03-10T02:57:40+01:00
draft: false
weight: 315
images: []
categories: []
contributors: ["cyphersats"]
---

[Orinale](https://web.archive.org/web/20041206185232/http://finney.org/~hal/anti_observers.html) - 2 Agosto, 1993

Molte delle nostre discussioni sono influenzate dalle idee di David Chaum. Lui è stato il pioniere di una tecnologia in grado di proteggere la privacy individuale pur consentendo tipi molto flessibili di credenziali e garanzie. Ha anche svolto un ruolo importante nelle varie proposte per il contante digitale.

Ma credo che negli ultimi anni Chaum abbia preso la direzione sbagliata. Si sta concentrando sempre più su protocolli che si basano su un'implementazione hardware a prova di manomissione di un protocollo crittografico che lui chiama "observer". Questo observer chip si troverebbe nel vostro computer (che potrebbe essere un PDA in stile Newton o una smart card) e svolgerebbe un ruolo importante negli scambi d'informazioni, denaro o credenziali che fareste con altri. In pratica, l'observer si assicura che l'utente stia dicendo la verità nelle sue transazioni, che non stia spendendo due volte il suo contante digitale o che non stia rivendicando una credenziale che non possiede.

Ora questo approccio ha l'ovvio vantaggio di risolvere alcuni problemi che non possono essere risolti altrimenti. Ad esempio, non sembra esserci modo di fornire un contante digitale sicuro e off-line, se non con qualcosa di simile a un observer.

Ma ha il problema altrettanto ovvio di affidarsi a un chip a prova di manomissione come parte necessaria del protocollo. Recentemente sembra che molti dei lavori del suo gruppo siano stati concepiti per esplorare protocolli basati su observer. Ciò significa che queste idee non sono utili per le implementazioni solo software. Uno dei (relativamente pochi) punti di forza che noi e le forze che rappresentiamo abbiamo è che il software libero può essere diffuso molto lontano e molto velocemente, rendendo difficile per chi si oppone alla privacy fermare con successo i nostri sforzi. Qualsiasi tecnologia basata su chip speciali perderà questi vantaggi.

Un altro problema dell'observer è di natura psicologica. Sebbene Chaum si impegni a fondo per progettare i suoi protocolli crittografici in modo che anche un osservatore imbroglione non possa apprendere NULLA sull'utente del computer che possa compromettere la sua privacy, le persone potrebbero comunque sentirsi a disagio nell'avere una "coscienza" meccanica in tasca. Le persone vogliono sentirsi in controllo dei loro computer e credo che sostenere questo controllo sia una parte importante della filosofia dei Cypherpunk.

Un punto correlato è che su sci.crypt sono già stati fatti dei confronti tra gli observer di Chaum e il chip Clipper, in quanto entrambi si basano su una tecnologia resistente alle manomissioni per implementare funzionalità che non sono del tutto nell'interesse del proprietario. Supponendo che riusciamo a sconfiggere Clipper, il marchio di questa associazione potrebbe aumentare la resistenza agli osservatori.

Vorrei che Chaum e il suo gruppo smettessero di dirigere i loro sforzi verso protocolli che richiedono un chip observer per essere efficaci. Certo, ci sono cose che non funzionano bene senza observer. Ma credo che una valutazione realistica dei pro e dei contro suggerisca che i protocolli senza observer hanno maggiori probabilità di favorire il nostro obiettivo finale di privacy personale.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](/cypherpunk/hal-finney/hal-finney-home-page)
