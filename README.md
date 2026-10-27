# customterm-releases

Canale di distribuzione e auto-update di **customTerm** (solo binari, nessun sorgente).

customTerm è un host di terminale per Windows e Linux che fa girare **Claude Code** in sessioni
parallele: un albero di progetti nella barra laterale, una scheda per sessione, e ogni
sessione è un processo Claude vero dentro un PTY.

## Download

| Sistema | Download diretto (ultima versione) |
| --- | --- |
| **Windows** | **[customTerm-Setup.exe](https://github.com/LupusInTabula/customterm-releases/releases/latest/download/customTerm-Setup.exe)** |
| **Linux** (x64) | **[customTerm.AppImage](https://github.com/LupusInTabula/customterm-releases/releases/latest/download/customTerm.AppImage)** |

Le versioni precedenti stanno nella pagina delle **[release](https://github.com/LupusInTabula/customterm-releases/releases)**.

## Installazione su Windows

1. Scarica **[customTerm-Setup.exe](https://github.com/LupusInTabula/customterm-releases/releases/latest/download/customTerm-Setup.exe)**.
2. Eseguilo.

⚠️ **Windows mostrerà un avviso di SmartScreen** ("Windows ha protetto il PC"): la build non è
firmata con un certificato commerciale. Clicca **Ulteriori informazioni → Esegui comunque**.

L'installazione non fa domande: è per utente, finisce in
`%LOCALAPPDATA%\Programs\customTerm`, crea la scorciatoia sul desktop e avvia l'app da sola.
Non servono permessi di amministratore.

## Installazione su Linux

1. Scarica **[customTerm.AppImage](https://github.com/LupusInTabula/customterm-releases/releases/latest/download/customTerm.AppImage)**.
2. Rendilo eseguibile e avvialo:

   ```bash
   chmod +x customTerm.AppImage
   ./customTerm.AppImage
   ```

Un AppImage non si installa: è un file solo, lo tieni dove vuoi (per esempio `~/Applications`).
Su Ubuntu 22.04 e successive serve `libfuse2` (`sudo apt install libfuse2`, su 24.04
`libfuse2t64`), altrimenti l'AppImage non parte.

Su Linux non ci sono le cartelle condivise di Windows né la regola del firewall: tutto il resto
è uguale.

### Cosa deve esserci già sulla macchina

| Serve | Perché | Se manca |
| --- | --- | --- |
| **Claude Code** (`claude` nel PATH) | l'app lancia `claude` per ogni sessione Claude | le sessioni Claude non partono, quelle terminale sì |
| **Node.js** (`node` nel PATH) | alimenta la barra di stato (modello, contesto, limiti) | l'app funziona, ma la barra di stato resta vuota |

## Aggiornamenti

**Si aggiorna da solo**, su Windows e su Linux. L'app controlla questa pagina all'avvio e poi
ogni 6 ore, scarica in background e installa alla chiusura.

Quindi per prendere una versione nuova basta **chiudere e riaprire l'app**. Non serve
disinstallare niente, e le conversazioni non si perdono: vivono nei transcript di Claude Code,
non dentro l'app.

Se vuoi forzare la mano, scarica di nuovo il file dal link qui sopra: su Windows eseguilo sopra
l'installazione esistente, su Linux sostituisci il vecchio AppImage.

## Sorgente

Il codice sta in un repository privato. Qui ci sono solo gli installer e i `latest.yml` /
`latest-linux.yml` che l'updater legge, esattamente come per
[rigvitals-releases](https://github.com/LupusInTabula/rigvitals-releases).
