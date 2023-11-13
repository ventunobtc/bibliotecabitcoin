---
title: "Detecting Double-Spending"
description: "Hal Finney - 15 Ottobre, 1993"
date: 2023-03-10T02:55:49+01:00
draft: false
weight: 345
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20010308153733/http://www.finney.org/~hal/chcash2.html) - 15 Ottobre, 1993

Revisionato 13 Marzo 1996

Ecco un tentativo di descrivere il contante digitale di Chaum dal suo articolo, Untraceable Electronic Cash, di Chaum, Fiat e Naor, tratto dagli atti di Crypto 88. Questo contante ha la proprietà che l'utente può rimanere anonimo finché lei non spende più di una volta, ma se spende due volte la sua identità viene rivelata.

Ecco come funziona in termini generali: Alice apre un conto presso una banca in modo non anonimo. Mostra un documento d'identità in modo che la banca sappia chi è; sia lei che la banca conoscono il numero di conto. Quando preleva del contante, si reca in banca o la contatta elettronicamente e presenta una prova di chi è e qual è il suo numero di conto, e la banca le dà del contante digitale. Il contante digitale è un modello di informazione, possibilmente memorizzato in un file informatico su una smart card o un disco magnetico. In seguito, la donna spende il contante digitale inviandolo o consegnandolo a Bob, un commerciante. Bob può controllare e verificare che il contante provenga dalla banca. Se il contante è valido, lo accetta e consegna la merce ad Alice. Successivamente, invia il contante alla banca per aggiungerlo al proprio conto.

Si noti che questo potrebbe essere fatto con una semplice firma RSA. La banca potrebbe fornire ad Alice una dichiarazione che dice "questo vale 1 dollaro", firmata dalla chiave segreta della banca. Bob può verificare che l'estratto conto è stato effettivamente firmato dalla banca e sa quindi che nessun altro, oltre alla banca, può averlo creato. Lo accetta e lo invia alla banca, che lo accetta in quanto riconosce la sua stessa firma.

Un problema di questo banale denaro è che la doppia spesa non può essere individuata o prevenuta, poiché tutti i contanti hanno lo stesso aspetto. Si può rimediare assegnando al contante un numero di serie univoco. Ora, quando Bob va ad accettare il contante da Alice, può chiamare la banca e dire: qualcun altro ha depositato il numero di serie 123456? Se no, accetta il contante e lo deposita. Questa è la cosiddetta moneta elettronica on-line; il commerciante deve verificare con la banca ogni transazione.

Questo sistema semplice e migliorato non merita, tuttavia, di essere chiamato contante, perché manca della caratteristica distintiva del contante digitale: non è anonimo. Quando la banca vede depositare del denaro con il numero di serie 123456, riconosce che si tratta della stessa banconota che Alice ha prelevato. La banca può quindi dedurre che Alice ha speso i soldi da Bob, e da questo tipo di informazione si potrebbe costruire un dossier su di lei con ogni tipo d'informazione distruttiva della privacy.

Per consentire l'anonimato, dobbiamo addentrarci nella matematica. Vogliamo che Alice e la banca creino insieme una firma RSA che non possa essere falsificata, ma che la banca non riconosca come proveniente da Alice. Questa è la prima cosa di cui parla l'articolo di Chaum.

Il denaro in questo sistema è della forma $(x, f(x)^{1/3}) \mod n$, dove $n$ è il modulo pubblico della banca. $f()$ (e, di seguito, $g()$) è una funzione unidirezionale, che può essere calcolata facilmente ma di cui è impraticabile calcolare l'inverso. Dovrebbe anche essere impraticabile trovare due diverse $y,z$ tali che $f(y) = f(z)$. Oggi esistono diverse scelte adeguate per le funzioni unidirezionali, le più comuni sono l'algoritmo MD5 di RSA e il Secure Hash Algorithm (SHA) del governo statunitense.

Il motivo per cui l'espressione sopra verrebbe accettata come denaro contante è duplice. In primo luogo, solo la banca può calcolare qualsiasi cosa elevato alla $(1/3) \mod n$. Questa è fondamentalmente l'operazione di firma RSA per l'esponente 3. Nessun altro può trovare radici cubiche. Il motivo per cui si usa $f(x)$ è il seguente. Supponiamo di aver proposto che $(x, x^{1/3})$ sia il contante, per un certo $x$ casuale, ragionando sul fatto che solo la banca può trovare la radice cubica di $x$. Riuscite a capire come falsificare il contante in questo modo? (Prendetevi qualche istante e cercate di capire come potreste costruire una coppia del genere anche se non sapete prendere le radici cubiche).

La risposta è che è facile falsificarlo scegliendo prima una $y$ a caso e mostrando la coppia $(y^3, y)$. Ora abbiamo un numero e la sua radice cubica. Eppure non abbiamo dovuto prendere nessuna radice cubica per trovarla. Ecco perché questo tipo di moneta non sarebbe utile.

Il sistema di Chaum evita questo problema prendendo la radice cubica di una funzione unidirezionale di $x$. Per falsificarlo senza prendere una radice cubica si dovrebbe produrre $(finv(y^3), y)$, che corrisponderebbe allo schema precedente, ma non si può invertire la funzione unidirezionale in questo modo. Quindi solo la banca può creare denaro nella forma corretta. Questo può essere considerato come la definizione formale e matematica del mio "denaro" informale di cui sopra, che era una banconota firmata digitalmente con un numero di serie. Qui, $x$ è il numero di serie ed è firmato digitalmente in questo modo speciale. Non è necessario altro.

La cosa bella di questo denaro è che consente il _blinding_[^1], un metodo per far firmare alla banca il valore senza sapere quale valore sta firmando. Funziona così. Alice sceglie $x$, che sarà la $x$ del denaro. Calcola $f(x)$, ma invece di inviarlo alla banca per farlo firmare (elevato alla potenza di $1/3$) sceglie prima un numero casuale r e invia $f(x)* r^3$ alla banca. La banca porta questo numero alla potenza di $1/3$, ottenendo $r*f(x)^{1/3}$. Ricordate, però, che la banca non vede $r$ o $f(x)$ separatamente, ma solo il loro prodotto. Non sa cosa sia $r$ o $f(x)$. In realtà potrebbero essere qualsiasi cosa.

La banca invia questo $r*f(x)^{1/3}$ ad Alice, che lo divide per $r$, che conosce. Questo le dà $f(x)^{1/3}$ e lei lo mette insieme a $x$ per ottenere il suo denaro digitale: $(x, f(x)^{1/3})$. Ha un pezzo di denaro che può essere stato firmato solo dalla banca, eppure la banca non lo riconosce quando viene depositato.

Durante il prelievo avvengono altre cose, non matematiche. Alice deve dimostrare alla banca la sua identità, come già detto. La banca addebiterà al suo conto il valore del contante. In questo sistema, per semplicità, assumiamo che tutti i contanti abbiano lo stesso valore. In un sistema reale, valori diversi potrebbero essere codificati da esponenti diversi da 3.

Quando Alice deposita il denaro, Bob deve chiamare la banca per assicurarsi che non sia già stato depositato in precedenza, essendo questo un sistema "on-line". Sebbene la banca non riconosca la $x$ (non l'ha mai sentita nominare), ricorda tutte le $x$ che sono state depositate e quindi può avvisare Bob se il denaro è stato speso in precedenza. Sia Bob che la banca possono verificare la firma digitale sul denaro e quindi lo onoreranno.

Tutto questo materiale occupa meno di una pagina del documento di Chaum, che è di nove pagine. Per Chaum, tutto questo è banale. Ora arriviamo alla parte interessante. Ora vedremo lo schema che permette a chi spende due volte di perdere l'anonimato. Bob non dovrà più controllare in banca se il denaro è già stato speso. Accetta il denaro da Alice sapendo che, se lei imbroglia, la banca onorerà il contante e farà causa ad Alice per recuperare la perdita.

(Per rendere questa spiegazione più facile da seguire, descriverò una versione leggermente semplificata del contante off-line di Chaum. La versione che descrivo richiede l'uso di una funzione unidirezionale non invertibile come la $f()$ usata sopra. La versione di Chaum non richiede un'assunzione così forte e fornisce una non tracciabilità "incondizionata" anche se la funzione unidirezionale è rotta).

Cominciamo con la forma del contante. È il prodotto di $k/2$ numeri, dove $k$ è un "parametro di sicurezza" che influisce sulle possibilità di successo di un imbroglione. Ogni numero è della forma $g(xi,yi)^{1/3}$, dove $g$ è una funzione unidirezionale a due argomenti simile alla f sopra. (I termini "$xi$", "$yi$", "$ai$", ecc. sono valori separati per ogni $i$ da 0 a $k/2$).

$xi$ e $yi$ sono così: $xi = f(ai)$, dove $ai$ è un numero casuale e $f$ è un'altra funzione unidirezionale. $yi$ è piuttosto complicato. È $f(ai\space xor \lang info\rang)$, dove $\lang info\rang$, la chiave dell'intera operazione, è un'informazione identificativa del conto di Alice! È il suo numero di conto concatenato con il numero di serie del contante.

Ora, perché fare tutto questo? Ecco perché. Se si riuscisse a scoprire sia ai che $(ai xor \lang info\rang)$, per un certo $i$, si conoscerebbe l'identità di Alice (Fare $xor$ di entrambi produrrebbe $\lang info\rang$). Quando Alice spende due volte, sia $ai$ che $ai\space xor \lang info\rang$ saranno rivelati.

Ciò che accade quando Alice spende la moneta è questo. Per ogni $i$ da 0 a $k/2$ Bob sceglie 0 o 1 a caso. Se sceglie 1 gli vengono detti $ai$ e $yi$. Se sceglie 0, gli viene detto $(ai xor \lang info\rang)$ e $xi$. Questo gli consentirà di verificare la firma sul denaro, come descritto in dettaglio più avanti.

Notate che quando Bob riceve queste informazioni, conoscerà una serie di ai e una serie di $(ai xor \lang info\rang)$, ma per diversi $i$. Non conosce sia $ai$ che $(ai xor \lang info\rang)$ per lo stesso $i$. Quindi non può rompere l'anonimato di Alice.

Quando Bob deposita il denaro in banca, trasmette le informazioni ottenute da Alice riguardo gli $ai$ e così via.

Supponiamo che Alice imbrogli. Spende di nuovo il denaro da un'altra parte, da Charlie. Charlie segue la stessa procedura di Bob, scegliendo 0 o 1 a caso per ogni valore di $i$. Ecco il problema. Poiché sta scegliendo a caso, è molto improbabile che scelga esattamente gli stessi 0 e 1 scelti da Bob. (In questo caso, la dimensione di $k$ è importante: se è più grande, è meno probabile che Charlie e Bob scelgano lo stesso schema di 0 e 1. Ma ciò rende i calcoli più lunghi). Ciò significa che per uno o più valori di $i$, Charlie probabilmente sceglierà uno 0 mentre Bob ha scelto un 1, o viceversa.

Per questo motivo, se Bob ha ottenuto ai per quel valore di $i$, Charlie otterrà $ai\space xor\space \lang info\rang$. Oppure, se Bob ha ottenuto $ai\space xor\space \lang info\rang$, Charlie otterrà $ai$. In ogni caso, quando Charlie invierà alla banca la registrazione di queste informazioni, la banca metterà insieme le informazioni di Bob e di Charlie e otterrà sia $ai$ che $ai\space xor\space \lang info\rang$. La combinazione di queste informazioni rivela $\lang info\rang$; e Alice viene catturata! Questa è l'idea principale.

(Chaum suggerisce di non affidarsi semplicemente al caso per assicurarsi che Bob e Charlie utilizzino serie diverse di 1 e 0. Almeno alcuni dei bit potrebbero essere assegnati a Bob e Charlie dalla banca in modo tale che ognuno riceva un numero diverso. In questo modo sarebbe garantito che Bob e Charlie scelgano valori opposti per alcuni $i$).

La ragione per cui il denaro ha la forma che ha è che Bob può controllare che sia firmato dalla banca. Per ogni valore di $i$ Alice deve fornirgli informazioni sufficienti per calcolare $xi$ e $yi$. Se Bob sceglie un 1, gli dà $ai$ e $yi$. Dato $ai$, Bob può calcolare $xi (=f(ai))$, e con questo e $yi$ può calcolare $g(xi,yi)$. Se Bob sceglie uno 0, lei gli dà $(ai\space xor\space \lang info\rang)$, come descritto prima, e anche $xi$. Dato $(ai\space xor\space \lang info\rang)$, Bob calcola $yi (=f(ai\space xor\space \lang info\rang))$, e con questo e $xi$ può calcolare $g(xi,yi)$.

Quindi, per ogni $i$, sia che Bob dia uno 0 o un 1, ottiene informazioni sufficienti per calcolare $g(xi,yi)$. Li moltiplica tutti insieme e conferma che sono uguali al valore del "denaro" originale di Alice quando viene portato alla terza potenza (ricordiamo che il denaro era il prodotto di $g(xi,yi)^{1/3}$ per tutti gli $i$). Solo la banca avrebbe potuto apporre una firma su questa funzione unidirezionale $f$, i cui argomenti assumono questa forma speciale.

Esiste un'ulteriore complicazione. (In realtà, se si cerca bene, esiste un numero quasi infinito di complicazioni. Ma ci concentreremo solo su un'altra). Alice deve ottenere questa forma speciale di denaro dalla banca in modo tale che la banca non la riconosca. Ciò significa fare _blinding_. Ma in questo caso la banca vuole essere sicura che il denaro abbia la forma corretta quando lo firma; in particolare, vuole essere dannatamente sicura che $\lang info\rang$ di Alice, sepolta in tutte quelle $f$ e $g$, sia effettivamente quella giusta per lei. Ma poiché la banca non può vedere ciò che sta firmando, è difficile farlo.

Chaum usa il taglia-e-cuci per questo. Fa preparare ad Alice tutte le $f$ e le $g$ secondo la forma sopra descritta, inserendo con cura le proprie $\lang info\rang$ incriminate in ognuna di esse. Poi moltiplica ogni $g(xi, yi)$ per un fattore di _blinding_ $ri^3$ proprio come nel primo caso. Questi sono quelli che invia alla banca per essere firmati.

Il trucco, però, è che ne invia il doppio di quelli che verranno utilizzati. Ne invia $k$, ma solo $k/2$ saranno utilizzati. (Ecco perché il ciclo precedente utilizzava $k/2$ come limite). La banca sceglie $k/2$ a caso tra i $k$ inviati come quelli che verranno effettivamente utilizzati. Alice deve quindi inviare i valori di $ri$ con _blinding_ per quelli che la banca non ha scelto.

L'idea è che se Alice cerca di imbrogliare, inserendo "Bozo" invece di "Alice" in quel campo $\lang info\rang$, corre un rischio. Innanzitutto, per essere utile, dovrà inserirlo in molti campi $\lang info\rang$ per diversi valori di $i$. Quando Bob e Charlie si confrontano dopo che lei ha fatto la doppia spesa, ogni valore di $i$ per il quale hanno scelto 0 e 1 diversi, che saranno in media la metà, rivelerà un campo $\lang info\rang$. Se ne falsifica solo alcuni, è probabile che la sua vera identità venga comunque rivelata.

Ma se ne falsifica molti, quando la banca ne sceglie la metà, è probabile che almeno alcuni di quelli falsi siano nel set che la banca non ha scelto. A quel punto, quando Alice dovrà rivelare le sue $r$ di _blinding_, il gioco sarà fatto. La banca svelerà tutti i $g(xi,yi)$ che non vengono utilizzati e vedrà i campi $\lang info\rang$ falsi.

Questa metodologia "taglia e scegli" ha lo svantaggio che Alice deve fare il doppio del lavoro per preparare il denaro, metà del quale sarà semplicemente buttato via. Ma è un modo semplice, "a forza bruta", per assicurarsi che le firme di _blinding_ vengano effettivamente eseguite su dati correttamente formati.

Quindi, ecco fatto. L'anonimato, a patto che non si imbrogli, e i doppiogiochisti vengono scoperti. È un po' complicato, ma i computer servono a questo; Bob e Alice non farebbero tutte queste cose a mano. Alice preme il pulsante "genera un candidato di denaro" e ottiene qualcosa da inviare alla banca (molti dei unovi PDA hanno comunicazioni wireless a infrarossi che sarebbero perfette per le transazioni faccia a faccia). Bob premerà il pulsante "controlla i soldi" quando Alice li spenderà e il pulsante lampeggerà in rosso o verde. Finché i calcoli non richiedono troppo tempo, cosa che in questo caso non accadrebbe nonostante la lunga spiegazione, le persone coinvolte possono ignorare i dettagli.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](cypherpunk/hal-finney/hal-finney-home-page)

[^1]: Il blinding, o Chaumian Blinding, è una tecnica che consente di effettuare una transazione senza rivelare i partecipanti, l'ora o il contenuto di essa, nemmeno alla figura centralizzata che la deve approvare. É stata sviluppata dal crittografo americano David Lee Chaum e pubblicata nel suo documento intitolato "Blind Signature for Untraceable Payments".
