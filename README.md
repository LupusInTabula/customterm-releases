# customterm-releases

Canale di distribuzione e auto-update di **customTerm** (solo binari, nessun sorgente).

customTerm è un host di terminale per Windows che fa girare **Claude Code** in sessioni
parallele: un albero di progetti nella barra laterale, una scheda per sessione, e ogni
sessione è un processo Claude vero dentro un PTY.

## Installazione

1. Apri la **[release più recente](https://github.com/LupusInTabula/customterm-releases/releases/latest)**.
2. Scarica `customTerm-Setup-<versione>.exe`.
3. Eseguilo.

⚠️ **Windows mostrerà un avviso di SmartScreen** ("Windows ha protetto il PC"): la build non è
firmata con un certificato commerciale. Clicca **Ulteriori informazioni → Esegui comunque**.

L'installazione non fa domande: è per utente, finisce in
`%LOCALAPPDATA%\Programs\customTerm`, crea la scorciatoia sul desktop e avvia l'app da sola.
Non servono permessi di amministratore.

### Cosa deve esserci già sulla macchina

| Serve | Perché | Se manca |
| --- | --- | --- |
| **Claude Code** (`claude` nel PATH) | l'app lancia `claude.exe` per ogni sessione Claude | le sessioni Claude non partono, quelle terminale sì |
| **Node.js** (`node` nel PATH) | alimenta la barra di stato (modello, contesto, limiti) | l'app funziona, ma la barra di stato resta vuota |

## Aggiornamenti

**Si aggiorna da solo.** L'app controlla questa pagina all'avvio e poi ogni 6 ore, scarica in
background e installa alla chiusura.

Quindi per prendere una versione nuova basta **chiudere e riaprire l'app**. Non serve
disinstallare niente, e le conversazioni non si perdono: vivono nei transcript di Claude Code,
non dentro l'app.

Se vuoi forzare la mano, scarica l'installer dalla release più recente ed eseguilo sopra
l'installazione esistente: si comporta come un aggiornamento.

## Sorgente

Il codice sta in un repository privato. Qui ci sono solo gli installer e il `latest.yml` che
l'updater legge, esattamente come per
[rigvitals-releases](https://github.com/LupusInTabula/rigvitals-releases).
