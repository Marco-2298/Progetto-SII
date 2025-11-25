📌 Origine del dataset

Il dataset "NBA_Draft_ve" utilizzato in questo progetto è stato scaricato da una piattaforma di dataset pubblici,  Kaggle.

📌 Come viene utilizzato nel progetto

Questo dataset verrà impiegato per:

creare un modello di analisi e previsione delle performance dei giocatori scelti al Draft;

analizzare la correlazione tra college, scelta al draft e prestazioni NBA;

addestrare algoritmi di recommender system / predictive modeling;

effettuare un confronto storico tra draft class diverse;

costruire nuove feature (es. efficienza, valore carriera, sviluppo futuro).

Il dataset permette quindi una prima analisi completa, su tutti i giocatori draftati dal 1947 ad oggi, utile sia per modellazione statistica che per machine learning.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📊 Spiegazione delle colonne

🏀 Colonne anagrafiche

Year: 
L’anno in cui si è svolto il Draft NBA.

Rk:
La posizione assoluta nel draft.

Tm:
La franchigia NBA che ha selezionato il giocatore.

Player:
Nome e cognome del giocatore.

College:
Università o programma da cui proviene il giocatore.
Può essere NaN per giocatori internazionali o epoche storiche meno documentate.

📈 Colonne di carriera (Totali / Stagioni / Partite)

Yrs:
Numero di anni giocati in NBA.
NaN indica giocatori che non hanno mai disputato partite NBA.

G:
Partite totali giocate in carriera.

MP:
Minuti totali giocati in carriera.

🏀 Statistiche totali di carriera

PTS:
Punti totali segnati.

TRB:
Rimbalzi totali (Total Rebounds).

🧮 Statistiche avanzate / percentuali

3P%:
Percentuale nel tiro da 3 punti.

FT%:
Percentuale ai tiri liberi.

🔁 Statistiche medie per partita

MP:
Minuti medi per partita.

PTS:
Punti medi per partita.

TRB:
Rimbalzi medi per partita.

AST:
Assist medi per partita.

🧠 Metriche avanzate di impatto (Analytics)
WS – Win Shares:
Stima del "numero di vittorie" prodotte da un giocatore.
Misura quanto un giocatore contribuisce realmente alle vittorie della squadra.

WS/48:
Win Shares per 48 minuti.
Usato per confrontare giocatori con minutaggi molto diversi.

BPM – Box Plus/Minus:
Valuta l’impatto del giocatore (offensivo + difensivo) per 100 possessi, basato sulle statistiche da boxscore.

VORP – Value Over Replacement Player:
Misura quanto un giocatore vale più di un ipotetico "giocatore sostituto".
È una delle metriche più usate per analisi avanzate.

✅ Note sul dataset

Molti valori NaN sono normali per giocatori degli anni ‘40–60, o per chi non ha mai debuttato in NBA.

Le statistiche avanzate (WS, BPM, VORP) sono disponibili solo per epoche recenti.

È un dataset adatto a:

clustering (per simili giocatori)

regressione (per predire il successo NBA)

ranking models

recommender systems