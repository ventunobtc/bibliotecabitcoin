---
title: "Truly Stealthy PGP"
description: "Hal Finney - 6 Marzo, 1994"
date: 2023-03-10T03:07:44+01:00
draft: false
weight: 360
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20020504223837/http://www.finney.org/~hal/stealth_pgp.html) - 6 Marzo, 1994

Revisionato il 7 Marzo, 1995

(Un PGP "veramente furtivo" sarebbe quello il cui output binario è indistinguibile dal rumore. Il PGP privato delle intestazioni dei messaggi e dei byte di lunghezza si avvicina a questo obiettivo, tranne per il fatto che il byte di ordine superiore della sua chiave di sessione crittografata avrebbe una distribuzione non uniforme (maggiori informazioni sul "PGP furtivo" qui). Eric Hughes ha proposto di scegliere le chiavi di sessione in modo da evitare questo problema. Ecco un algoritmo che potrebbe funzionare).

Sia L una potenza di 256 oltre il modulo n. Per sicurezza, sia la prossima potenza di 256 oltre n*(2^64) (ad esempio, come numero MP, L è 1 seguito da tanti 0 quante sono le dimensioni di n più 8 byte). Sia t la parte intera di L/n, in modo che L = n*t + s con s in [0,n]. Chiamiamo la chiave di sessione PGP IDEA SK, e la versione cifrata di questa m = SK^e. Ora eseguire i seguenti passaggi:

1) Scegliere una SK casuale in [0,n].
2) crittografarlo con RSA per formare m = SK^e mod n.
3) Scegliere un k casuale in [0,t].
4) Calcolare la chiave cifrata "a gradini" come M = m + k*n. Questo sarà uniforme in [0,(t+1)*n] se m è uniforme in [0,n], cosa che penso sia.
5) se M non è in [0,L) (cioè se M >= L) allora fallisce. Le probabilità che ciò accada sono meno di 1 su 2^64, in pratica zero.
6) Altrimenti memorizzare M come numero binario grezzo con base 256 di L byte.

L'idea è che una volta ottenuta l'uniformità di M in [0,(t+1)*n) possiamo renderla uniforme in [0,L] fallendo sui candidati che erano troppo alti. Questo accadrà solo se k=t e m>=s, e poiché t>2^64 le probabilità che ciò accada sono infinitesime.

Per recuperare m, basta prendere il primo log base 256 di L byte (che è noto al destinatario se sa che è per lui) come M, e calcolare m = M mod n.

Utilizzando questo algoritmo con l'attuale Stealth PGP si otterrebbe una versione "veramente furtiva" che, a mio avviso, sarebbe indistinguibile da byte casuali senza accesso alla chiave privata del destinatario.

Hal Finney<br>
hal@rain.org
