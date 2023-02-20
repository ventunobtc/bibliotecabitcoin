---
title: "P2P Filename Integrity"
description: "Nick Szabo - 2005"
date: 2022-10-11T19:50:58+02:00
draft: false
weight: 520
images: []
categories: []
contributors: ["cyphersats", "brandosari"]
---

[Originale](https://web.archive.org/web/20050328092206/http://szabo.best.vwh.net:80/nameintegrity.html) - 2005
 
Propongo una directory sicura e completamente decentralizzata per le reti p2p. Tale directory migliorerà l'integrità dei filename e fornirà vantaggi in termini di reputazione per chi crea e carica i file, risolvendo i problemi di [pollution e poisoning](https://web.archive.org/web/20050514194302/http://p2pecon.berkeley.edu/pub/CWC-EC05.pdf) nelle reti di condivisione p2p. La proposta è una variante dei titoli di proprietà sicuri.
 
La directory si basa su sistemi di quorum bizantini, o simili, e sulle firme digitali per identificare 
gli uploader originali ed i nominativi ("proprietari”) originali dei file tramite tuple (nome del file, hash del file, pseudonimo del proprietario, logo, catena di firme digitali, consenso). I proprietari rivendicano inoltre gli pseudonimi e i loghi tramite le tuple (logo, catena di firma digitale) e (pseudonimo, catena di firma digitale). La directory replica queste tuple in modo da risolvere il problema dei generali bizantini. Chiunque voglia caricare dei file originali può ottenere una coppia di chiavi pubbliche/private dal software p2p. L’uploader successivamente crea un nuovo pseudonimo e logo rivendicandone la proprietà, firmandoli, e li aggiunge al loro database. Le chiavi pubbliche sono il perfetto identificatore di una data entità; tutto il resto viene rivendicato come “proprietà” tramite le chiavi pubbliche.
 
I proprietari degli pseudonimi che caricano un nuovo file (cioè un file che non è un duplicato bit-per-bit di un file già rivendicato) possono allo stesso tempo dargli un nome e rivendicare il corrispettivo hash, usando la tupla descritta precedentemente, diventando di conseguenza il proprietario di quel file. (Non esiste alcuna proprietà legale, ma è una metafora che rende l’idea. I "diritti di proprietà" sono garantiti dalla risoluzione del problema dei generali bizantini e dalla firma digitale).
 
Uno pseudonimo e un'icona rappresentano un'entità attendibile (cioè un'entità la cui reputazione per la denominazione dei file è nota o al software di filtraggio o all'utente finale). La reputazione che deriva dal possedere un file va a vantaggio del proprietario e anche degli utenti, man mano che si aumenta la qualità della denominazione.
 
Di conseguenza, le persone in genere non vorranno trasferire i loro pseudonimi alle chiavi di altre persone. Tuttavia, a causa della vita limitata delle coppie di chiavi, vogliamo che sia possibile trasferire i diritti da una chiave all'altra, come in altri tipi di sistemi di proprietà sicuri.
 
Si noti che questa directory opera in parallelo con la componente di propagazione dei file del sistema p2p. In alcuni casi può accadere che venga propagato prima il file e in altri il nome, in ogni caso il file non è utilizzabile finché non saranno propagati entrambi. La tollerabilità del ritardo delle informazioni nella directory (oltre a quella del file) dipende dai valori che gli utenti e chi carica il file assegnano al tempo di propagazione, all'integrità del filename e alla reputazione del proprietario.
 
Oltre ai proprietari, il campo "consenso" può anche essere utilizzato da terze parti che vogliono garantire la correttezza di un nome in riferimento all'hash del file.
 
Gli incentivi che ne derivano, validi per falsificatori del filename, uploader, etc. sono molto interessanti e vengono lasciati come esercizio al lettore, in aggiunta ai “sistemi di reputazione” per chi desidera un sistema di filtraggio automatico. 

