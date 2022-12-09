# Come contribuire

Si può contribuire nei seguenti modi:
- Entrare nel gruppo Telegram di [ventunoBTC](https://t.me/ventunobtc) e condividere il testo tradotto
- Aprire una `issue` per avvisarci di un possibile testo da tradurre
- Creare direttamettamente una `pull request`

In questa guida vedremo gli ultimi due casi, in particolare come aggiungere un menù, una sezione o solo un testo tradotto.

## Creare una issue

È sufficiente seguire le istrizioni che si trovano seguendo questo [link](https://ventuno.space/listing-requirements).

## Creare una pull request

Da terminale installa le dipendenze e avvia il server:

```bash
# install dependencies
npm install
```
```bash
# start developement server
npm run start
```

Per una spiegazione dettagliata su come funziona, consulta la documentazione di [Nuxt.js](https://nuxtjs.org/)

### Aggiungere una traduzione

Il primo passo è identificare il menù e la sezione in cui si vuole pubblicare la propria traduzione. In seguito, utilizzeremo come esempio la traduzione della prima email di Satoshi.

La prima email di Satoshi (il file sarà nominato `email.md`) dovrà essere pubblicata nel menù `Satoshi` e nella sezione `Cryptograpy Mailing List`:

```bash
npm run create satoshi/cryptography-mailing-list/email.md
```

L'ultimo passo consiste nell'inserire il testo, scritto in `Markdown`, dopo i seguenti metadati:

```markdown
title: "..."
date: "..."
draft: "true"
```

### Creare un menù o una sezione

Come si sarà già intuito, i menù e le sezioni corrispondono alle directory in cui i file delle traduzioni vengono inseriti. Però, quando si aggiungono le directory, bisogna creare anche il file `_index.md` per ogni menù e sezione.

Prendendo l'esempio precedente e ipotizzando che il menù `Satoshi` e la sezione `Cryptograpy Mailing List` non siano stati creati:

#### 1. Crea il menù

```bash
npm run create satoshi/_index.md
```

#### 2. Crea la sezione

```bash
npm run create satoshi/cryptography-mailing-list/_index.md
```