# REPORT-1-Web-Mobile-Banking-Security-Assessment-01-2026
RAPPORTO TECNICO DI SICUREZZA
Tipo: Web & Mobile Application Assessment
Approccio: Attacker Mindset (Offensive Thinking)
Livello di Rischio: Critico

INTRODUZIONE
L’analisi è stata condotta simulando il comportamento reale di un attaccante esterno.
L’obiettivo non era verificare la conformità teorica, ma individuare punti di ingresso
realisticamente sfruttabili partendo da privilegi minimi.

METODOLOGIA
L’approccio seguito è stato progressivo:
- Osservazione del flusso di autenticazione
- Analisi delle API esposte
- Manipolazione dei parametri lato client
- Test dei controlli logici lato server

VULNERABILITÀ IDENTIFICATE

1) IDOR (Insecure Direct Object Reference)
La logica di autorizzazione non verificava la reale proprietà della risorsa richiesta.
Un attaccante, modificando manualmente gli identificatori, poteva accedere a dati
finanziari di terze parti senza elevare privilegi.

2) Bypass della Verifica OTP
La validazione del secondo fattore risultava parzialmente gestita lato client.
Manipolando la risposta HTTP, l’accesso veniva concesso senza completare il flusso 2FA.

3) Information Disclosure tramite API
Le risposte JSON contenevano informazioni interne non necessarie (IP, struttura DB),
utili a facilitare fasi successive di attacco mirato.

IMPATTO
- Compromissione completa della riservatezza dei dati
- Possibile frode finanziaria
- Escalation verso attacchi interni più avanzati

CONCLUSIONI
Il sistema risulta vulnerabile ad attacchi condotti da un attore con competenze medie.
Le vulnerabilità individuate sono sfruttabili senza exploit complessi, basandosi
principalmente su logica applicativa difettosa.
