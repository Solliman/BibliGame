# Cronologia delle Modifiche - BibliGame

Questo documento tiene traccia della memoria storica di tutte le modifiche apportate al progetto BibliGame, a partire dall'interfaccia web iniziale fino alla completa integrazione mobile nativa.

---

## 📌 Indice dei Rilasci
- [Versione 1.0.0 (Avvio)](#versione-100-avvio)
- [Aggiornamento Immersivo V1 (Audio & Profilo)](#aggiornamento-immersivo-v1-audio--profilo)
- [Aggiornamento Immersivo V2 (Icone & Shuffling)](#aggiornamento-immersivo-v2-icone--shuffling)
- [Aggiornamento Immersivo V3 (Correzioni Spaziatura & progressioni)](#aggiornamento-immersivo-v3-correzioni-spaziatura--progressioni)
- [Aggiornamento Immersivo V4 (Correzioni Finali UX & Localizzazione)](#aggiornamento-immersivo-v4-correzioni-finali-ux--localizzazione)
- [Aggiornamento Immersivo V5 (Splash Screen & Benvenuto)](#aggiornamento-immersivo-v5-splash-screen--benvenuto)

---

## Versione 1.0.0 (Avvio)
* **Struttura Core**: Creazione del gioco testuale basato su tutti i 66 libri della Bibbia (Canone Protestante).
* **Interfaccia Web**: Menu di selezione del libro, selezione dei capitoli e griglia di navigazione.
* **Integrazione IA**: Supporto alle API Groq (`llama-3.3-70b-versatile`) e Gemini (`gemini-2.5-flash`) per generare scenari testuali e bivi di scelta (Teologici vs Umani).
* **Meccanica a Tempo**: Inserimento del countdown a 30 secondi per effettuare la scelta del bivio d'azione.

---

## Aggiornamento Immersivo V1 (Audio & Profilo)
* **Audio Synth**: Creazione di effetti sonori polifonici sintetizzati in tempo reale tramite Web Audio API (suono all'inizio delle scelte, suono per scelta canonical/human).
* **Particelle Grafiche**: Generazione di emoji fluttuanti coordinate al tocco dell'utente (`✨`, `🕊️`, `📖` per scelte teologiche; `👣`, `🕯️`, `🌱` per scelte umane).
* **Profilo Giocatore**: Inserimento della prima schermata di profilazione caratteriale al completamento di un libro per definire lo stile di risposta del giocatore.
* **Android Shell**: Configurazione iniziale del progetto Android nativo con WebView a schermo intero in Jetpack Compose.
* **Branding**: Generazione tramite intelligenza artificiale del logo premium `logo.jpg` e configurazione iniziale delle icone app.

---

## Aggiornamento Immersivo V2 (Icone & Shuffling)
* **Ritaglio Icona Android**: Rimozione dei margini bianchi in eccesso del logo (`logo.jpg`) tramite `sips` per massimizzare la visibilità della corona dorata e dei raggi solari.
* **Icone Adattive**: Ricreazione dei file XML adattivi (`ic_launcher.xml` e `ic_launcher_round.xml`) con sfondo bianco solido. Ora l'icona sul launcher del telefono è perfettamente circolare e solare.
* **Mescolamento delle Risposte (Shuffling)**: Modificata la logica di visualizzazione dei bivi in gioco. Ora le risposte non presentano più la scelta teologica in prima posizione fissa, ma vengono mescolate casualmente ad ogni caricamento, spingendo il giocatore a leggere le opzioni.
* **Musica Dinamica**: Inserite 4 diverse progressioni armoniche (Do maggiore, La minore, Sol maggiore, Re maggiore) che si alternano automaticamente ogni 5 minuti in sottofondo per evitare la fatica acustica.
* **Bypass Chiave API**: Integrazione protetta e cifrata (tramite inversione Base64 anti-bot) della chiave API Groq all'interno dell'app. Al primo avvio l'app salta la schermata chiave per andare direttamente al menù dei libri.

---

## Aggiornamento Immersivo V3 (Correzioni Spaziatura & progressioni)
* **Gestione della Safe Area**: Modificato il file nativo `MainScreen.kt` per eliminare i margini bianchi e far sì che il gioco vada a schermo intero nativo (Edge-to-Edge). Aggiunto `viewport-fit=cover` in HTML e regolate le altezze CSS per evitare la sovrapposizione dell'intestazione con l'orologio della barra di stato del telefono.
* **Sblocco Sequenziale dei Capitoli**: Introdotto l'obbligo di affrontare la storia nell'ordine corretto. I capitoli successivi a quello corrente sono bloccati e contrassegnati dall'icona a lucchetto (**🔒**). Ciascun capitolo si sblocca solo al completamento del precedente.
* **Gestione del Background (Lifecycle Observer)**: Risolto il problema della musica che continuava a suonare quando si usciva dal gioco. Implementati i controlli `onPause()` e `onResume()` della WebView agganciati al ciclo di vita dell'activity Android.

---

## Aggiornamento Immersivo V4 (Correzioni Finali UX & Localizzazione)
* **Spostamento del Timer**: Spostata la barra del countdown da 30s dalla testata per posizionarla direttamente sopra la domanda e le risposte. Ora compare solo dopo aver premuto l'Aura dorata di lettura.
* **Auto-Scroll sulle Risposte**: All'attivazione delle risposte, la schermata scorre automaticamente verso il basso (smooth scroll) per posizionare le opzioni al centro della visuale sui display più compatti.
* **Profilo Biblico Unitario**: Sostituita la dicitura del Profilo Unitario in *"Il Tuo Profilo del Cammino Biblico"*. Rimossi i vecchi titoli generici per inserire profili d'anima specifici (*Fede e Intelletto*, *Equilibrio e Sapienza*, *Azione e Compassione*), con testi descrittivi dinamici che si arricchiscono in base al numero di libri biblici completati.
* **Aggiornamento di Stato della Home**: Aggiunto il rinfresco automatico della Home tramite `renderHome()` alla chiusura del libro, in modo che la scheda del Profilo Biblico compaia all'istante senza dover forzare la chiusura dell'app.
* **Ripristino Stabilità Asset Locali**: Configurato il caricamento primario locale all'interno della WebView nativa dell'APK per evitare problemi di 404 e chiavi API scoperti sui server remoti non ancora configurati.

---

## Aggiornamento Immersivo V5 (Splash Screen & Benvenuto)
* **Schermata Splash (Intro)**: Schermata iniziale di 5 secondi con il logo di BibliGame centrato ed un cerchio dorato sfumato ("sfumatura alle spalle"). Pulsante "Salta intro" per bypassare rapidamente la schermata.
* **Messaggio di Benvenuto in Home**: Aggiunto un testo esplicativo accogliente all'apertura del gioco per i nuovi utenti che spiega come giocare, come funziona la profilazione finale ed il profilo globale in Home.
* **Pulsante di Chiusura Permanente**: La card di benvenuto presenta un pulsante di chiusura (x) per rimuoverla in modo permanente (memorizzando la scelta in `localStorage`).
