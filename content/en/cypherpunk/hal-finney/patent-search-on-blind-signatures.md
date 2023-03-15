---
title: "Patent Search on Blind Signatures"
description: "Hal Finney"
date: 2023-03-12T18:41:17+01:00
draft: false
weight: 395
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://web.archive.org/web/20041206190901/http://finney.org/~hal/chaum_patents.html)

Un po' di tempo fa qualcuno ha postato su una nuova società che effettua ricerche su brevetti tramite richieste via e-mail. Per un'altra settimana stanno effettuando ricerche gratuite come offerta introduttiva. Ho fatto una ricerca sui sistemi di contante a firma cieca e questi sono i brevetti trovati. Potrebbe essere utile per chi sta pensando di implementare il contante elettronico. Il testo completo dei brevetti è disponibile a 4,95 dollari. Il tipo di ricerca che ho effettuato gratuitamente costerà 149 dollari una volta terminata la prova gratuita (che è già terminata).

Per maggiori informazioni inviare un messaggio con la sola dicitura "help" nel corpo a spo_patent@spo.eds.com.

2 &nbsp; 04977595 &nbsp; 19901211 &nbsp; 380/24 &nbsp; Method and apparatus for implementing ++electronic++ ++cash++<br>
Inventor: Ohta; Kazuo<br>
Assignee: Nippon Telegraph and Telephone Corporation<br>
Abstract:<br>
<ul>
    In un metodo d'implementazione del contante elettronico, un utente fa sì che una banca applichi una firma cieca alle informazioni sull'utente Vi prodotte, mediante una funzione unidirezionale, da informazioni segrete Si contenenti informazioni d'identificazione, ottenendo così informazioni firmate sull'utente. Inoltre, l'utente fa in modo che la banca applichi una firma cieca alle informazioni d'autenticazione Xi prodotte, mediante una funzione unidirezionale, da informazioni casuali Ri, ottenendo così informazioni d'autenticazione firmate. L'utente utilizza un gruppo d'informazioni contenente le informazioni dell'utente firmate, le informazioni d'autenticazione firmate, le informazioni dell'utente e le informazioni d'autenticazione come contante elettronico per il pagamento a un negozio. Il negozio verifica la validità delle informazioni dell'utente firmate e delle informazioni d'autenticazione firmate e produce e invia all'utente una richiesta. In risposta alla richiesta, l'utente produce una risposta Yi utilizzando informazioni segrete e informazioni casuali e la invia al negozio. Dopo aver verificato la validità della risposta, il negozio accetta il contante elettronico.
</ul>

3 &nbsp; 05224162 &nbsp; 19930629 &nbsp; 380/24 &nbsp; ++Electronic++ ++cash++ system<br>
Inventor: Okamoto; Tatsuaki<br>
Assignee: Nippon Telegraph and Telephone Corporation<br>
Abstract:<br>
<ul>
    In un sistema di contanti elettronici, K serie di firme cieche sono derivate da informazioni segrete contenenti informazioni sull'identificazione di un utente, K/2 serie di esse sono aperte e una banca allega una firma cieca alle restanti K/2 serie d'informazioni. L'utente ottiene una licenza firmata dalla firma cieca. L'utente genera informazioni di firma cieca dalla licenza e da una somma di denaro desiderata, ottenendo una firma cieca della banca sulle informazioni e contanti elettronici firmati dalla banca dalla firma cieca. L'utente presenta a un negozio una radice di potenza residua di un nodo in una struttura gerarchica di denaro e il contante elettronico, corrispondente alla somma di denaro da utilizzare, e il negozio ne verifica la validità e, se sono validi, propone informazioni di richiesta all'utente. L'utente propone al negozio, come informazione di risposta, una radice di potenza residua del nodo corrispondente alla somma di denaro da utilizzare. Il negozio verifica la validità delle informazioni di risposta e, se queste sono valide, conferma il pagamento in contanti elettronici della somma di denaro da utilizzare.
</ul>

4 &nbsp; 04759063 &nbsp; 19880719 &nbsp; 380/30 &nbsp; ++Blind++ signature systems<br>
Inventor: Chaum; David L.<br>
Abstract:<br>
<ul>
    Un sistema crittografico consente, in un caso ideale, a un fornitore di trasformare crittograficamente una pluralità di messaggi in chiavi segrete; i messaggi trasformati vengono firmati digitalmente da un firmatario; e i messaggi trasformati firmati vengono restituiti al fornitore per essere trasformati da quest'ultimo nelle stesse chiavi segrete, in modo tale che il fornitore sviluppi una firma digitale relativa a ciascun messaggio originale. Una proprietà importante di questi sistemi è che il firmatario non può determinare quale messaggio trasformato ricevuto per la firma corrisponda a quale firma digitale, anche se sa che tale corrispondenza deve esistere.
</ul>

6 &nbsp; 04914698 &nbsp; 19900403 &nbsp; 380/30 &nbsp; One-show ++blind++ signature systems<br>
Inventor: Chaum; David<br>
Abstract:<br>
<ul>
    I numeri che rappresentano denaro contante possono essere spesi una sola volta ciascuno, altrimenti verrebbe rivelato il conto da cui sono stati prelevati. Più in generale, una tecnica per l'emissione e l'esibizione di firme digitali cieche garantisce che, se queste vengono mostrate in risposta a diverse sfide, alcune informazioni che il firmatario assicura di contenere saranno rivelate e potranno essere recuperate in modo efficiente. Alcune implementazioni consentono alle firme di essere incondizionatamente irrintracciabili se mostrate non più di una volta. Le estensioni consentono di codificare i valori nelle firme quando vengono mostrate e di ottenere la modifica del valore non mostrato in forma aggregata e non rintracciabile.
</ul>

11 &nbsp; 04949380 &nbsp; 19900814 &nbsp; 380/30 &nbsp; Returned-value ++blind++ signature systems<br>
Inventor: Chaum; David<br>
Abstract:<br>
<ul>
    Una parte pagante ottiene da una parte firmataria, tramite un sistema di firma cieca, una prima firma digitale a chiave pubblica avente un primo valore in una transazione di prelievo; il pagante riduce il valore della prima firma ottenuta dal primo valore a un secondo valore e fornisce questa forma di firma a valore ridotto al firmatario in una transazione di pagamento; il firmatario restituisce una seconda firma digitale al pagante tramite un sistema di firma cieca durante l'esecuzione online della transazione di pagamento; la carta deriva dalla prima e dalla seconda firma una terza firma avente un valore aumentato corrispondente alla rilevanza della differenza tra il primo e il secondo valore. Inoltre, sono previste le seguenti caratteristiche aggiuntive: i pagamenti non sono collegabili ai prelievi; si può impedire a un negozio tra il pagante e il firmatario di ottenere più valore di quello desiderato dal pagatore; il primo valore non deve essere rivelato al firmatario o all'intermediario nella transazione di pagamento; la differenza restituita può essere accumulata in più transazioni di pagamento; la differenza restituita può essere suddivisa tra una pluralità di transazioni di pagamento.
</ul>

19 &nbsp; 04759064 &nbsp; 19880719 &nbsp; 380/30 &nbsp; ++Blind++ unanticipated signature systems<br>
Inventor: Chaum; David L.<br>
Abstract:<br>
<ul>
    Un sistema di firma cieca migliorato che non richiede calcoli durante l'accecamento per prevedere quale tra una pluralità di possibili firme verrà apposta durante la firma, pur consentendo alla parte accecata di eliminare l'accecamento e recuperare il tipo di firma imprevista su ciò che è stato accecato. Un'ideale materializzazione esegue l'accecamento formando un prodotto comprendente una pluralità di generatori elevati a potenze normalmente segrete alla parte firmataria, ed elimina l'accecamento formando un prodotto con l'inverso moltiplicativo di una forma firmata dei generatori elevati alle potenze originali. Il ri-accecamento consente di trasformare una firma di un valore in una firma di una particolare forma accecata del valore.
</ul>

23 &nbsp; 04206315 &nbsp; 19800603 &nbsp; 380/23 &nbsp; ++Digital++ signature system and apparatus<br>
Inventor: Matyas; Stephen M.<br>
Assignee: International Business Machines Corporation<br>
Abstract:<br>
<ul>
    Una macchina per la firma digitale fornisce un metodo semplificato per la formazione e la verifica di una firma allegata a un messaggio digitale. Il mittente trasmette una firma con le consuete chiavi e con le voci della tabella di convalida che corrispondono alle chiavi non inviate e con la codifica compressa della tabella di convalida successiva. Il destinatario utilizza la codifica compressa della tabella di convalida successiva per formare le voci della tabella di convalida dalle chiavi di firma, in modo da avere una tabella di convalida completa. Questa tabella di convalida viene compressa e confrontata con la codifica compressa ricevuta dal mittente in un messaggio precedente.
</ul>

[Hal Finney Home Page](hal-finney-home-page.md)
