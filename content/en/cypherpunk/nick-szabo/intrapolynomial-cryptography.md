---
title: "Intrapolynomial Cryptography"
descriptio: "Nick Szabo - 1999"
date: 2023-01-29T15:18:32+01:00
draft: false
weight: 510
images: []
categories: []
contributors: ["cyphersats", "brandosari"]
---

[Originale](https://web.archive.org/web/20040411230036/http:/szabo.best.vwh.net/intrapoly.html) - 1999

Dei ricercatori hanno proposto svariati "client puzzle" o "busy-work" come hashcash, MicroMint, bit gold e affrancatura tramite calcolo computazionale {n.d.r. compute-cost postage} per creare valute indipendenti oppure rendere lo spam costoso. L'implicazione matematica di queste proposte è che esiste qualcosa come la crittografia intrapolinomiale. Quattro motivazioni per la teoria della crittografia intrapolinomiale sono (a) nuovi costrutti come le suddette applicazioni, (b) stima più accurata del costo computazionale necessario per la rottura di un cifrario, (c) potrebbe essere più facile dimostrare i limiti più bassi, piuttosto che trattarli come delle congetture, caso della crittografia superpolinomiale (standard), e (d) se non esistono funzioni unidirezionali, la crittografia standard è intrapolinomiale piuttosto che superpolinomiale.

Propongo la seguente formalizzazione:

$f:\set{0,1}^* \rightarrow \set{0,1}^*$ è una funzione detta strong k-benchmark per un modello di macchina $M$ con $k>=1$ se le successive condizioni sono verificate:

1.	$f$ è calcolabile nel tempo $O(p(n))$ su $M$, dove $p$ è un polinomio.
2.	$f$ non riduce l'ingresso più di $q(n,k)$, dove $q(n,k)$ è un polinomio di grado $k$.
3.	Per ogni algoritmo randomizzato $A$ in esecuzione su $M$ in un tempo inferiore a $q(n,k)p(n)$, esiste un $N$ tale che per $n>N$
$$Pr[A(f(x)) = f^{-1}(f(x))] < \frac{1}{q(n,k)p(n)}$$

In altre parole, non esiste un algoritmo più veloce di $q(n,k)p(n)$ che possa invertire $f$ per più di un numero trascurabile di valori.

È altrettanto possibile definire degli average-case, best-case e worst-case per le funzioni benchmark di grado $k$, in modo analogo alle funzioni unidirezionali. Domanda aperta (analoga alla questione sull’esistenza di funzioni unidirezionali nella crittografia superpolinomiale): è possibile dimostrare la condizione (3) come limite inferiore e superiore per una determinata funzione e k >= 1 su qualche modello di macchina realizzabile, ad esempio RAM-log?

Gli strong e average-case sono più adatti alle applicazioni relative alla crittografia. Purtroppo per questi scopi sarà inoltre necessario avere: 
1.	un elenco completo di tutti i modelli di macchine fisicamente realizzabili, nel senso che qualsiasi macchina di questo tipo possa essere simulata con un overhead molto piccolo, ad esempio costante oppure $O(log(n))$, da qualche modello presente nell'elenco
2.	di dimostrare i limiti inferiori su una funzione benchmark per tutti i modelli dell'elenco

Poiché si tratta di un'operazione lunga e stancante, si spera che nella pratica si possa farla franca con un breve elenco comprensivo di tutte le architetture verosimilmente implementabili. Questo potrebbe funzionare quando, ad esempio, la totale esposizione necessaria alla rottura di un protocollo è inferiore ai costi di ricerca e sviluppo per la progettazione e costruzione di una nuova architettura per sconfiggerlo. La crittoanalisi comprenderebbe la scoperta delle architetture ottimali per rompere un cifrario intrapolinomiale.

Ci sono almeno due implicazioni pratiche della precedente analisi. Una è che si ha poco margine d'errore nell'analisi e nell'implementazione di compute-cost postage, hashcash, bit gold, MicroMint e altri schemi di crittografia intrapolinomiale. La seconda è che, assumendo l'avversario non abbia un budget molto basso che lo rende di fatto limitato a classici personal computer, non ha senso analizzare la sicurezza o il costo di questi schemi senza considerare l'architettura della macchina. Ad esempio, gli spammer potrebbero essere in grado di sconfiggere il compute cost postage utilizzando chip personalizzati ottimizzati per calcolare la particolare funzione puzzle.

