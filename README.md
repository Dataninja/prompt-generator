# Prompt Generator

Strumento didattico in quattro passaggi per aiutare chi insegna a scrivere un prompt completo per un chatbot: ruolo, compito, obiettivo, limiti. Il prompt si compone mentre si scrive e si copia con un clic.

Fa parte dei materiali di **Open the Box**, il progetto di alfabetizzazione mediatica di [Dataninja](https://www.dataninja.it), ed è pensato per i corsi di AI literacy rivolti al personale docente.

## Come funziona

Quattro schede, una per variabile:

| Passo | Variabile | Che cosa chiede |
|---|---|---|
| 1 | Ruolo | chi scrive, che materia insegna, che classe ha davanti |
| 2 | Compito | i passaggi da eseguire, nell'ordine |
| 3 | Obiettivo | il fine ultimo del lavoro |
| 4 | Limiti | lunghezza, formato, registro, cosa non fare |

Il riquadro a destra mostra il prompt che si sta componendo, segnala le variabili ancora vuote e, quando sono tutte compilate, apre una checklist di verifica del risultato. Il testo scritto resta salvato nel browser (`localStorage`) e si ritrova alla riapertura della pagina; il pulsante **Ricomincia** lo cancella.

Nulla viene inviato a un server: non ci sono chiamate di rete, analytics o cookie. L'unica risorsa esterna è il font Work Sans da Google Fonts, con ricaduta su Helvetica o Arial se non è raggiungibile.

## Uso

Basta aprire `prompt-generator.html` in un browser. Non serve un server, non serve installare nulla.

Per pubblicarlo online con GitHub Pages: caricare il file nel repository, poi *Settings → Pages* e scegliere il branch come sorgente. Se lo si rinomina `index.html` la pagina risponde direttamente all'indirizzo del repository.

## Struttura

Un solo file. Icone e loghi sono incorporati come data URI in base64, quindi non ci sono cartelle di immagini né percorsi relativi da mantenere.

```
prompt-generator.html    tutto: markup, CSS, JavaScript, immagini
README.md
```

## Personalizzazione

- **Testi dei passaggi**: array `DATI` nello script, verso la fine del file. Ogni oggetto ha `breve` (etichetta della scheda), `nome` (titolo), `etichetta` (prefisso nel prompt finale), `hint` (la riga di spiegazione) e `ph` (l'esempio nel campo di testo).
- **Regole fisse**: blocco `f.innerHTML` nella funzione `render()`, mostrato solo sull'ultimo passaggio.
- **Checklist di verifica**: fondo della funzione `aggiornaOut()`.
- **Colori**: variabili CSS in `:root`, con i corrispettivi per il tema scuro subito sotto.
- **Icone e loghi**: array `ICONE` e i due `<img>` dentro `.loghi`. Per sostituirli serve rigenerare la stringa base64, per esempio con `base64 -w0 nuova-icona.png`, e incollarla dopo `data:image/png;base64,`.

La chiave di salvataggio locale è `otb-prompt-generator-v1`: cambiandola si azzerano le bozze salvate da chi ha già usato la pagina.

## Accessibilità e compatibilità

Contrasti conformi ad AA, navigazione da tastiera, tema chiaro e scuro automatici in base alle impostazioni di sistema, layout responsive a colonna singola sotto i 900 px. Funziona su qualsiasi browser aggiornato; `color-mix()` richiede versioni recenti di Chrome, Safari o Firefox, e dove non è supportato l'effetto è solo una sfumatura di sfondo in meno.

## Crediti

Open the Box è un progetto di Dataninja. Maggiori informazioni su [openthebox.io](https://openthebox.io/).
