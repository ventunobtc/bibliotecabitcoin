---
title: "How to Time-Stamp a Digital Document"
description: "Pubblicato su Journal of Cryptology, vol 3, no 2, pagine 99-111, 1991"
date: 2023-11-04T12:48:23+01:00
draft: false
weight: 200
images: []
categories: []
contributors: ["feeder"]
---

[Originale](https://link.springer.com/content/pdf/10.1007/3-540-38424-3_32.pdf) - 1991

## Riassunto

La prospettiva di un mondo in cui tutti i documenti di testo, audio, immagini e video sono memorizzati in formato digitale su supporti facilmente modificabili solleva il problema di come fornire una certificazione affidabile della data di creazione o ultima modifica di un documento. Il problema è quello di datare i dati, non il supporto. Nel presente lavoro proponiamo procedure computazionalmente accettabili per apporre una marca temporale digitale su tali documenti, in modo che sia impossibile per un utente retrodatare o postdatare il documento, anche con la collusione di un sistema di marcatura temporale. Le nostre procedure mantengono la completa privacy del contenuto dei documenti stessi e non richiedono alcuna registrazione da parte del servizio di marcatura temporale.

<p align=center><em>
La gloria del tempo è conciliare i re avversari, <br>
Smascherare il falso e portare alla luce il vero, <br>
Porre il suo sigillo su ciò che è antico, <br>
Destare il giorno e sorvegliare la notte, <br>
Per far torto a chi fa torto, fino al pentimento.
<br><br>
Lo Stupro di Lucrezia, l. 941
</em></p>

## 1 - Introduzione

Ci sono molte situazioni in cui è necessario certificare la data di creazione o ultima modifica di un documento. Ad esempio, in materia di proprietà intellettuale, è talvolta fondamentale verificare la data in cui un inventore ha per la prima volta messo per iscritto un'idea brevettabile, al fine di stabilirne la precedenza rispetto ad altre rivendicazioni.

Una procedura attualmente accettata per creare la marca temporale di un'idea scientifica prevede l'annotazione giornaliera del proprio lavoro in un quaderno di laboratorio. Le annotazioni datate vengono inserite una dopo l'altra nel quaderno, senza lasciare alcuna pagina vuota. Le pagine del quaderno, numerate in modo sequenziale e poi rilegate, rendono difficile manomettere le registrazioni senza lasciare segni evidenti. Se il quaderno viene poi vidimato regolarmente da un notaio pubblico oppure rivisto e firmato da un dirigente aziendale, la validità del credito è ulteriormente rafforzata. Se l'anteriorità delle idee dell'inventore viene contestata in un secondo momento, sia l'evidenza fisica del taccuino che la procedura stabilita servono a dimostrare che è stato l'inventore ad aver avuto l'idea in una certa data o prima di essa.

Esistono altri metodi di marcatura temporale. Ad esempio si può spedire una lettera a se stessi e non aprirla. In questo modo si garantisce che la lettera allegata è stata creata _prima_ della data del timbro postale apposto sulla busta. Le aziende incorporano procedure più elaborate nei loro processi quotidiani al fine di aumentare la credibilità dei documenti interni, nel caso in cui vengano contestati in un secondo momento. Ad esempio, questi metodi possono garantire che i documenti siano gestiti da più di una persona, in modo che qualsiasi manomissione di un documento da parte di una persona venga rilevata da un'altra. Tutti questi metodi, tuttavia, si basano su due presupposti: il primo è che i documenti possono essere esaminati per trovare eventuali segni di manomissione; il secondo è che esista un'altra parte che visioni il documento la cui integrità e imparzialità è vista come garanzia della richiesta.

Riteniamo che questi presupposti siano messi in seria discussione nel caso di documenti creati e conservati esclusivamente in forma digitale. Questo perché i documenti elettronici digitali sono estremamente facili da manomettere, inoltre la modifica non lascia alcun segno sul supporto fisico. Si rende necessario, quindi, un metodo di marcatura temporale dei documenti con le seguenti due proprietà:

- innanzitutto, si deve trovare un modo per datare i dati stessi, senza fare affidamento sulle caratteristiche del supporto su cui questi appaiono, in modo che sia impossibile modificare anche un solo bit del documento senza che la modifica sia evidente.
- in secondo luogo, dovrebbe essere impossibile marcare un documento con una data e ora diverse da quelle attuali.

Lo scopo di questo articolo è introdurre una soluzione matematicamente valida e computazionalmente accettabile al problema della marcatura temporale. Nelle sezioni che seguono, presenteremo una prima semplice e ingenua soluzione al problema: la cassetta di sicurezza digitale. Questa soluzione ha la funzione didattica di evidenziare le ulteriori difficoltà associate alla marcatura temporale digitale, in aggiunta a quelle riscontrate nei metodi convenzionali. I successivi miglioramenti di questa semplice soluzione conducono infine a delle implementazioni pratiche della marcatura temporale digitale.

## 2 - Il contesto

Il contesto del nostro problema è una rete distribuita di utenti, che può rappresentare un insieme di individui, aziende diverse o divisioni all'interno della stessa azienda; ci riferiremo agli utenti come _clienti_. Ogni cliente ha un numero di identificazione unico.

Una soluzione al problema della marcatura temporale può essere costituita da diverse parti. Esiste una procedura da eseguire quando un cliente appone la marca temporale di un documento. Il cliente deve poter successivamente verificare che la procedura sia stata eseguita correttamente. Dovrebbe inoltre esistere una procedura per rispondere alle contestazioni di una terza parte sulla validità della marcatura del documento.

Come per qualsiasi problema crittografico, è cruciale caratterizzare con precisione il livello di sicurezza raggiunto da uno schema di marcatura temporale. Una buona soluzione al problema richiede che, sotto ragionevoli ipotesi riguardo la capacità computazionali degli utenti, la loro affidabilità e la complessità computazionale del problema, sia estremamente difficile o addirittura impossibile produrre false marche temporali. Naturalmente, più deboli sono le assunzioni necessarie, meglio è.

## 3 - Una soluzione ingenua

Una soluzione semplice, definita come "cassetta di sicurezza digitale", potrebbe funzionare come segue:

ogni volta che un cliente deve marchiare temporalmente un documento, questo viene trasmesso a un servizio di marcatura temporale (N.d.T. in inglese _Time Stamping Service_, TSS"). Il servizio registra la data e l'ora in cui il documento è stato ricevuto e ne conserva una copia di sicurezza. Se l'integrità del documento del cliente viene messa in discussione, è possibile confrontarlo con la copia conservata dal TSS. Se le due copie sono identiche, questa è la prova che il documento non è stato manomesso dopo la data indicata nei registri del TSS. Questa procedura soddisfa di fatto il requisito centrale per la marcatura temporale di un documento digitale.[^1] Tuttavia, questo approccio solleva alcune problematiche:

[^1]: Gli autori hanno appreso recentemente di una simile proposta da parte di Kanare [14]

**Privacy** Questo metodo compromette la riservatezza del documento in due modi:  

  - una terza parte potrebbe conoscere e intercettare la trasmissione del documento;
  - dopo la trasmissione, il documento è disponibile presso il TSS a tempo indeterminato. In questo modo il cliente non deve preoccuparsi soltanto della sicurezza del documento in suo possesso, ma anche di quella della copia depositata presso il TSS.

**Banda e storage** Sia la quantità di tempo necessaria per inviare un documento per la marcatura temporale che la quantità di memoria richiesta per la memorizzazione al TSS dipendono dalla dimensione del documento stesso. Pertanto, il costo in termini di tempo e spesa per marcare un documento di grandi dimensioni potrebbe risultare proibitivo.

**Incompetenza** La copia del documento di competenza al TSS potrebbe essere danneggiata durante la trasmissione, potrebbe essere marchiata in maniera errata da parte del TSS, oppure potrebbe essere danneggiata o persa del tutto in qualsiasi momento durante la sua conservazione. Ognuno di questi eventi invaliderebbe la rivendicazione della marca temporale da parte del cliente.

**Fiducia** Il problema fondamentale rimane: nulla in questa soluzione impedisce al TSS di accordarsi con un cliente per marchiare il documento con una data e ora diverse da quelle attuali.

Nella prossima sezione dell'articolo descriveremo una soluzione che affronti le prime tre problematiche sopra presentate. L'ultimo problema, la fiducia, sarà affrontato separatamente in una sezione dedicata.

## 4 - Un servizio fidato di marcatura temporale

In questa sezione assumiamo che il TSS sia affidabile, e descriviamo due migliorie rispetto alla soluzione ingenua presentata precedentemente.

### 4.1 - Hash

La prima semplificazione consiste nel fare uso di una famiglia di _funzioni hash senza collisione_ crittograficamente sicure. Si tratta di una famiglia di funzioni di tipo:

$$ h: {\lbrace0, 1\rbrace}^* \rightarrow  {\lbrace0, 1\rbrace}^l $$

che comprimono stringhe di bit di lunghezza arbitraria in stringhe di bit di lunghezza fissa $l$, con le seguenti proprietà:

1. le funzioni $h$ sono computazionalmente semplici da eseguire ed è facile scegliere casualmente una tra le funzioni della famiglia.

2. data una funzione $h$, è computazionalmente impossibile trovare una coppia distinta di stringhe $x$, $x'$ che soddisfi la proprietà $h(x) = h(x')$. (L'esistenza di tale coppia è definita _collisione_.)

L'importanza pratica di queste funzioni è nota da molto tempo e sono state utilizzate dai ricercatori in numerose applicazioni, si veda ad esempio [7, 15, 16]. Damgird ha dato la prima definizione formale e una prova costruttiva della loro esistenza, partendo dal presupposto che esistano permutazioni unidirezionali "claw-free" [4] (N.d.T. in italiano _senza artigli_, cioè è difficile trovare due input $x, y$ per una coppia di funzioni $f$ e $g$ tali che $f(x) = g(y)$). A tal fine, è sufficiente una qualsiasi "azione di gruppo unidirezionale" [3].

Naor e Yung hanno definito la nozione simile di "funzioni hash universali unidirezionali" che soddisfano, al posto della seconda condizione sopracitata, il requisito leggermente più debole che sia computazionalmente impossibile, data una stringa $x$, calcolare un'altra stringa $x' \neq x$ che soddisfi $h(x) = h(x')$ per una qualsiasi $h$ scelta casualmente. Sono stati in grado di creare tali funzioni partendo dal presupposto che esistano funzioni unidirezionali uno-a-uno [17]. Rompel ha recentemente dimostrato che tali funzioni esistono se esistono funzioni unidirezionali [20]. Per una discussione sulle differenze tra questi due tipi di funzioni hash crittografiche, si veda il paragrafo 6.3.

Esistono implementazioni pratiche di funzioni hash, ad esempio quella di Rivest [19], che appaiono ragionevolmente sicure.

Utilizzeremo le funzioni hash nel seguente modo: invece di trasmettere il proprio documento $x$ al TSS, un cliente invierà il suo valore di hash $h(x) = y$. Ai fini dell'autenticazione, la marcatura temporale di $y$ è equivalente alla marcatura temporale di $x$. Questo riduce notevolmente sia il problema della larghezza di banda che quello dello spazio di memorizzazione, risolvendo anche il problema della privacy. A seconda degli obiettivi di progettazione di una possibile implementazione del sistema di marcatura temporale, può esistere un'unica funzione di hash utilizzata da tutti i clienti, o diverse funzioni di hash per i diversi clienti.

Per il resto di questo documento, parleremo di valori hash di marca temporale $y$ come stringhe casuali di bit di lunghezza fissa. Parte della procedura di convalida di una marca temporale sarà quella di produrre il documento pre-immagine $x$ che soddisfi $h(x) = y$; l'incapacità di produrre tale documento invaliderà la marcatura temporale.

### 4.2 Firma

Il secondo miglioramento si avvale delle firme digitali. Informalmente, uno _schema di firma_ è un algoritmo che consente a un soggetto, il firmatario, di etichettare i messaggi in modo da identificare univocamente se stesso. Le firme digitali sono state proposte da Rabin e da Diffie e Hellman [18, 7]. Dopo una lunga serie di articoli di numerosi autori, Rompel [20] ha dimostrato che l'esistenza di funzioni unidirezionali può essere sfruttata per progettare uno schema di firma che soddisfi la nozione molto forte di sicurezza definita per la prima volta da Goldwasser, Micali e Rivest [10].

Con uno schema di firma sicuro, quando il TSS riceve il valore di hash aggiunge la data e l'ora, quindi firma il documento appena prodotto e lo invia al cliente. Controllando la firma, il cliente ha la certezza che il TSS abbia effettivamente elaborato la richiesta, l'hash sia stato correttamente ricevuto e siano state inserite data e ora corrette. In questo modo si risolve il problema dell'incompetenza presente e futura del TSS e si riduce notevolmente la necessità, da parte del TSS stesso, di conservare i documenti.

## 5 Due schemi di marcatura temporale  

<p align="center"><em>
Sed quis custodiet apsos Custodes?<br>
Juvenal, c. 100 A.D.</em><br>
Ma chi sorveglierà i sorveglianti stessi?
</p>  

Quello che abbiamo descritto finora è, a nostro avviso, un metodo pratico per la marcatura temporale di documenti digitali di lunghezza arbitraria. Tuttavia, né la firma né l'uso di funzioni hash impediscono in qualche modo a un servizio di marcatura temporale di emettere un marchio falso. Idealmente, vorremmo un meccanismo che garantisca che, per quanto il TSS sia inaffidabile, i certificati emessi saranno sempre corretti e che non sia in grado di emettere marchi errati anche se lo volesse.

Può sembrare difficile definire una procedura di marcatura temporale in modo da rendere impossibile la produzione di false marche temporali. Dopotutto, se l'output di un algoritmo $A$, dato in ingresso un documento $x$ e alcune informazioni temporali $t$, è una stringa di bit $c = A(x,t)$ che rappresenta una legittima marca temporale per $x$, cosa impedisce a un falsario, qualche tempo dopo, di calcolare le stesse informazioni temporali $t$ ed eseguire $A$ per produrre lo stesso certificato $c$? La domanda rimane pertinente anche se $A$ è un algoritmo probabilistico.

Il nostro compito può essere visto come il problema di simulare l'azione di un TSS fidato, in assenza di parti fidate. Esistono due approcci piuttosto diversi che possiamo adottare, e ognuno di questi porta a una soluzione. Il primo approccio consiste nel costringere un TSS centralizzato, ma probabilmente inaffidabile, a produrre marchi temporali autentici, in modo tale che sia sufficientemente difficile produrne di falsi. Il secondo approccio consiste nel distribuire in qualche modo la fiducia richiesta tra gli utenti del servizio. Non è affatto chiaro, al momento, se questi due approcci sono implementabili.

### 5.1 Collegamento

La nostra prima soluzione parte dall'osservazione che la sequenza dei clienti che richiederanno i servizi di marcatura temporale e i valori hash che invieranno non possono essere conosciuti in anticipo. Quindi, se il TSS include i bit della sequenza di richieste precedenti inviate dai clienti nel certificato firmato, allora sapremo che la marcatura temporale si è verificata **dopo** queste richieste. Ma il requisito di includere nel certificato i bit dei documenti precedenti può essere utilizzato anche per risolvere il problema di vincolare il tempo nell'altra direzione, perché il TSS non può emettere certificati successivi a meno di avere disponibile la richiesta attuale.

Descriviamo due varianti di questo schema di collegamento; la prima, leggermente più semplice, rispecchia la nostra idea principale, mentre la seconda può essere preferibile nella pratica. In entrambe le varianti, il TSS farà uso di una funzione hash priva di collisioni, da indicare con $H$. Questa procedura deve essere aggiunta all'uso di funzioni hash da parte dei clienti per produrre il valore hash di ogni documento di cui si desidera avere la marcatura temporale.

Per essere precisi, una _richiesta_ di marcatura temporale consiste in una stringa $y$ di $l$-bit (presumibilmente il valore di hash del documento) e un numero di identificazione del cliente $ID$. Useremo la notazione $\sigma(\cdot)$ per indicare la procedura di firma utilizzata dal TSS. Il TSS emette _certificati_ firmati e sequenzialmente numerati. In risposta alla richiesta $(y_n, ID_n)$ del nostro cliente, $n-esima$ richiesta in sequenza, il TSS esegue due operazioni:

1. Invia al nostro cliente il certificato firmato $s = \sigma(C_n)$, dove il certificato
   
   $$C_n = (n, t_n, ID_n, y_n; L_n)$$
   
   è composto dal numero di sequenza $n$, dall'ora $t$, dal numero $ID$ del cliente, dal valore di hash $y_n$ della richiesta e da alcune informazioni di collegamento che provengono dal certificato precedentemente emesso: $L_n = (t_{n-1}, ID_{n-1}, y_{n-1}, H(L_{n-1}))$

2. Quando la richiesta successiva è stata elaborata, il TSS invia al nostro cliente il numero di identificazione $ID_{n+1}$ per la richiesta successiva.

Dopo aver ricevuto $s$ e $ID_{n+1}$ dal TSS, il cliente verifica che $s$ sia una firma valida di un certificato valido, ad esempio che sia della forma corretta $(n, t, ID_n, y_n; L_n)$, contenente il tempo corretto $t$.

Se il documento $x$ venisse contestato successivamente alla marcatura temporale, il contestatore controllerebbe innanzitutto che la marca temporale $(s, ID_{n+1})$ sia della forma corretta (essendo $s$ la firma valida di un certificato contenente effettivamente l'hash di $x$). Per garantire che il cliente interessato non abbia colluso con il TSS, il contestatore può chiamare il cliente $ID_{n+1}$ e chiedergli di produrre il sua marcatura temporale $(s', ID_{n+1})$. Questo include una firma

$$ s' = \sigma(n + 1, t_{n+1}, ID_{n+1}, y_{n+1}; L_{n+1}) $$  

di un certificato che contiene nelle sue informazioni di collegamento $L_{n+1}$ una copia del suo valore hash $y_n$. Questa informazione di collegamento è ulteriormente autenticata dall'inclusione a sua volta dell'immagine $H(L_n)$ delle sue informazioni di collegamento $L_n$. Un contestatore particolarmente sospettoso può ora chiamare $ID_{n+2}$ e verificare la marca temporale successiva nella sequenza; questa operazione può continuare per tutto il tempo desiderato dal contestatore. Allo stesso modo, il contestatore può anche seguire la catena delle marche temporali a ritroso, a partire dal cliente $ID_{n-1}$.

In che modo questo vincola il TSS a non produrre marcature temporali errate? Si osservi innanzitutto che l'uso della firma fa si che l'_unico_ modo per falsificare una marcatura temporale è con la collaborazione del TSS. Ma il TSS non può post-datare un documento, perché il certificato deve contenere i bit delle richieste immediatamente precedenti al tempo desiderato, ma il TSS non li ha ancora ricevuti. Non è inoltre possibile retrodatare un documento preparando una falsa datazione per un'epoca precedente, perché i bit del documento in questione devono essere incorporati nei certificati emessi successivamente, ma questi certificati sono stati già emessi. Includere correttamente un documento firmato nel flusso già esistente di certificati con marca temporale richiede inoltre il calcolo di una collisione per la funzione hash $H$.

Pertanto, l'unica possibilità di falsificazione consiste nel preparare una falsa catena di marche temporali, abbastanza lunga da esaurire il più sospettoso contestatore che si prevede.

Nello schema appena descritto, i clienti devono conservare tutti i loro certificati. Al fine di allentare questo requisito, nella seconda variante di questo schema colleghiamo ogni richiesta non solo alla richiesta successiva, ma alle successive $k$ richieste. Il TSS risponde alla $n-esima$ richiesta come segue:

1. Come sopra, il certificato $C_n$ è nella forma $C_n = (n, t_n, ID_n, y_n; L_n)$, dove ora l'informazione di collegamento $L_n$ è della forma:
   
   $$ L_n = [(t_{n-k}, ID_{n-k}, y_{n-k}, H(L_{n-k})), ..., (t_{n-1}, ID_{n-1}, y_{n-1}, H(L_{n-1}))] $$

2. Dopo che le successive $k$ richieste sono state processate, il TSS invia al nostro cliente la lista $(ID_{n+1}, ..., ID_{n+k})$

Dopo aver verificato che la marca temporale di questo cliente è corretta, un contestatore sospettoso può chiedere a uno qualsiasi dei successivi $k$ clienti $ID_{n+i}$ di produrre la propria marca temporale. Come sopra, la sua marca temporale include la firma di un certificato che contiene nelle sue informazioni di collegamento $L_{n+i}$ una copia delle parti rilevanti di pertinenza del certificato contestato $C_n$, autenticata dall'inclusione del valore hash di $H$ delle informazioni di collegamento $L_n$ del cliente contestato. La sua marca temporale include anche i numeri di cliente $(ID_{n+i+1}, ..., ID_{n+i+k})$, di cui gli ultimi $i$ sono i nuovi; il contestatore può chiedere a questi clienti le loro marche temporali, e questo può continuare per tutto il tempo desiderato dal contestatore.

Oltre ad alleggerire il requisito di salvataggio di tutti i certificati da parte dei clienti, questa seconda variante rafforza la sicurezza del sistema, dove per incorporare correttamente un nuovo documento nel flusso già esistente di certificati marcati con data e ora richiede il calcolo di una collisione simultanea $ampia k$ per la funzione hash $H$, invece di una semplice collisione a coppie.

### 5.2 Fiducia distribuita

Per questo schema, si ipotizza che esista uno schema di firma sicuro in modo che ogni utente possa firmare i messaggi, e che un sicuro generatore standard di numeri pseudocasuali $G$ sia disponibile a tutti gli utenti. Un _generatore pseudocasuale_ è un algoritmo che, a partire da una breve sequenza di bit passata in ingresso, detta _seme_ (N.d.T. in inglese _seed_), genera in uscita sequenze di bit che sono indistinguibili da quelle generate da un qualsiasi algoritmo realistico; in particolare, tali sequenze sono imprevedibili. Questi generatori sono stati studiati per la prima volta da Blum e Micali [2] e da Yao [22]; Impagliazzo, Levin e Luby hanno dimostrato che questi generatori esistono a patto che esistano funzioni unidirezionali [12].

Ancora una volta, consideriamo un valore hash $y$ che il nostro cliente vorrebbe marchiare temporalmente. Egli utilizza $y$ come seme per il generatore pseudocasuale il cui risultato può essere interpretato come una $k-tupla$ di numeri di identificazione dei clienti.

$$ G(y) = (ID_1, ID_2, ..., ID_k) $$

Il nostro cliente invia la sua richiesta $(y, ID)$ a ciascuno di questi clienti. In risposta riceve dal cliente $ID_j$ un messaggio firmato $s_j = \sigma_j( t, ID, y)$ che include il tempo $t$. La sua marca temporale è costituita da $[(y, ID), (s_1,. . ., s_k)]$. Le $k$ firme $s_j$ possono essere facilmente verificate dal nostro cliente o da un potenziale contestatore. Non sono necessarie ulteriori comunicazioni per rispondere a una successiva contestazione.

Perché un tale elenco di firme dovrebbe costituire una marca temporale credibile? Il motivo è che, in queste circostanze, l'unico modo per produrre un documento con una marca temporale valida ma con tempo falsificato è usare un valore di hash $y$ in modo che $G(y)$ nomini $k$ clienti che siano disposti a collaborare per falsificare la marcatura. Se in un qualsiasi momento esiste al massimo una frazione costante $\epsilon$ di clienti potenzialmente disonesti, il numero atteso di semi $y$ che devono essere provati prima di trovare una $k-tupla$ $G(y)$ contenente solo collaboratori tra questa frazione è $\epsilon^{-k}$. Inoltre, dal momento che abbiamo assunto che $G$ sia un generatore pseudocasuale sicuro, non esiste un modo più conveniente per trovare un seme $y$ valido se non scegliendolo casualmente. Questo ignora l'ulteriore problema dell'avversario, nella maggior parte degli scenari reali, di trovare un documento plausibile che produca in modo conveniente un valore di hash $y$.

Il parametro $k$ deve essere scelto in fase di progettazione del sistema in modo che questo sia un calcolo non fattibile. Si osservi anche che una stima molto pessimistica della popolazione di clienti corruttibili $\epsilon$, che potrebbe essere del 90%, non comporta una scelta proibitiva di $k$. Non è inoltre necessario che l'elenco dei clienti corruttibili sia fisso, purché il rapporto tra questi e l'intera popolazione non superi mai $\epsilon$.

Questo schema non necessita di un TSS centralizzato. Gli unici requisiti sono che sia sempre possibile comunicare con gli altri clienti, ricevere da loro le firme richieste e che esista un elenco pubblico di clienti in modo tale che sia possibile interpretare il risultato di $G(y)$ in modo standard come una $k-tupla$ di clienti. Un'implementazione pratica di questo metodo richiederebbe specifiche disposizioni nel protocollo per i clienti che non possono essere contattati al momento della richiesta di marcatura temporale. Ad esempio, per opportuni $k' < k$, il sistema potrebbe accettare risposte firmate da un qualsiasi $k'$ dei $k$ clienti nominati da $G(y)$ come una marca temporale valida per $y$ (in questo caso sarebbe necessario un valore maggiore per il parametro $k$ per ottenere la stessa bassa probabilità di trovare un insieme di collaboratori in modo casuale).

## 6 - Osservazioni

### 6.1 Compromessi

Esistono un certo numero di compromessi tra i due schemi. Lo schema a fiducia distribuita ha il vantaggio che tutta l'elaborazione avviene al momento della creazione della richiesta. Nello schema di collegamento, d'altra parte, il cliente ha un breve ritardo nell'attesa della seconda parte del suo certificato; la risposta a una sfida successiva, inoltre, può richiedere ulteriori comunicazioni.

Uno svantaggio correlato dello schema di collegamento è che dipende dal fatto che almeno alcune parti (clienti o, forse, il TSS) conservino i propri certificati.

Lo schema di fiducia distribuita risulta tecnologicamente più oneroso per il sistema: la possibilità di avere a disposizione e richiedere una rapida risposta firmata a piacimento.

Lo schema di collegamento individua la data di un documento solo tra l'istante della richiesta precedente e quella successiva, il che lo rende più adatto a un contesto in cui viene inviata una quantità relativamente grande di documenti per la marcatura temporale, rispetto alla scala di importanza della tempistica.

Vale la pena sottolineare che le proprietà di limitazione temporale dello schema di collegamento non dipendono dall'uso di firme digitali.

### 6.2 Vincoli temporali

Vorremmo sottolineare che i nostri schemi vincolano l'evento della marcatura temporale sia in avanti che indietro nel tempo. Tuttavia, considerando il lasso di tempo tra la creazione di un documento e il momento in cui viene marcato grande a piacere, allora nessun metodo può fare meglio che fornire una limitazione futura del momento in cui il documento stesso è stato creato. In generale, pertanto, la marca temporale dovrebbe essere considerata solo come prova che un documento non è stato retrodatato.

D'altra parte, se l'evento di marcatura temporale può essere reso parte del processo di creazione del documento, allora il vincolo è valido in entrambe le direzioni. Si consideri, ad esempio, la sequenza di conversazioni telefoniche che passano attraverso un determinato dispositivo. Per elaborare la chiamata successiva su questo dispositivo, si potrebbe richiedere che vengano fornite le informazioni di collegamento della chiamata precedente. Analogamente, al termine della chiamata, le informazioni di collegamento verrebbero passate alla chiamata successiva. In questo modo, l'evento di creazione di un documento (la telefonata) include un evento di marcatura temporale e quindi l'ora della telefonata può essere fissata in un punto preciso del tempo. La stessa idea potrebbe essere applicata alle sequenze di transazioni finanziarie, come le compravendite di azioni o gli scambi di valuta, o qualsiasi sequenza di interazioni elettroniche che avvengano attraverso una determinata connessione fisica.

### 6.3 Considerazioni teoriche

Anche se non la useremo in questa sede, suggeriamo che una precisa definizione teorica della complessità del livello più forte possibile di sicurezza della marcatura temporale potrebbe essere ricavata dalle definizioni date da Goldwasser e Micali [9], Goldwasser, Micali e Rivest [10] e Galil, Haber e Yung [8] per varie applicazioni crittografiche. Le procedure di marcatura temporale e verifica dipenderebbero tutte da un _parametro di sicurezza_ $p$. Uno schema di marcatura temporale risulterebbe _polinomialmente sicuro_ se la probabilità di successo di un avversario con limiti polinomiali che tenta di produrre una marca temporale falsa è minore di un qualsiasi polinomio in $1/p$ per $p$ sufficientemente grande.

Sotto l'ipotesi che esistano permutazioni unidirezionali claw-free, possiamo dimostrare che il nostro schema di collegamento è polinomialmente sicuro. Se assumiamo che esista al più una frazione costante di clienti corruttibili, e assumendo anche l'esistenza di funzioni unidirezionali (e quindi l'esistenza di generatori pseudocasuali e di uno schema di firma sicuro), possiamo dimostrare che il nostro schema di fiducia distribuito è polinomialmente sicuro.

Nel paragrafo 4.1 abbiamo menzionato la differenza tra le funzioni hash "senza collisioni" e quelle "universali e unidirezionali". L'esistenza di funzioni unidirezionali è sufficiente a garantire anche l'esistenza di funzioni hash universali unidirezionali. Tuttavia, per dimostrare la sicurezza dei nostri schemi di marcatura temporale, abbiamo apparentemente bisogno di una maggiore garanzia della difficoltà di produrre collisioni di hash, data dalla definizione di funzioni di hash senza collisioni. Per quanto è attualmente noto, un'ipotesi di complessità più forte - ovvero l'esistenza di coppie di permutazioni $senza collisioni$ - è necessaria per dimostrare l'esistenza di tali funzioni. (Si veda anche [5] e [6] per ulteriori discussioni sulle proprietà teoriche delle funzioni hash crittografiche).

Le funzioni hash unidirezionali sono lo strumento utilizzato per creare uno schema di firma sicuro. L'apparente bisogno di un'assunzione più forte suggerisce una differenza, forse essenziale, tra le firme e le marche temporali. È interesse del firmatario agire correttamente seguendo le istruzioni di uno schema di firma sicuro (ad esempio, scegliendo casualmente una funzione hash da un opportuno insieme). Per la marcatura temporale, d'altra parte, un utente disonesto o un TSS corrotto potrebbe trovare convenienza a non seguire le istruzioni standard (ad esempio, scegliendo una funzione hash per la quale sia facile trovare collisioni); lo schema di marcatura temporale deve essere ideato in modo tale che questo comportamento scorretto non produca alcun guadagno.

Se possibile, vorremmo ridurre le assunzioni necessarie per la marcatura temporale sicura alla semplice assunzione che esistano funzioni unidirezionali. Questa risulta essere per noi la minima assunzione ragionevole, dal momento che tutta la crittografia basata sulla complessità richiede l'esistenza di funzioni unidirezionali [12, 13].

### 6.4 Considerazioni pratiche

Quando si passa dal dominio teorico della complessità a quello dei sistemi crittografici reali, sorgono nuove problematiche. In un certo senso, la marcatura temporale pone una richiesta maggiore alle funzioni unidirezionali rispetto ad altri tipi di applicazioni. Ad esempio, se un sistema elettronico di trasferimento fondi fa uso di una funzione unidirezionale per l'autenticazione, e questa funzione viene violata, tutti i trasferimenti effettuati _prima_ della violazione risultano ancora validi. Nel caso delle marcature temporali, invece, se la funzione di hash viene violata, tutte le marche temporali emesse prima della violazione vengono messe in discussione.

Una parziale soluzione a questo problema è fornita dalla possibilità di rinnovare le marche temporali. Supponiamo di avere due implementazioni di marcatura temporale e che ci sia ragione di credere che la prima implementazione sarà presto violata. I certificati emessi con la vecchia implementazione possono essere rigenerati utilizzando quella nuova. Quindi, si consideri un certificato con marca temporale creato con la vecchia implementazione che viene rimarchiato con la nuova implementazione prima che quella vecchia sia violata. Prima della violazione della vecchia implementazione, l'unico modo per creare un certificato era quello legittimo. Pertanto, marcando il certificato stesso con la nuova implementazione, non solo si ha la prova dell'esistenza del documento al momento della nuova marcatura, ma anche della sua esistenza al momento indicato nel certificato originale.

Un altro problema da considerare è che la sola produzione di collisioni di hash non è sufficiente a rompere lo schema di marcatura temporale. Piuttosto, è necessario trovare _documenti significativi_ che portino alla generazione di collisioni. Specificando pertanto il formato di una classe di documenti, è possibile complicare la ricerca di collisioni significative. Ad esempio, la densità di testi composti da soli caratteri ASCII tra tutte le possibili stringhe di bit di lunghezza $N$ bytes è $(2^7/2^8)^N$, ovvero $(1/2)^N$, semplicemente perché il bit più significativo di ciascun byte è sempre 0. Ancora peggio, la densità di un testo inglese accettabile può essere limitata superiormente da una stima dell'entropia dell'inglese giudicata dai madrelingua [21]. Questo valore è di circa 1 bit per carattere ASCII, che porta a una densità di $(2^1/2^8)^N$, ovvero $1/128^N$.

Lasciamo ai lavori futuri il compito di formalizzare l'aumento della difficoltà di calcolo delle collisioni se i documenti validi sono distribuiti in maniera sparsa e forse casuale nello spazio di input. Allo stesso modo, il fatto che uno schema di collegamento $k-way$ richieda al potenziale attaccante di calcolare collisioni $k-way$ anzichè coppie di collisioni può essere sfruttato per allentare i requisiti della funzione hash. Può risultare significativo investigare la possibilità che esistano funzioni hash per le quali _non esistano_ collisioni $k-way$ tra stringhe in un sottoinsieme opportunatamente ristretto dello spazio di input: la sicurezza di tale sistema non dipenderebbe più dalla assunzione di complessità.

### 7 Applicazioni

Utilizzando le funzioni di hash, gli schemi di firma e i generatori pseudocasuali teoricamente migliori (crittograficamente sicuri), abbiamo progettato dei sistemi di marcatura temporale aventi le desiderate proprietà teoriche. Tuttavia, vorremmo sottolineare anche la natura pratica della nostra soluzione: poiché esistono implementazioni _pratiche_ di questi strumenti crittografici, entrambi i nostri sistemi di marcatura temporale possono essere implementati come descritto con un costo accettabile. Alcune pratiche funzioni di hash, come quella di Rivest, risultano piuttosto veloci, anche su PC di fascia bassa [19].

Quali tipi di documenti potrebbero beneficiare di una marcatura temporale digitale sicura? Per i documenti che stabiliscono l'anteriorità di un'invenzione o un'idea, la marcatura temporale ha un chiaro valore. Una caratteristica particolarmente desiderabile della marcatura temporale digitale è rendere dimostrabile la precendenza della proprietà intellettuale senza rivelarne il contenuto. Questo potrebbe avere un effetto significativo sia sul diritto d'autore che sui brevetti e potrebbe essere applicato ovunque, dal software alla formula segreta della Coca-Cola.

Ma cosa fare con i documenti per i quali non sia così significativa la marcatura temporale quanto l'integrità del documento stesso? Anche questi documenti possono beneficiare della marcatura temporale, nelle seguenti circostanze. Supponiamo che si possa stabilire che le conoscenze necessarie o la motivazione per la manomissione di un documento non esistevano fino a un istante identificabile e successivo alla creazione del documento. Ad esempio, si può immaginare un'azienda che tratta quotidianamente un gran numero di documenti, alcuni dei quali si rivelano in seguito incriminanti. Se tutti i documenti dell'azienda venissero regolarmente marcati al momento della loro creazione, diventerebbe evidente quali documenti sono incriminanti e come dovrebbero essere modificati, così sarebbe stato troppo tardi per poterli manomettere. Chiameremo tali documenti _a manomissione imprevedibile_. Diventa chiaro che molti documenti aziendali sono a manomissione imprevedibile. Pertanto, se la marcatura temporale venisse incorporata nel processo aziendale, si potrebbe aumentare notevolmente la credibilità di molti documenti.

Una variante che può essere particolarmente utile per i documenti aziendali è quella di marcare temporalmente un registro di documenti piuttosto che ogni singolo documento. Potrebbe essere calcolato, ad esempio, il valore di hash di ogni documento aziendale creato in un giorno e aggiunto al registro giornaliero dei documenti dell'azienda. Successivamente, alla fine della giornata lavorativa, la marcatura temporale potrebbe essere applicata al solo registro. In questo modo si eliminerebbe la spesa per la marcatura di ogni singolo documento, pur consentendo di rilevare eventuali manomissioni;si potrebbe anche determinare se alcuni di questi documenti siano stati distrutti del tutto.

Naturalmente, la marcatura temporale digitale non è limitata ai documenti di testo. Qualsiasi stringa di bit può essere marcata temporalmente comprese le registrazioni audio digitali, fotografie e video. Essendo la maggior parte di questi documenti a manomissione imprevedibile, la marcatura temporale può aiutare a distinguere una fotografia originale da una manomessa, un problema che negli ultimi tempi ha ricevuto una notevole attenzione da parte della stampa generalista [1, 11]. In effetti, è difficile pensare a qualsiasi altra "correzione" algoritmica che possa incrementare la credibilità di fotografie, video o registrazioni audio rispetto alla marcatura temporale.

## 8 Sommario

In questo articolo abbiamo dimostrato che il crescente utilizzo di documenti di testo, audio e video in formato digitale e la facilità con cui tali documenti possono essere modificati crea un nuovo problema: come si può certificare la data di creazione e ultima modifica di un documento? I metodi di certificazione, o marcatura temporale, devono soddisfare due criteri. Il primo requisito è datare i bit effettivi del documento, senza ipotesi sul supporto fisico su cui lo stesso è registrato. In secondo luogo, la data e l'ora della marcatura temporale non devono essere falsificabili.

Abbiamo proposto due soluzioni a questo problema. Entrambe prevedono l'uso di funzioni hash $unidirezionali$, i cui output vengono elaborati al posto degli effettivi documenti, e di firme digitali. Le soluzioni si differenziano solo per modo in cui si rende non falsificabile la marcatura temporale. Nel primo caso, i valori di hash dei documenti presentati a un TSS sono collegati tra loro, e i certificati che attestano il collegamento a un determinato documento vengono distribuiti ad altri clienti sia a monte che a valle di quel documento. Nella seconda soluzione, diversi membri dell'insieme di clienti devono marcare temporalmente il valore di hash. I membri sono scelti mediante un generatore di numeri pseudocasuali che utilizza il valore di hash del documento stesso come seme. Questo rende impossibile scegliere deliberatamente quali clienti devono o non devono marcare un determinato hash. Il secondo metodo può essere implementato in totale assenza di un TSS centralizzato.

Infine, abbiamo considerato la possibilità di estendere la marcatura temporale per migliorare l'autenticità di documenti per i quali il tempo di creazione o modifica non sia l'elemento critico. Questo è il caso di un'ampia classe di documenti che abbiamo definito "a manomissione imprevedibile". Ipotizziamo inoltre che nessuno schema puramente algoritmico possa migliorare la credibilità di un documento rispetto alla marcatura temporale.

### Ringraziamenti

Siamo grati per le utili discussioni con Don Beaver, Shimon Even, George Furnas, Burt Kaliski, Ralph Merkle, Jeff Shrager, Peter Winkler, Yacov Yacobi e Moti Yung per le utili discussioni.

## Riferimenti bibliografici

[1] J. Alter - When photographs lie. _Newsweek_, pp. 44-45, 30 Luglio, 1990

[2] M. Blum e S. Micali - How to generate cryptographically strong sequences of pseudo-random bits. _SIAM Journal on Computing_, 13(4):850-864, Novembre 1984

[3] G. Brassard e M. Yung - One-way group actions. In _Advances in Cryptology-Crypto '90_, these proceedings. Lecture Notes in Computer Science, Springer-Verlag, Berlino, 1991

[4] I. Damgård - Collision-free hash functions and public-key signature schemes. In _Advances in Cryptology-Eurocrypt '87_, pp. 203-217. Lecture Notes in Computer Science, vol. 304, Springer-Verlag, Berlino, 1988

[5] I. Damgård - A design principle for hash functions. In _Advances in Cryptology-Crypto '89_ (ed. G. Brassard), pp. 416-427. Lecture Notes in Computer Science, vol. 435, Springer-Verlag, Berlino, 1990

[6] A. DeSantis e M. Yung - On the design of provably secure cryptographic hash functions. In _Advances in Cryptology-Eurocrypt '90_. Lecture Notes in Computer Science, Springer-Verlag, Berlino, in attesa di pubblicazione

[7] W. Diffie e M.E. Hellman - New directions in cryptography. _IEEE Trans. on Inform. Theory_, vol. IT-22, pp. 644-654, Novembre 1976

[8] Z. Galil, S. Haber e M. Yung - Interactive public-key cryptosystems. Candidato alla pubblicazione, 1990

[9] S. Goldwasser e S. Micali - Probabilistic encryption. _JCSS_, 28:270-299, Aprile 1984

[10] S. Goldwasser, S. Micali, e R. Rivest - A secure digital signature scheme. _SIAM Journal on Computing_, 17(2):281-308, 1988

[11] Andy Grundberg - Ask it no questions: The camera can lie. _The New York Times, section 2_, pp. 1, 29, 12 Agosto 1990

[12] R. Impagliazzo, L. Levin, e M. Luby - Pseudorandom generation from one-way functions. In _Proc. 2lst STOC_, pp. 12-24. ACM, New York, 1989

[13] R. Impagliazzo e M. Luby - One-way functions are essential for complexity-based cryptography. In _Proc. 30th FOGS_, pp. 230-235. IEEE, New York, 1989

[14] H. M. Kanare - Writing the laboratory notebook - p. 117. _American Chemical Society, Washington, D.C._, 1985

[15] R.C. Merkle - Secrecy, authentication, and public-key systems. Ph.D. thesis, Stanford University, 1979

[16] R.C. Merkle - One-way hash functions and DES. In _Advances in Cryptology-Crypto '89_ (ed. G. Brassard), pp. 428-446. Lecture Notes in Computer Science, vol. 435, Springer-Veriag, Berlino, 1990

[17] M. Naor e M. Yung - Universal one-way hash functions and their cryptographic applications. In _Proc. 21st STOC_, pp. 33-43. ACM, New York, 1989

[18] M.O. Rabin - Digitalized signatures. In _Foundations of Secure Computation_ (ed. R.A. DeMillo et al.), pp. 155-168. Academic Press, 1978

[19] R. Rivest - The MD4 message digest algorithm. In _Advances in Cryptoloqy-Crypto '90_, these proceedings. Lecture Notes in Computer Science, Springer-Verlag, Berlino, 1991

[20] J. Rompel - One-way functions are necessary and sufficient for secure signatures. In _Proc. 22nd STOC_, pp. 387-394. ACM, New York, 1990

[21] C. Shannon - Prediction and entropy of printed English. _Bell System Technical Journal_, vol. 30 pp. 50-64, 1951

[22] A.C. Yao - Theory and applications of trapdoor functions. In _Proc. 23rd FOCS_, pp. 80-91. IEEE, New York, 1982

