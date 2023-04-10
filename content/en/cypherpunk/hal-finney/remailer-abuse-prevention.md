---
title: "Remailer Abuse Prevention"
description: "Hal Finney - 27 Marzo, 1994"
date: 2023-03-10T03:04:38+01:00
draft: false
weight: 370
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206204903/http://finney.org/~hal/remailer_abuse.html) - 27 Marzo, 1994

Stasera, in treno, stavo rileggendo alcuni vecchi documenti di crittografia, tra cui il documento Auscrypt di Chaum su pseudonimi digitali, credenziali e simili. Chaum descriveva un metodo per consentire alle biblioteche di prendere le persone che non restituiscono i libri della biblioteca, pur mantenendo la riservatezza di tutte le transazioni. Mi è venuto in mente che una forma modificata della sua idea potrebbe aiutare a ridurre l'abuso dei remailer.

L'idea di Chaum era piuttosto complicata, ma credo che un approccio più semplice potrebbe funzionare utilizzando il software Magic Money esistente. Un'idea di cui abbiamo parlato per ridurre gli abusi sarebbe quella di far pagare semplicemente l'affrancatura digitale per ogni messaggio. Tuttavia, è stato fatto notare che in pratica i costi di spedizione sarebbero probabilmente così bassi che questo aiuterebbe solo in casi estremi di abuso di volume.

La mia idea è che le monete non rappresentino denaro, ma siano "gettoni di non abuso". Con ogni messaggio verrebbe incluso un gettone di non abuso nella forma che Magic Money utilizza quando si cambia il denaro in arrivo in banca. Questo è composto dalla moneta stessa, più quella che viene chiamata "proto-moneta", che è una versione cieca di quella che diventerà la nuova moneta. Il remailer controllerebbe il token non abusato in arrivo per assicurarsi che non sia stato visto prima, proprio come fa la banca con Magic Money.

Tuttavia, non firmerebbe e restituirebbe immediatamente la proto-moneta _blinding_[^1]. Invece, lo terrebbe per un giorno o due per vedere se ci sono reclami riguardo al messaggio. Ciò richiederebbe di ricordare l'ID del messaggio in uscita insieme alla proto-moneta, ma non sarebbe necessario ricordare nient'altro del messaggio, e naturalmente con le catene di remailer la vera fonte del messaggio sarebbe completamente sconosciuta.

Se non arrivano reclami (il che è il caso della stragrande maggioranza dei messaggi, secondo la mia esperienza) il remailer firmerebbe e pubblicherebbe la proto-moneta _blinding_. Questa verrebbe messa in un luogo pubblico, generalmente disponibile a tutti coloro che potrebbero usare il remailer. L'utente che ha inviato il messaggio dovrebbe osservare questa proto-moneta e raccoglierla, sbloccandola con il suo software Magic Money, per produrre un nuovo token non abusivo che può usare per inviare un altro messaggio.

Se dovessero arrivare lamentele serie sul messaggio, il remailer non firmerebbe la proto-moneta e il mittente avrebbe perso un gettone non abusivo.

L'aspetto positivo di questo sistema è che protegge la privacy dell'utente del sistema remailer. Con la tecnologia Magic Money ogni token non d'abuso è _blinding_, quindi non c'è alcun collegamento possibile tra l'emissione di tali token e il loro utilizzo. Il grande problema dei remailer è che i messaggi abusivi non possono essere affrontati senza cercare di rintracciare chi li ha inviati, cosa che di solito è impossibile. Questo sistema risolve il problema senza danneggiare la privacy di nessuno.

Un paio di questioni che ho tralasciato riguardano le modalità di emissione dei token non abusivi. C'è l'ovvio pericolo che un abusatore riesca a ottenere sempre nuovi token fingendo di essere un nuovo utente della rete che vorrebbe usare il remailer. Due soluzioni a questo problema sarebbero: in primo luogo, far pagare una somma significativa per una manciata di token non di abuso; si tratterebbe di una tassa una tantum per i non abusatori, ma potrebbe diventare costosa per coloro che abusano; in secondo luogo, dare i token non di abuso solo agli utenti che possono essere identificati con i loro Veri Nomi. (Non si tratta di una situazione che richiede una sicurezza di livello militare; metodi semi-sicuri di identificazione dei veri nomi dovrebbero essere adeguati).

Un'altra cosa che ho suggerito sopra e che potrebbe sembrare un po' controversa è che le proto-monete firmate ma ancora _blinding_ potrebbero essere rese disponibili in chiaro. Poiché queste hanno la forma r*f(x)^(1/d), dove r, un numero casuale, è noto solo all'utente che ha creato la proto-moneta, credo che siano effettivamente criptate one-time-pad. Non vedo quindi la necessità di nascondere questi messaggi con una chiave pubblica. In effetti, non credo che Magic Money abbia bisogno di una chiave pubblica per l'utente, dato che viene utilizzata solo per proteggere questi messaggi, che non credo abbiano bisogno di protezione. Sono graditi commenti su questo punto.

Un ultimo punto riguarda la definizione di abuso. Per quanto mi riguarda, questo dipende dall'operatore del remailer. La settimana scorsa ho ricevuto una lettera molto educata e preoccupata da una ragazza che si chiedeva perché avesse ricevuto una mail dal mio remailer che la invitava a succhiare il dito di un tizio, solo che non era il suo dito. (Nonostante la nostra recente discussione sulla classificazione implicita "X" di questa lista, sono riluttante a essere più esplicito). Non ne ricevo molti, ma mi sento comunque in colpa. Il mio approccio attuale consiste nell'aggiungere ogni persona all'elenco degli indirizzi in uscita bloccati, ma credo che la tecnologia consenta una soluzione più efficace.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](/cypherpunk/hal-finney/hal-finney-home-page)

[^1]: il blinding, o Chaumian Blinding, è una tecnica che consente di effettuare una transazione senza rivelare i partecipanti, l'ora o il contenuto di essa, nemmeno alla figura centralizzata che la deve approvare. É stata sviluppata dal crittografo americano David Lee Chaum e pubblicata nel suo documento intitolato "Blind Signature for Untraceable Payments".