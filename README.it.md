# Aurora Glass v3 — dashboard animata per Home Assistant

🇬🇧 [Read in English](README.md)

> **Novità: [Aurora Glass con procedura guidata](https://github.com/lucalux00/aurora-glass)** — si installa da HACS come integrazione: trova le tue stanze, ti fa scegliere i nomi e aggiunge la plancia alla barra laterale, in italiano o in inglese. Questo repository resta per l'installazione a mano con YAML.

![Aurora Glass v3](docs/dashboard-casa-notte-intera.webp)

Una sola scheda personalizzata che trasforma la plancia di Home Assistant in una scena viva: cielo, sole, luna e finestre della casetta seguono l'ora reale. Dieci mondi animati, undici effetti meteo, pulsanti fatti di immagini e GIF, allarme, clima, telecamere ed energia con i costi in euro calcolati sulla tua tariffa.

- **Demo dal vivo (senza installare nulla):** https://domotikpro.it/aurora-glass-v3-demo/index.html
- **Guida completa con schermate:** https://domotikpro.it/progetti/aurora-glass-v3
- **Video passo passo:** https://www.youtube.com/@domotikproit

| Tablet | Energia | Telefono |
|---|---|---|
| ![Tablet](docs/tablet-casa-tramonto.webp) | ![Energia](docs/energia-vista.webp) | ![Telefono](docs/mobile-casa-notte-sm.webp) |

## Cosa include
- 10 mondi animati e 11 effetti meteo (pioggia, neve, temporale, lucciole, petali, fuochi…)
- Cielo che segue l'ora reale
- 50 immagini e GIF già pronte per i pulsanti (luci, scene, sensori, allarme, clima)
- Pannello allarme, controllo clima, telecamere
- Vista Energia: potenza, kWh di oggi/ieri/mese/anno e costo = kWh × la tua tariffa
- Un solo file JavaScript, nessuna compilazione, nessun cloud
- **Privacy:** funziona tutto in locale. L'unica richiesta esterna sono i font Google (Manrope, Sora). Nessun dato viene raccolto o inviato.

## Installazione (circa 10 minuti)
La versione commentata è in [`aurora-glass-v3/LEGGIMI.txt`](aurora-glass-v3/LEGGIMI.txt). In breve:

**Con HACS (copia la scheda e le immagini e aggiunge la risorsa da solo):** HACS → ⋮ → *Repository personalizzati* → aggiungi `https://github.com/lucalux00/aurora-glass-v3`, tipo *Dashboard* → cerca **Aurora Glass v3** → *Scarica* → ricarica il browser, poi passa al punto 3. Senza HACS segui i punti 1–2.

1. **Copia i file.** Metti la cartella `aurora-glass-v3/www/aurora-v3` dentro la cartella `www` di Home Assistant (File editor, Samba o Studio Code Server). Risultato: `www/aurora-v3/aurora-v3.js` e `www/aurora-v3/btn/…`. Nel componente File editor la cartella di configurazione si chiama `/homeassistant`: è la stessa. Se `www` è nuova, riavvia Home Assistant una volta. Prova: apri `<indirizzo di Home Assistant>/local/aurora-v3/aurora-v3.js` nel browser: se vedi del testo è tutto a posto.
2. **Aggiungi la risorsa.** Profilo → attiva *Modalità avanzata*. Impostazioni → Plance → ⋮ → Risorse → Aggiungi risorsa: URL `/local/aurora-v3/aurora-v3.js?v=1`, tipo *Modulo JavaScript*. Quando aggiorni la scheda, alza il numero dopo `?v=`.
3. **Crea la plancia.** Impostazioni → Plance → Aggiungi plancia → Nuova plancia da zero.
4. **Incolla la scheda.** Apri la plancia → matita → ⋮ → *Editor di configurazione testuale*, cancella tutto e incolla [`dashboard-esempio.yaml`](aurora-glass-v3/dashboard-esempio.yaml), poi salva. Le luci saranno grigie finché non indichi le tue entità.
5. **Collega le tue entità.** Strumenti per sviluppatori → Stati: cerca i nomi (`light.`, `binary_sensor.`…) e aggiungili sotto `entities:` come in [`scheda-esempio.yaml`](aurora-glass-v3/scheda-esempio.yaml) (tutte le opzioni, commentate).
6. **Energia e tariffa (facoltativo).** Indica il tuo sensore di potenza (W) in `energy.power`. Per i kWh di oggi/mese/anno usa [`aurora-energia.yaml`](aurora-glass-v3/aurora-energia.yaml). Nella vista Energia tocca la barra *Tariffa* e scrivi quanto paghi un kWh (o calcolalo dalla bolletta: totale da pagare ÷ kWh).

La scheda si chiama `custom:aurora-v3-card`.

## Se qualcosa non va
- *Scheda rossa "Custom element doesn't exist"* — controlla la risorsa e ricarica con Ctrl+F5.
- *Immagini vuote* — `assets` deve essere `/local/aurora-v3/btn/` (con la barra finale).
- *Luci grigie* — il nome dell'entità non esiste o il dispositivo è offline.
- *Costi a zero* — tocca la barra *Tariffa* e imposta il prezzo per kWh.

## Rimuovere
Elimina la plancia, la risorsa e la cartella `www/aurora-v3`. Nient'altro viene toccato.

## Stato
Versione 3, provata dall'autore su Home Assistant 2026.9. Segnalazioni e suggerimenti sono benvenuti: apri una issue.

## Licenza
[GPL-3.0](LICENSE). Puoi usare, studiare, modificare e condividere la scheda, anche a scopo commerciale, purché ogni versione modificata che distribuisci resti GPL-3.0, sia accompagnata dal codice sorgente e mantenga la nota originale: © 2026 DomotikPro.it (Luca Pinelli).

Il nome "Aurora Glass" e il marchio DomotikPro.it non rientrano nella licenza: una versione modificata deve usare un nome diverso.

---
Realizzato da [DomotikPro.it](https://domotikpro.it) — guide pratiche per una casa smart affidabile.
