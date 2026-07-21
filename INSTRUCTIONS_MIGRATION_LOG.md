# 📜 Linee Guida per AI: Tracciamento, Backup e Nuova Struttura (Bibbia Game)

Questo file contiene le regole fondamentali di gestione del progetto **Bibbia Game** per garantire la continuità dello sviluppo con qualsiasi assistente IA (Gemini, Claude, ecc.) anche in caso di perdita o cancellazione della cronologia chat.

---

## 1. 📂 Spostamento e Nuova Mappa del Progetto
Questo progetto farà parte di una riorganizzazione generale del Desktop e del NAS sotto la cartella madre **`Solli Works`**.
*   **Nuovo Percorso Locale:** `/Users/sollimac/Desktop/Solli Works/08 - Bibbia Game/`
*   **Nuovo Percorso di Backup sul NAS:** `/Volumes/docker/Solomon_works/Solli Works/08 - Bibbia Game/`

---

## 2. 📝 Regola Mandatoria di Tracciamento Giornaliero (Daily Journal)
Per evitare la perdita di informazioni tra diverse sessioni di chat, l'AI è tenuta a seguire questo flusso:

*   **🌅 Inizio Giornata (o inizio nuova Chat):** L'AI deve leggere questo file, il file di memoria locale del progetto (`bg_mAImory.md` o simile) e l'ultimo log di tracciamento per allinearsi istantaneamente sullo stato del lavoro.
*   **🌌 Fine Giornata / Chiusura Sessione:** 
    *   **Trigger dell'utente:** Quando l'utente scrive frasi come `"chiudo"`, `"chiudo per oggi"`, `"per oggi chiudo così"`, o `"sospendo"`.
    *   **Azione dell'AI:** L'AI capisce che la sessione è conclusa. Prima di terminare il turno, deve **creare o aggiornare il file `daily_log.md`** (o la sezione Walkthrough) contenente:
        *   Le modifiche apportate ai file (con percorsi assoluti).
        *   Eventuali bug aperti o problemi riscontrati.
        *   La roadmap chiara con i passi successivi per riprendere il lavoro in seguito.
        *   Salvare un backup della chat corrente in locale.

---

## 💾 3. Gestione della Memoria (mAImory Locale)
Per non inquinare la memoria centrale del brand musicale di Solli Solomon (che risiede sotto `06 - mAImory`):
*   Tutti i dettagli tecnici, le regole di gioco, le grafiche e le note di programmazione di **Bibbia Game** devono essere salvati all'interno di questa cartella in un file dedicato (es. `bibbia_game_memory.md`).
*   Le conversazioni importanti di questa chat verranno archiviate in locale per backup in `workflow/chat_log.md` all'interno di questa stessa cartella di progetto.
