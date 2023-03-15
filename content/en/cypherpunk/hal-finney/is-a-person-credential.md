---
title: "Is-A-Person Credential"
description: "Hal Finney - 26 Agosto, 1993"
date: 2023-03-10T03:01:58+01:00
draft: false
weight: 340
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206194506/http://finney.org/~hal/is_a_person.html) - 26 Agosto, 1993

Alcuni hanno sostenuto che non c'è modo di impedire l'uso di pseudonimi multipli in rete, che è possibile oggi e domani le nuove tecnologie crittografiche forniranno tecniche ancora più semplici.

Si tratta di una semplificazione eccessiva, come sottolinea Tim May. Le credenziali "Is-a-person" possono essere utilizzate per determinare se qualcuno è un "Vero Nome" o no, che è proprio quello che Larry Detweiler voleva sapere. Ecco un modo in cui potrebbero funzionare.

(Per rendere più chiaro il concetto, è meglio pensare in termini di equazione: pseudonimo == chiave pubblica. Uno pseudonimo è una chiave pubblica. Pensiamo agli pseudonimi come a nomi, come "wonderer" o "sam hill", o forse come a indirizzi e-mail, come "hacker@univ.edu". Ma dal punto di vista della crittografia, questi sono solo fronzoli. La cosa importante è la chiave. Con una chiave pubblica, uno pseudonimo può firmare i suoi messaggi, in modo che nessun altro possa fingere di essere lui. Può leggere i messaggi che gli vengono inviati, messaggi che nessun altro può leggere. Se deve cambiare indirizzo e-mail, può farlo e mantenere la sua identità continuando a usare la stessa chiave. È la sua chiave che rappresenta la sua vera identità in rete. OK, torniamo alla credenziale is-a-person:)

Una credenziale is-a-person potrebbe essere strutturata in modo identico alle monete digitali utilizzate nella semplice proposta di Chaum sul contante digitale. Ti recheresti presso l'agenzia di accreditamento e forniresti una forma unica di identificazione, qualcosa che nessun altro potrebbe falsificare. Oggi potrebbe essere l'impronta del pollice, in futuro potrebbe essere una scansione del DNA. Tuttavia, non è necessario identificarsi con il proprio nome. Non hanno bisogno di sapere chi siete; sanno solo che siete un essere umano vivo e vegeto, che non hanno mai visto prima. (Potrebbe esserci più di un'agenzia di accreditamento, ma tutte condividerebbero un database di impronte digitali o altro).

Scegliete una chiave pubblica speciale che userete per tutte le vostre attività con il Vero Nome in rete. Questa chiave pubblica verrà utilizzata per firmare i messaggi che si vuole dimostrare provengano da una persona reale. Ogni messaggio inviato con quella firma è noto come proveniente da un Vero Nome e non da uno pseudonimo. Esiste un solo Vero Nome per persona.

Si noti che questo Vero Nome non deve essere necessariamente il proprio nome reale. Se vuoi postare sempre sotto il nome di John Q. Public e usare questa chiave speciale per questo scopo, è possibile farlo. Ma non potrete postare con nessun altro nome, compreso il vostro, come Vero Nome, a meno che non usiate la stessa chiave. E naturalmente, se lo fate, le persone potranno sapere che siete lo stesso John Q. Public, dato che state usando la stessa chiave di firma.

Il modo in cui questo viene stabilito è quello di prendere la chiave del vostro Vero Nome, che chiameremo TN, e fare come è stato fatto per i contanti di Chaum: passarla attraverso una funzione unidirezionale f, e chiudere con un numero casuale r^3: f(TN)*r^3. Lo dai all'agenzia di credenziali quando arriva con la tua impronta e la firmi prendendo la radice cubica. Questo è f(TN)^(1/3) * r. A casa, si divide per r, ottenendo f(TN)^(1/3).

Questo è il vostro certificato True Name. È possibile inviarlo a un registro di chiavi pubbliche insieme a TN; chiunque può calcolare f(TN) e verificare la firma dell'agenzia di credenziali. Le persone sapranno quindi che questa chiave è l'unica appartenente a una persona reale e firmata in questo modo. Per ogni persona può esistere una sola chiave di questo tipo.

Quindi, se le persone dichiarano di postare con i Veri Nomi, possono dimostrarlo molto facilmente, utilizzando la chiave del loro Vero Nome, firmata da un'agenzia di credenzializzazione. Le persone possono continuare a postare con tutti i nomi che vogliono, ma solo uno può definirsi Vero.

Si noti che questa soluzione non rivela molto della persona. Poiché i certificati sono accecati da r^3 quando vengono firmati, anche l'agenzia di credenzializzazione non ha modo di sapere quali impronte sono associate a quale Vero Nome. (Quindi, in realtà, non sarebbe un problema se l'agenzia ottenesse il vostro nome e indirizzo quando vi presentate - questo non potrebbe comunque essere collegato ai vostri messaggi se non lo voleste). Nessuno è obbligato a usare un vero nome quando pubblica un messaggio; potrebbe usare solo gli pseudonimi. D'altra parte, se le persone vogliono riservare certe conferenze solo ai Veri Nomi, possono farlo. C'è un'enorme flessibilità nell'utilizzare gli pseudonimi nella misura in cui si vuole.

Quindi, le persone non dovrebbero essere così precipitose nell'affermare che la crittografia può essere usata solo per aumentare l'anonimato. È una tecnologia potente che può essere usata per aumentare il nostro controllo sulle informazioni in molti modi. I documenti di Chaum continuano a stupirmi su cosa è possibile fare.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](hal-finney-home-page.md)
