---
title: "Distributing Authorities and Verifying Their Claims"
description: "- 1997"
date: 2023-01-29T15:17:17+01:00
draft: false
weight: 500
images: []
categories: []
contributors: ["cyphersats", "brandosari"]
---

[Originale](https://web.archive.org/web/20011102030812/http://szabo.best.vwh.net:80/authorities.html) - 1997

I sistemi di reputazione devono essere basati sui fatti piuttosto che su mere opinioni o sulla fede per essere efficaci. Ad esempio, se vogliamo avere un buon sistema di valutazione del credito, dobbiamo essere sicuri che il registro di credito, stilato dall'agenzia, sia sufficientemente preciso. Le informazioni sulla reputazione sono tipicamente raccolte e distribuite da autorità fidate specializzate in materia. Altri tipi di prestazioni specifiche sono spesso affidate a terzi: chiamo tali terze parti "autorità". Dobbiamo poterci fidare delle autorità (agenzia di credito, fornitore di software antivirus, autorità di certificazione, zecca di denaro digitale, ecc.) e delle loro affermazioni (sulla solvibilità, su byte patterns pericolosi, sull'identità, sul mantenimento della massa monetaria, ecc.). Come ha ben sottolineato Reagan, "fidati, ma verifica". Per meritare la nostra fiducia, le autorità devono convincerci che le loro dichiarazioni sono vere. Dobbiamo essere in grado di "accertare" la loro veridicità, verificando che le transazioni dichiarate siano effettivamente avvenute. Nelle economie di mercato esiste una professione specifica che svolge questa funzione: l’auditing.

È da tempo riconosciuto, sia negli affari che in politica, che le autorità godono di più affidabilità quando sono distribuite. Considerate i seguenti "protocolli" grezzi ma efficaci:

[Separazione dei poteri](https://avalon.law.yale.edu/18th_century/fed47.asp): l’autorità politica è divisa in vari rami, ognuno dei quali è responsabile solo di alcuni aspetti dell'autorità stessa (ad esempio: un ramo approva le leggi, un altro le fa rispettare).

[Segregazione dei compiti](https://web.archive.org/web/19990427063637/http://www.bus.orst.edu/faculty/brownc/lectures/controls/control1.htm): in una grande azienda, le transazioni sono suddivise in modo che nessuna persona possa commettere frodi. Lo chiamo "principio della required conspiracy" [^1]. Ad esempio, le funzioni di magazzino/consegna, vendita, e ricezione dei pagamenti sono svolte da soggetti diversi, con una politica che prevede che ognuno di essi riferisca ogni transazione a un quarto soggetto, la contabilità. Qualsiasi attività segnalata (ad esempio, consegna senza ricezione del pagamento) indica una potenziale frode (ad esempio: è stata effettuata una consegna a un cliente e il pagamento è stato intascato invece di essere versato nella cassa aziendale). La segregazione dei compiti è lo strumento preferito di chi svolge auditing. Quando è assente, quest’ultimo grida "fallo", proprio come un buon ingegnere reagirebbe alla scoperta di un single point of failure [^2]. Molti sistemi crittografici sono, giustamente, falliti dal punto di vista commerciale perché si basavano sulla fiducia in un'unica entità piuttosto che sulla segregazione delle funzioni in modo da creare cospirazioni.

L'ironia della sorte è che con la crittografia possiamo migliorare notevolmente le tecniche tradizionali di auditing (segregazione dei compiti, controlli incrociati delle transazioni con i libri contabili delle controparti e così via). Citerò brevemente tre meccanismi:

## Quorum

Distribuzione a quorum (anche detto "soglia") delle prestazioni o del controllo delle risorse, fondato sulla [condivisione segreta](https://web.archive.org/web/19990423083549/http://cacr.math.uwaterloo.ca/%7Edstinson/ssbib.html) delle chiavi necessarie per eseguire o controllare una risorsa. [Markus Jacobson](https://web.archive.org/web/20120113024315/http://cseweb.ucsd.edu/users/markus/) ha progettato, ad esempio, un quorum di zecche per firmare monete digitali. Il quorum stabilisce una "required conspiracy" di M su N per svolgere una funzione, fornendo un'opzione di protezione più forte rispetto al tipico due (2) su N utilizzato nella segregazione dei compiti e una maggiore fiducia nella sicurezza alla base della segregazione.

## Registri di audit post-infalsificabili

Tradizionalmente, chi svolge audit contatta delle controparti per verificare che una transazione sia effettivamente avvenuta. (Ecco il "principio della required conspiracy" di nuovo all'opera). Con dei registri post-infalsificabili, attraverso un sistema gerarchico di funzioni hash unidirezionali, una delle parti può vincolarsi pubblicamente alle transazioni man mano che vengono completate, pubblicando hash cumulativi firmati del flusso di operazioni. La riservatezza della transazione è completamente mantenuta fino a quando chi esegue audit decide di effettuare una “verifica" per determinare la sua effettiva natura. L'identità della controparte può rimanere riservata, dato che non è necessaria per stabilire gli altri fatti della transazione. L'unico attacco è la falsificazione delle transazioni in tempo reale, proprio mentre essa sta avendo luogo, evento nella maggior parte dei casi pratici impraticabile. La maggioranza delle frodi di contabilità prevede l'analisi di una serie di transazioni completate e successivamente modificate in modo da ottenere un risultato finale falsificato a piacere.

## Revisione confidenziale reciproca

Il Multiparty Secure Computation consente a N parti di condividere un calcolo, ognuna delle quali apprende solo ciò che può essere dedotto dai propri input e dall'output del calcolo. Ad esempio, le parti possono calcolare statistiche riassuntive sui loro registri di transazioni condivisi, compreso il controllo incrociato con le controparti, senza rivelare tali registri. Sfortunatamente, il MSC diretto è troppo lento (un messaggio Internet per ogni “bignum” machine instruction) ma il solo riconoscere che è effettivamente possibile può indirizzarci verso soluzioni pratiche.

Combinando queste possibilità crittografiche, possiamo ottenere un'altissima fiducia nella veridicità delle dichiarazioni e dei resoconti delle autorità senza rivelare informazioni identificative e altri dettagli delle transazioni alla base di tali resoconti. Ciò fornisce le fondamenta per solidi sistemi di reputazione e di terze parti fidate che mantengono l'integrità nel tempo, le comunicazioni e la sintesi, e preservano la riservatezza dei partecipanti di transazioni.

## References:

BRICS, [A BRICS Course on Secure Multi-Party Computation](https://web.archive.org/web/20031013005246/http://www.brics.aau.dk/BRICS/Activities/95/SecMultComp/index.html)

Carol Brown, [Internal Control Concepts](https://web.archive.org/web/19970808205719/http://www.bus.orst.edu/faculty/brownc/lectures/controls/control1.htm)

Publius (James A. Madison), Federalist No. 47 — [The Particular Structure of the New Government and the Distribution of Power Among Its Different Parts](https://avalon.law.yale.edu/18th_century/fed47.asp)

Publius (James A. Madison), Federalist No. 47 — Federalist No. 48 — [These Departments Should Not Be So Far Separated as to Have No Constitutional Control Over Each Other](https://avalon.law.yale.edu/18th_century/fed48.asps)

Douglas Stinson, [Bibliography on Secret Sharing Schemes](https://web.archive.org/web/19990423083549/http://cacr.math.uwaterloo.ca/%7Edstinson/ssbib.html)

Surety Technologies, “Digital Fingerprints”

Nick Szabo, “Negative Reputation Systems”


[^1]: La necessità di avere sempre una cospirazione in atto per mantenere l’ordine tra le diverse parti. N.d.T.
[^2]: Punto o caratteristica di un sistema  che, in condizioni critiche, può compromettere il sistema nella sua interezza
