---
title: "Cyberspace Crypto Anarchy and Pushing Limits"
descriptio: "Timothy May - 3 Aprile, 1994"
date: 2023-01-29T17:55:46+01:00
draft: false
weight: 430
images: []
categories: []
contributors: ["21MillionClub", "brandosari"]
---

[Originale](https://groups.csail.mit.edu/mac/classes/6.805/articles/crypto/cypherpunks/may-pushing-limits.txt) - 3 Aprile, 1994

Questo messaggio verte su due argomenti di recente interesse (per alcuni):

1. Impostare un metodo di pagamento per la trasmissione di messaggi, per gestire i problemi di "mailbombing" e "flooding" in modo più naturale (località di riferimento, l'utente di un servizio paga, evitando gli effetti dell'esplosione del "Morris Worm" che sarebbe potuto accadere con Detweiler che ci ha bombardato, come ha notato Hal).

2. La questione principale del “Cyberspazio”. Essa deriva da recenti disaccordi e meriterebbe di essere discussa ampiamente. La crittografia renderà questa problematica di fondamentale importanza negli anni a venire.

Perché discuterne ora? Che cosa potremmo mai ricavare da questo dibattito?

Al momento sto leggendo il nuovo fantastico libro di Kip Thorne, intitolato “I buchi neri e salti temporali”. Si trova facilmente nelle librerie, disponibile in copertina rigida solo ora. (Sono $30, ma è un libro gigantesco, poi l’ho preso da Barnes and Noble per soli $24. A proposito di Barnes and Noble, il negozio a Santa Clara sta vendendo “Intro to Kolmogorov Complexity” di Li e Vitanyi per $44 a cui non è ancora stato applicato lo sconto del 20%, potrebbe essere un errore di prezzo siccome ne ho pagati $60 per il mio. Dategli un’occhiata se siete interessati... Mi pare vi fossero due copie.)

Thorne ha speso 30 anni della sua vita a studiare il collasso gravitazionale e i buchi neri, è anche stato coautore del famoso libro “Gravitation” del 1973, che ho personalmente utilizzato per il mio esame di relatività generale nello stesso anno.

Il punto? Nel libro, Thorne descrive il suo coinvolgimento con Carl Sagan nel ricavare la fisica dei viaggi nel tempo attraverso i wormhole. Egli ebbe un’epifania: nonostante qualcosa possa essere impossibile da realizzare in termini economici o ingegneristici, possiamo ottenere informazioni utili nell’esaminare quali sono i limiti assoluti del possibile. Fu così che Thorne e i suoi studenti studiarono l’idea e le implicazioni di una civiltà estremamente avanzata, che potesse mantenere aperto un wormhole. Le conclusioni sono affascinanti e diedero vita a un nuovo modo di interpretare la struttura dello spazio-tempo.

Spingersi oltre i limiti e poter osservare un comportamento “ideale” è rivitalizzante.

Il collegamento con la crittografia è questo: forse dovremmo ragionare più su effetti e implicazioni di crittografia forte, moneta digitale, remailer ideali, ecc., assumendo che determinate problematiche di natura pratica siano, o saranno presto, risolte. In realtà ragioniamo già secondo questa logica, ad esempio quando discutiamo dei mix ideali di Chaum oppure quando gli ingegneri discutono di amplificatori operazionali ideali--astrazioni utili per comparare il comportamento ideale con quello del mondo reale.

Ovviamente, molti di noi considerano “Il vero nome” di Vernor Vinge un eccellente (e breve) trattato che dimostra come le cose possano funzionare in un mondo basato su comunicazioni veloci, economiche e sicure. Altri autori hanno previsto un futuro diverso (e.g. “Shockwave Rider”, “1984”, “Snow Crash”). 

Per farla breve, ecco qui alcune proposte di ciò che penso sia un “comportamento ai limiti”. Non le approfondirò al momento.

* “Pay as you go” è il modo più naturale per gestire la maggior parte delle transazioni economiche. Ci sono eccezioni, ovviamente, come l’assicurazione, contratti derivati, ecc., ma possiamo argomentare che la maggior parte del denaro disponibile venga utilizzato per transazioni immediate. Un esempio calzante: per quale motivo i tuoi avversari non possono “bombardarti di mail spazzatura” in quantità esagerate? Le mail a cui facciamo riferimento vengono spedite in quantità relativamente piccole (al massimo giusto per riempire una casella, forse qualcosa in più per le persone famose) per un semplice motivo: qualcuno dovrà pur sostenere i costi di spedizione! Non esiste nessun metodo “gratuito” per “creare 19 copie di queste tonnellate di immondizia e spedirle ai tuoi nemici”. Il motivo per cui con certi software funziona--il remailer bombing di Detweiler, il Morris Worm del 1988, le catene di Sant’Antonio “Dave Rhodes”--è dovuto a determinati difetti nell’attuale modello della Rete:

  - il costo della trasmissione dei messaggi non è direttamente a carico del mittente (questo incoraggia un uso eccessivo di risorse scarse, in completo stile “tragedia dei beni comuni”)

  - siti e remailer obbediscono alle “istruzioni” per diffondere il messaggio, crearne copie, ecc.

* Considero quindi imperativo sviluppare il più velocemente possibile:

  - dei sistemi di pagamento per la trasmissione di messaggi (sostenni personalmente l’idea dell’“affrancatura digitale” come primo caso d’uso delle monete digitali, come del resto fecero altri; di fatto Ray Cromwell ha mostrato la sua proposta proprio oggi… E’ ora di rimboccarci le maniche. Per evitare che pensiate che io stia invocando l’altruismo, sono dell’idea che si faranno alcune fortune in questo ambito.)

  - protocolli volti a rendere anonimi oppure oscurare la propria identità, simil-Chaum.

  - un generale allontanamento dai sistemi “per tutti”, che incubano pensieri come “accesso equo” e simili. Se il “problema” è che le persone povere non possano--viene asserito--permettersi un abbonamento mensile di $17 per l’accesso alla Rete (ciò che Netcom fa pagare in oltre 25 città), allora la mia soluzione è semplicemente di creare sussidi per poter pagare la bolletta. (Non sto promuovendo l’idea, non penso nemmeno sia saggio creare sussidi per pagare abbonamenti o conti al ristorante, ma questo è sicuramente più ragionevole del “nazionalizzare” questi network e di conseguenza ridurre efficienza e creare confusione per tutti.)

* La connettività verrà alterata drammaticamente. Già ora la “distanza” è un concetto indipendente dalla distanza fisica nel cyberspazio. (Poco sorprendente in quanto questo era già evidente con il telefono, ma è un punto di vista che si rivela utile per il cyberspazio: uno spazio formato da connettività e distanze alterate.)

* sL’accesso locale ai servizi, il telefono o le linee di trasmissione che raggiungono le case o gli uffici possono essere dei potenziali bottleneck. Se, invece, una connessione viene effettuata a un nodo locale in cui vi sono diversi competitor (si intende quando non vi sarà più un monopolio concesso dallo Stato), la possibilità di “censura” cala vertiginosamente, e per svariati motivi.

  - perciò bisogna spingersi verso linee ad “accesso criptato”, da un terminale (casa, ufficio) a un punto con connettività illimitata.

  - questo è al pari della mia situazione con PacBell line e Netcom: a PacBell non “interessa” per quali scopi uso la linea locale, e una volta fuori, posso connettermi a un Netcom meno invadente piuttosto che a un AOL o Prodigy, stile Grande Fratello.

* Il cyberspazio è infinitamente colonizzabile. Nessun limite all’espansione. (Assunto: la creazione del cyberspazio avviene su macchine e network, ovviamente né gratuiti né infiniti. Ma il “nessun limite” deriva dal fatto che coloro vicini al “limite” possono semplicemente spostarlo allocando più risorse di CPU, più network, ecc.).

* Gli accessi “regionali” tramite crittografia possono essere controllati dai “proprietari”:

  - il principio “la mia casa, le mie regole” attuato localmente, senza necessità di un’autorità centrale statale.

  - sicurezza essenzialmente inviolabile (in termini crittografici)

* Oltretutto, una forte crittografia provvede alle “fondamenta” del cyberspazio… la malta, i mattoni, le travi di sostegno, i muri. Nient’altro può provvedere alla “continuità”…senza la crittografia i muri sono soggetti al crollo per minimo disturbo di un qualsiasi ente o persona con intenzioni maligne. Con la crittografia nemmeno una bomba all’idrogeno da 100 megaton può scalfire le mura.<br>
(Se pensate che stia esagerando, fate qualche calcolo sull’energia necessaria per rompere un modulo da 1000 digit decimali.)

* Nessuna “legge urbanistica” sarà necessaria, tantomeno possibile, nel cyberspazio. (“Snow Crash” di Neil Stephenson, nonostante sia una lettura affascinante e provocatoria, manca il segno: il cyberspazio è troppo estensibile e localmente manipolabile.)

* Le posizioni fisiche dei luoghi nel cyberspazio saranno sempre più difficili da localizzare. Un vasto “labirinto di stanze e corridoi” potrebbe essere stanziato fisicamente in Malesia, mentre un “Casinò online” mantenuto tramite metodi crittografici (remailer) dalla stanza da letto di qualcuno in Provo, Utah.

* La discussione riguardo le “regole di accesso” diventa quindi insensata, tranne nel caso in cui dei governi riescano a irrompere nel network e nei sistemi privati con metodologie più avanzate di quelle in discussione.

Questa è la “critto-anarchia” di cui parlo dal 1988. Il cyberspazio sarà più rivoluzionario di qualsiasi cosa mai vista finora. Con “sole” circa 10^70 particelle in tutto l’universo, c’è ampiamente più “spazio” (spazio degli indirizzi, spazio delle chiavi, ecc.) in un numero relativamente piccolo di cifre. Il cyberspazio è spazio matematico, e la sua vastità è davvero illimitata.

E quindi migreremo i nostri scambi, il nostro intrattenimento e le nostre vite nel cyberspazio molto più velocemente che nell’orbita bassa terrestre e oltre. Infatti io penso di essere già a metà strada. In un paio di anni, con una connettività allo stato d’arte, vaste scelte di network da poter utilizzare, remailer sicuri e strumenti simili per poter anonimizzare le mie transazioni, ne sarò così assorbito che non ci sarà via d’uscita.

Per ora può bastare. Penso che abbia senso prendere una visione leggermente più ampia degli inevitabili trend, per vedere in che direzione stiamo procedendo, per vedere quali problemi necessitano di più lavoro.

Spero che alcuni di voi siano d'accordo con me.

--Tim May