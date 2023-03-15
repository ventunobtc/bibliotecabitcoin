---
title: "RPOW - Reusable Proofs of Work"
description: "Prototipo di contante digitale inventato da Hal Finney e precursore di Bitcoin - 15 Agosto, 2004"
date: 2023-01-29T15:28:52+01:00
draft: false
weight: 385
images: []
categories: []
contributors: ["cyphersats"]
---

[Originale](https://cryptome.org/rpow.htm) - 15 Agosto, 2004

To: cypherpunks@al-qaeda.net
Subject: RPOW - Reusable Proofs of Work
Date: Sun, 15 Aug 2004 10:43:09 -0700 (PDT)
From: hal at finney dot org ("Hal Finney")

Vorrei invitare i membri di questa lista a provare il mio nuovo server basato su hashcash, [rpow.net](https://nakamotoinstitute.org/finney/rpow/index.html).

Questo sistema riceve hashcash come token Proof of Work (POW) e in cambio crea token firmati RSA che chiamo Reusable Proof of Work (RPOW). &nbsp;I RPOW possono essere successivamente trasferiti da persona a persona e scambiati con nuovi RPOW a ogni passaggio. &nbsp;Ogni token RPOW o POW può essere utilizzato una sola volta ma, siccome ognuno dà vita a uno nuovo, è come se lo stesso token potesse essere passato da persona a persona.

Poiché gli RPOW sono creati solo da POW o RPOW di pari valore, sono rari e "preziosi" quanto l'hashcash che è stato utilizzato per crearli e sono riutilizzabili, a differenza di quest’ultimo.

Il concetto innovativo è il modello di sicurezza. &nbsp;Il server RPOW gira su una scheda processore ad alta sicurezza, l'IBM 4758 Secure Cryptographic Coprocessor, validato al livello 4 di FIPS-140. &nbsp;Questa scheda è in grado di fornire un'attestazione firmata della configurazione software installata, che qualsiasi utente (sufficientemente motivato) può verificare rispetto al codice sorgente pubblico del sistema. &nbsp;In questo modo tutti possono verificare che essa non abbia backdoor e che creerà token RPOW solo quando gli verranno forniti token POW/RPOW di pari valore.

Questo è ciò che crea fiducia nei RPOW in quanto oggetti che incarnano effettivamente i valori dichiarati, la consapevolezza che sono stati realmente creati sulla base di un token POW (hashcash) di pari valore.

Ho molte altre informazioni sul sistema, disponibili insieme al codice sorgente, su [rpow.net](https://nakamotoinstitute.org/finney/rpow/index.html). &nbsp;Esiste anche una grezza interfaccia web che consente di scambiare POW con RPOW senza necessità di scaricare il client.

Questo sistema è in fase di beta iniziale, apprezzo quindi qualsiasi feedback se qualcuno avesse la possibilità di testarlo. &nbsp;Tenete presente che in caso di problemi potrei dover ricaricare il codice del server, il che invaliderebbe i gettoni RPOW creati in precedenza. Quindi non impazzite ad accaparrare RPOW per il momento.

Grazie mille.

Hal Finney

