---
title: "PGP Multi Precision Library Fuctions"
description: "Hal Finney - 26 Novembre, 1993"
date: 2023-03-12T19:06:03+01:00
draft: false
weight: 350
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206202230/http://finney.org/~hal/pgp_math_lib.html) - 26 Novembre, 1993

## Panoramica

PGP contiene una libreria matematica a precisione multipla per implementare le sue funzioni crittografiche. Questa libreria è in gran parte autonoma e può essere utilizzata in altre applicazioni.

La libreria di PGP è abbastanza portabile e funziona su macchine big- e little-endian, nonché su macchine con interi a 16 e 32 bit. Può essere compilata in una modalità che dipende solo da codice C, oppure può essere collegata a un modulo in linguaggio assembly personalizzato per la particolare macchina, in modo da garantire una maggiore velocità. I moduli in linguaggio assembly vengono forniti con PGP per una varietà di target.

La libreria utilizza buffer di dimensioni fisse per i suoi calcoli. Ciò significa che esiste un limite massimo alla dimensione dei numeri che possono essere utilizzati. Questo tetto viene però determinato in fase di compilazione, quindi le applicazioni speciali possono creare la libreria con tetti elevati, se lo si desidera.

La libreria di PGP e il suo codice sorgente in generale non sono di pubblico dominio; sono protetti da copyright di Philip Zimmermann, raggiungibile all'indirizzo <prz@acm.org>. PGP è rilasciato sotto termini di licenza che, credo, permettono l'uso del codice sorgente per scopi non commerciali. Sarebbe una buona idea parlarne con Phil prima di utilizzare il codice in qualsiasi prodotto destinato a un rilascio diffuso.

## La libreria

La libreria mp di PGP è contenuta in gran parte nel modulo mpilib.c. Questo modulo richiede mpilib.h, usuals.h e platform.h durante la compilazione. L'uso più semplice di mpilib è quello di collegarlo alla propria applicazione, compilando con i flag -D appropriati per la tua macchina. (Maggiori informazioni sulla scelta dei flag sono riportate di seguito).

Qualsiasi modulo che utilizzerà le funzioni mp dovrà includere anche mpilib.h. Tutti questi moduli dovranno essere compilati con i flag -D utilizzati da mpilib.c.

## Compilazione

La compilazione di mpilib.c e di altri moduli che includono mpilib.h richiede la scelta corretta dei flag -D. Il caso più semplice è se la macchina di destinazione è una di quelle per cui esistono definizioni esplicite in platform.h. Nella versione 2.3a, queste sono: MSDOS, VMS, VAXC, mips, i386, sparc, mc68000, mc68020. In ognuno di questi casi, nella distribuzione di PGP esiste un modulo in linguaggio assembly per implementare alcune funzioni mp.

Se si dispone di uno di questi target, aggiungere alla riga di comando di compilazione il flag -D per il simbolo dell'elenco precedente. Ad esempio, su una macchina MS-DOS, aggiungete -DMSDOS alla riga di comando. (In realtà, nella maggior parte dei casi questi simboli saranno definiti automaticamente dal compilatore o dal preprocessore del target. Ma non fa male definirli esplicitamente). Poi si deve assemblare anche il file corrispondente in linguaggio assembly. Per MS-DOS è 8086.asm; la scelta corretta per gli altri target dovrebbe essere evidente dai nomi dei file. Collegate il modulo oggetto in linguaggio assembly insieme al modulo oggetto di mpilib nella vostra applicazione.

Se non si dispone di uno di questi target, è possibile creare mpilib.c in modalità "portatile", che implementa tutte le funzioni in C. A tale scopo, definire -DPORTABLE e -DMPORTABLE sulla riga di comando. Inoltre, se si utilizza una macchina big-endian (come una macchina Sparc o 68000), è necessario definire anche -DHIGHFIRST. Le macchine little-endian non hanno bisogno di una definizione esplicita per l'endianness.

In modalità portatile, PGP utilizza di default unità a 16 bit. Se il vostro target ha int a 32 bit, potete definire -DUNIT32 per ottenere un codice molto più efficiente.

Ricordate che queste definizioni devono essere aggiunte a tutti i moduli che includono mpilib.h, oltre a mpilib.c. (Nota: nel makefile di PGP si possono vedere anche altre definizioni, -DDYN_ALLOC e -DSMALL_MEM. Queste non sono rilevanti per la libreria mp e non sono necessarie per questa applicazione).

## NOTA MOLTO IMPORTANTE

PGP ha molte forme alternative di moltiplicazione e divisione a precisione multipla; quella appropriata viene scelta in base alla macchina in uso. La scelta predefinita è SMITH, perché di solito è la più veloce. Tuttavia, l'algoritmo SMITH ha il difetto di non funzionare correttamente (nella versione 2.3a) per i numeri piccoli. (Questo non è un problema per PGP, perché funziona con grandi numeri di centinaia di bit. Ma per una libreria di uso generale non è adeguata).

Una scelta migliore è UPTON per gli scopi di una libreria di uso generale. Se si utilizza uno dei target predefiniti, è necessario modificare il file mpilib.h in modo che definisca UPTON invece di SMITH per la particolare architettura del target. Se si costruisce con -DPORTABLE, si può modificare mpilib.h per cambiare la scelta predefinita, oppure si può definire -DUPTON sulla riga di comando.

## Utilizzo della libreria

Prima dell'uso, la libreria MP deve essere inizializzata. Attualmente l'unica inizializzazione necessaria è l'impostazione del valore di precisione, che indica il numero di "unità" (un'unità è tipicamente un int sulla macchina di destinazione) di lunghezza dei buffer mp a dimensione fissa. Questo viene fatto chiamando:


    set_precision (MAX_UNIT_PRECISION);

Per utilizzare la libreria mp, includere mpilib.h nel proprio modulo. Le variabili multiprecisione devono essere dichiarate come segue:

    unit temp[MAX_UNIT_PRECISION];

In questo modo si dichiara una variabile "temp" adatta a contenere un valore multiprecisione. A me piace fare:

    typedef unitarr[MAX_UNIT_PRECISION];
    unitarr temp;

che ha lo stesso effetto.

Le variabili MP possono essere dichiarate localmente o come variabili globali, come per altri tipi di variabili C.

Le funzioni della libreria mp di PGP devono essere chiamate con l'indirizzo di una variabile mp. Poiché le variabili mp sono dichiarate come array in C, è sufficiente passare il nome della variabile. Ad esempio, per aggiungere x2 a x1, si può fare così:

    unitarr x1, x2;
    mp_add (x1, x2);

mpilib.h definisce unitptr come un puntatore a un'unità. Se si scrivono funzioni che prendono come parametri valori MP, questi devono essere dichiarati come unitptr. Ad esempio, una funzione per sommare tre numeri e restituire un risultato potrebbe essere:

    void mp_add3 (unitptr rslt, unitptr arg1, unitptr arg2, unitptr arg3)
    {
        mp_move (rslt, arg1);
        mp_add (rslt, arg2);
        mp_add (rslt, arg3);
    }

Assicuratevi di non commettere l'errore di dichiarare le variabili locali e globali come unitptr e di passarle alle funzioni mp. È necessario allocare spazio per esse dichiarandole come array di unità.

## Funzioni di libreria

La maggior parte delle funzioni della libreria sono concettualmente semplici. L'unica eccezione è la moltiplicazione modulare. Questa esegue la funzione $A*B \mod M$. PGP richiede che ciò avvenga tramite due chiamate. Prima si indica il modulo $M$ con la chiamata stage_modulus. Poi si esegue la moltiplicazione con mp_modmult. Questo è il codice per fare $rslt=arg1 *arg2 \mod m$:

    unitarr rslt, arg1, arg2, m;
    stage_modulus (m);
    mp_modmult(rslt, arg1, arg2);

Se si esegue una serie di moltiplicazioni con lo stesso modulo, si può chiamare stage_modulus una sola volta e poi chiamare mp_modmult ripetutamente. Si tenga presente che mp_modexp chiama internamente stage_modulus, quindi questa funzione sovrascriverà il valore del modulo salvato.

A PGP mancano alcune funzioni che ci si aspetterebbe. Non ha l'addizione e la sottrazione modulare. Queste dovrebbero sostanzialmente eseguire $A+B$ e poi testare l'intervallo 0..(M-1) e, se fuori dall'intervallo, aggiungere o sottrarre M una volta per riportarlo nell'intervallo. Forse queste funzioni saranno aggiunte a una versione futura di PGP.

Alcune funzioni mp hanno parametri che sono sia ingressi che uscite (ad esempio, mp_inc(r) incrementa $r$). In altri casi, invece, gli ingressi sono separati dalle uscite. In questi casi non si deve passare la stessa variabile come parametro di ingresso e di uscita. Ad esempio, non si deve eseguire mp_mult (a, a, b) per ottenere a*=b, perché a viene usata sia come parametro di ingresso che di uscita. Si dovrebbe invece eseguire mp_mult (temp, a, b) e poi mp_move (a, temp).

Ecco alcune utili funzioni mpilib di PGP e cosa fanno. I numeri MP sono $r$, $r1$, $r2$, ecc.; i numeri interi non MP sono $i$, $j$, ecc.

### Funzioni MP non modulari

    mp_move(r1,r2)
        r1 = r2
    mp_add(r1,r2)
        r1 += r2
    mp_sub(r1,r2)
        r1 -= r2
    mp_compare(r1,r2)
        -1,0,o 1 a seconda di (r1< r2),(r1=r2),(r1> r2)
    mp_mult(r1,r2,r3)
        r1 = r2 * r3;
    mp_udiv(rem,rquot,rdend,rdor)
        unsigned rdend/rdor;rem=rimedio,rquot=quoziente
    mp_div(rem,rquot,rdend,rdor)
        signed rdend/rdor; rem=rimedio, rquot=quoziente
    mp_mod(rem,rdend,rdor)
        rem = rdend % rdor (unsigned)
    mp_abs(r)
        r = valore assoluto di r
    mp_inc(r)
        r += 1
    mp_dec(r)
        r -= 1
    mp_neg(r)
        r = -r
    mp_square(r1,r2)
        r1 = r2 * r2
    msub(r,r1)
        se (r> =r1) r -= r1

### Funzioni mp modulari

    stage_modulus(rm)
        imposta rm come modulo per mp_modmult
    mp_modmult(rslt,r1,r2)
        rslt = r1 * r2 mod valore di stage_modulus
    mp_modsquare(r1,r2)
        r1 = r2 * r2 mod valore del modulo_stadio
    mp_modexp(rslt,r1,r2,rm)
        rslt = (r1 alla potenza r2) mod rm

### Funzioni di interfaccia MP/Integer

    mp_init(r,i)
        valore mp r = valore intero i
    mp_burn(r)
        r = 0 (per cancellare i dati sensibili in memoria)
    testeq(r,i)
        Vero se il valore mp r == valore intero i
    testne(r,i)
        Vero se il valore mp r = valore intero i
    testge(r,i)
        Vero se il valore mp r > = valore intero i
    testle(r,i)
        Vero se il valore mp r < = valore intero i
    significatività(r)
        restituisce il numero di unità significative in r
    mp_shortdiv(rquot,rdend,i)
        rdend/i; rquot=quoziente, restituisce il resto int
    mp_shortmod(rdend,i)
        restituisce rdend % i (senza segno)

### I/O dei valori MP

Il modulo PGP mpiio.c contiene alcune routine per l'I/O dei valori mp. Questo modulo include pgp.h (che include molti altri file), ma non è necessario. Consiglio di commentare l'inclusione di pgp.h. In questo modo sarà sufficiente aggiungere mpiio.c e mpiio.h alla cartella del programma.

Per accedere alle funzioni di I/O più generali in mpiio.c è necessario compilarlo con -DDEBUG. In questo modo sarà possibile chiamare:

    str2reg(r,str)
        Converte la stringa str nel valore mp r

La stringa passata a str2reg viene ritenuta essere in formato decimale. Per passare una stringa esadecimale deve terminare in 'h'; le stringhe binarie devono terminare in 'b' e quelle ottali in 'o'. Le stringhe decimali possono terminare facoltativamente con '.' (questi caratteri di terminazione possono essere aggiunti da un passaggio prima che str2reg venga chiamato, se non si vuole richiederli all'utente o al file).

    display_in_base(str,r,irad)
        Visualizza la stringa r nella base irad, preceduta da str

Questa funzione stampa il valore mp r su standard out, utilizzando la base irad. La precederà dalla stringa str.

    mp_display(str,r)
        Visualizza la stringa r in esadecimale, preceduta da str

Questa funzione visualizza sempre in esadecimale ed è un po' più veloce di display_in_base.

Una funzione mancante è quella per convertire un valore mp in una stringa in memoria. display_in_base e mp_display scrivono sempre sullo standard output. Se necessario, queste routine possono essere modificate abbastanza facilmente per inviare l'output a un puntatore incrementale (*bp++) per ottenere questo effetto.

### Altre funzioni PGP MP

Il modulo genprime.c contiene diverse funzioni mp utili. Sfortunatamente, dato che l'obiettivo di questo modulo è la generazione di chiavi casuali PGP, ha collegamenti ad altre parti di PGP, come la generazione di numeri casuali. Probabilmente è meglio estrarre le routine sorgenti da questo modulo in modo selettivo. Tra le routine che potrebbero essere di uso generale ci sono:

    mp_gcd(rslt,r1,r2)
        rslt = massimo comune divisore di r1 e r2
    mp_inv(rslt,r1,r2)
        Calcolo di rslt tale che rslt*r1 mod r2 sia 1
    nextprime(r)
        Trova il prossimo primo superiore a r, restituito in r
    slowtest(r)
        Vero se r è un primo probabile
    primetest(r)
        Setaccia poi slowtest di r, vero se primo probabile

nextprime è veloce e utilizza una combinazione di setacci e test di primalità probabilistici. È quello usato da PGP per la generazione della chiave RSA. slowtest è usato da nextprime; applica il test di Fermat con i primi quattro primi come valori di prova. primetest verifica prima la divisibilità di r rispetto a un elenco di piccoli primi, poi chiama slowtest per verificarlo.

Ci sono anche altre chiamate in mpilib.c che non ho documentato sopra. Sono per lo più di livello inferiore, ma potrebbero essere utili per alcuni scopi. Un po' di studio del codice rivelerà queste routine.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](/cypherpunk/hal-finney/hal-finney-home-page)
