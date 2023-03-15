---
title: "For-Pay Remailers"
description: "Hal Finney - 28 Ottobre, 1993"
date: 2023-03-10T03:00:04+01:00
draft: false
weight: 380
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206201749/http://finney.org/~hal/pay_remail.html) - 28 Ottobre 1994

E se si potesse guadagnare gestendo un remailer?

Al momento, la maggior parte degli operatori di remailer opera per altruismo. Questo è positivo per molti aspetti, ma ha i suoi problemi, come hanno dimostrato gli eventi recenti:

- mancanza di motivazione a mantenere in funzione i remailer di fronte alle problemi e ai possibili rischi legali
- facilità di attacchi di spam da parte di utenti malintenzionati
- mancanza di incentivi per un servizio di remailing di qualità commerciale.

Sono sicuro che tutti noi possiamo pensare ad altro. So che sarebbe molto più facile giustificare il fatto di continuare a gestire il remailer per me stesso se portasse qualche dollaro al mese.

Credo che siano stati fatti alcuni esperimenti di remailer a pagamento. Sameer, credo, sta facendo pagare alcuni servizi, anche se forse era solo per gli indirizzi di ritorno anonimi. Molto tempo fa Karl Barrus aveva un servizio che richiedeva "francobolli digitali" pre-emessi, ma non credo che molti lo usassero.

I tempi potrebbero essere maturi per considerare la questione più seriamente. Diversi fattori si stanno unendo:

- alcuni sforzi per la standardizzazione dei comandi dei remailer e la cooperazione degli operatori (ad esempio questa lista)
- un uso più ampio di script e programmi di utilità per aiutare le persone a usare i remailer
- diversi sistemi concorrenti di denaro reale concorrenti che sono stati messi online proprio nell'ultimo mese o giù di lì che che permettono di essere pagati per le cose in rete

Per approfondire questi aspetti:

È evidentemente difficile gestire un servizio di remailer a pagamento se altri offrono il servizio equivalente gratuitamente. Poiché è piuttosto facile avviare un remailer, il costo marginale per farlo è basso, quindi anche i profitti sono bassi. Tuttavia, sebbene sia facile avviare un remailer, non è altrettanto facile mantenerlo in funzione di fronte alle lamentele dei destinatari di mail abusiva o di post inappropriati; alle seccature dei sysop, dei proprietari, dei net feed o di altri soggetti in alto nella grande catena di comando; ai possibili problemi con le forze dell'ordine quando si verificano comunicazioni illegali; alle possibili minacce di azioni legali (come quelle degli scientologist quando vengono pubblicati i loro documenti sacri), ecc. Quindi non dobbiamo farci ingannare dal fatto che la gestione di un remailer sia a costo zero.

D'altra parte, devo dire chiaramente che non mi aspetto di fare una fortuna con questo servizio. Qualcosa dell'ordine di un centesimo a messaggio mi sembra ragionevole solo come ipotesi. Forse dovrebbe essere un fattore di 10 più alto o più basso.

Un problema è naturalmente la difficoltà aggiuntiva che questo causerà nell'uso del remailer. Ci sono diverse aspetti da considerare. Da un lato si potrebbe sostenere che è già troppo difficile usare i remailer, e qualsiasi ulteriore difficoltà legata all'inclusione di qualche tipo di token di pagamento ucciderebbe il mercato. D'altra parte, posso concordare in spirito con i sentimenti espressi qui di recente sulla bassa qualità che sembra caratterizzare gran parte dell'uso dei remailer.

Non guardo i messaggi, ma di tanto in tanto vedo dei rimbalzi, e molto spesso si tratta di brutte fiamme o di materiale simile privo di valore. Ora, spero di vedere i residui, che il tipo di persone sprovvedute che commettono gli errori che mi fanno vedere i messaggi siano quelle che hanno meno probabilità di usare il servizio in modo proficuo. Ma è comunque scoraggiante. In questo contesto, forse sarebbe utile rendere il sistema un po' più difficile da usare, in modo da escludere i molestatori occasionali. (O, più realisticamente, questo potrebbe solo trattenere i molestatori eccezionalmente motivati).

In ogni caso, credo che la presenza degli script di remailing possa rendere l'uso di un remailer a pagamento non molto più difficile di uno gratuito. Se il costo è basso come ho suggerito e l'inclusione dei token di pagamento è quasi automatica, l'aggiunta di costi non dovrebbe avere un impatto negativo sull'uso, certamente non su un uso significativo e utile.

E anche un costo modesto potrebbe arrestare lo spam all'ingrosso che Detweiler e/o il recente "Scythe" sembrano amare. Almeno saremmo pagati per sopportare il fastidio delle lamentele.

Ora, la domanda successiva riguarda i dettagli del pagamento. Francamente, non credo che nessuno dei sistemi attuali sia adatto a noi a causa delle nostre esigenze particolari, ma le cose stanno cambiando rapidamente. Permettetemi di descrivervi qualcosa sul loro funzionamento.

Conosco due sistemi basati su VISA/Mastercard. Uno si chiama First Virtual (<http://www.fv.com>). Sono orientati alla vendita d'informazioni e dicono di non essere per i fornitori di servizi, ma in pratica mi è sembrato che potessero essere usati per i servizi. Quando un cliente vuole pagare, vi invia il suo ID FV. Voi lo inviate a FV e loro inviano un messaggio e-mail al cliente chiedendo se autorizza il pagamento. Se il cliente risponde "sì", FV accredita il vostro conto. Riceverete un assegno ogni mese. I clienti che dicono sempre "no" vengono espulsi dal sistema (così come i commercianti che presentano fatture false). FV addebita 29 centesimi più il 2% per transazione, ma gli esercenti possono raggruppare più ordini di un singolo cliente prima di inviarli.

Ci sono alcuni problemi con un sistema del genere, molti dei quali sono in qualche modo generici alla nostra situazione. Il più importante è che nella maggior parte dei casi non sappiamo chi sono i nostri clienti. In effetti, il punto centrale della rete di remailer è che non lo sappiamo in nessun caso, tranne per il primo salto della catena. Se chiedessimo ai clienti di esporre l'ID del loro account FV a ogni passaggio, sarebbe molto più facile tracciare i messaggi attraverso la rete (anche se gli ID sono nascosti nella busta di crittografia, sembra rischioso). Se poi inviamo un messaggio a FV dicendo che dobbiamo addebitare l'ID XXX, e FV risponde con un'e-mail all'indirizzo di casa della persona, questo offre maggiori possibilità di tracciamento.

Una soluzione potrebbe essere quella di addebitare il costo solo all'ingresso nella rete del remailer. Forse gli operatori dei remailer si addebiterebbero a vicenda e il primo remailer addebiterebbe un importo maggiore per gestire una catena "tipica"? Ci sono molte possibilità interessanti.

Un altro problema è che le spese generali di FV richiederebbero il raggruppamento dei messaggi prima di inviarli. Vorrei chiarire che il lotto deve essere composto da tutti gli addebiti a un singolo utente. Non serve a nulla inviare un messaggio a FV chiedendo di addebitare un centesimo a ciascuno dei 100 conti VISA. No, dovreste contare i messaggi di ciascun utente, separatamente, e quando l'utente XXX ha inviato, ad esempio, messaggi per un valore di 1 dollaro, potreste inviare la richiesta a FV e ricevere indietro 70 centesimi circa.

Quindi questo aggiunge un po' di spese generali e di registrazioni che attualmente non dobbiamo fare, anche se forse non è così difficile. Ma solleverebbe nuovi problemi di autenticazione degli ID FV e condividerebbe alcuni degli impatti negativi sulla privacy e i problemi di collegamento dei messaggi menzionati in precedenza.

L'altro sistema basato su VISA si chiama OpenMarket. L'ho letto solo stasera, quindi non lo conosco altrettanto bene (<http://www.openmarket.com>). È piuttosto legato al WWW, quindi non sembra funzionare per noi. I clienti si collegano a un particolare server WWW che li autentica e addebita la loro carta VISA in modo appropriato, quindi vengono reindirizzati al commerciante con una sorta di token che indica che hanno pagato.

NetBank (e-mail a netbank-intro@agents.com) è un sistema simile al contante digitale. I clienti ottengono dei token, che sono sostanzialmente dei grandi numeri segreti che hanno un valore in denaro. Li inviano ai commercianti e questi li inviano alla banca che li accredita sul conto. La NetBank invia un assegno ogni mese.

L'aspetto interessante è il modo in cui i clienti acquistano i gettoni di denaro. Un modo è collegarsi a un numero 900 con il proprio modem. Il cliente viene addebitato di 10 dollari e riceve un gettone di denaro digitale del medesimo valore. Un altro modo è inviare un assegno via fax. Non mi è chiaro come si ottiene il gettone in contanti in questo caso; credo che lo inviino per e-mail a un indirizzo specificato dall'utente. Dal punto di vista della privacy, questi sistemi non sono il massimo: i numeri 900 hanno l'identificazione automatica del numero, quindi, a meno che non siate disposti a recarvi a un telefono pubblico per prendere i contanti, potrebbero essere collegati al vostro numero di telefono. E il sistema di fax deve avere un qualche tipo di indirizzo di ritorno che vi colleghi a voi.

L'altro problema di NetBank è che il taglio più piccolo che si può spendere è di 25 centesimi. A causa della natura simile al contante dei token, non vedo un modo naturale per accumulare diversi messaggi in un unico pagamento. Forse potremmo sovrapporre a NetBank il nostro sistema di contanti digitali di poco valore, in cui gli utenti potrebbero acquistare i nostri contanti anonimi per 25 centesimi e ottenere abbastanza gettoni per 25 messaggi, poi ci regoleremmo tra di noi (o in realtà con la banca di anon-mail-token). Infatti questo potrebbe aiutare anche a risolvere i problemi di privacy. Il contante digitale anonimo è però fortemente brevettato.

Con un sistema simile al contante, ogni messaggio includerebbe un token numerico nell'intestazione che rappresenta il contante digitale. Il remailer lo estrarrebbe e lo invierebbe per l'accredito. Questo è un sistema semplice e potrebbe essere in gran parte automatico. Tuttavia, ci sono alcuni problemi di riutilizzo del contante da parte degli imbroglioni.

NetBank addebita 4 dollari al mese, più, per il contante basato sul numero 900, il 20% di sconto sul valore nominale.

L'ultimo sistema che descriverò è DigiCash di David Chaum (<http://www.digicash.com>). Chaum è l'inventore del contante digitale e sicuramente sa il fatto suo; inoltre, come ho già detto, ha la proprietà intellettuale abbastanza ben garantita dal punto di vista dei brevetti. Anche il sistema di pagamento DC è attualmente basato sul WWW. Il cliente deve eseguire un programma speciale sul suo computer, separato dal suo browser web. Questo programma contiene il suo denaro digitale, concettualmente simile a quello di NetBank, ma più sofisticato dal punto di vista crittografico. Quando il cliente vuole acquistare qualcosa, il server web del commerciante si collega al programma DC del cliente e trasferisce il contante al commerciante.

DigiCash dice che sta progettando un sistema basato sulla posta elettronica, ma per ora si concentra sul WWW. Al momento sono solo in fase beta e non utilizzano denaro reale. Non so quando diventeranno reali e basati sull'e-mail e non so se hanno detto quale sarà la loro commissione. Ma quando sarà disponibile, potrebbe essere l'approccio migliore se transazioni di piccolo valore possono essere supportate. DigiCash è completamente anonimo, nel senso che una volta che un cliente riceve il denaro, questo viene "accecato" in uno speciale metodo crittografico, in modo che la banca non possa associarlo a quel cliente (e nessun altro può farlo). Questo tipo di anonimato si adatta molto bene ai nostri requisiti di remailer.

So che sono molte informazioni da analizzare, ma soprattutto voglio che le persone siano consapevoli delle possibilità. La maggior parte di queste informazioni è molto, molto nuova, in genere ha solo poche settimane. Probabilmente nei prossimi mesi vedremo apparire molte altre opzioni. Sono sicuro che presto ci saranno sistemi di pagamento che forniranno la base tecnica per il remailing a pagamento. Non mi aspetto che qualcuno si arricchisca con questo, ma potrebbe aiutare a compensare i rischi che tutti noi affrontiamo e potrebbe servire a migliorare la qualità della rete di remailing.

Hal Finney<br>
hal@rain.org<br>
[Hal Finney Home Page](hal-finney-home-page.md)
