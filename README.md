# 🔵 PROGETTO

L’obiettivo del progetto è analizzare retrospettivamente i Draft NBA utilizzando un dataset storico contenente tutte le scelte dal 1947 al 2024, includendo statistiche di carriera aggiornate per ogni giocatore.

Il fine è studiare:

quali draft hanno generato il maggior valore complessivo,

quali college producono più talenti,

come classificare i giocatori in categorie qualitative,

la relazione tra posizione di scelta e longevità,

l’evoluzione delle prestazioni dei giocatori nei primi anni di carriera.

Successivamente, il lavoro sarà esteso con una seconda parte dedicata a un sistema intelligente basato sui concetti del corso, per assistere uno scout NBA nella ricerca del profilo ideale di giocatore tramite un motore di ricerca testuale e un recommender content-based.

## PARTE 1 — ANALISI STORICA DEI DRAFT NBA

### 📘 Notebook 1 — Data Exploration & Cleaning

Obiettivo: costruire un dataset coerente e utilizzabile per analisi e modelli.

Operazioni principali:

Esplorazione del dataset originale 1947–2024.

Gestione dei valori mancanti (college, pick forfeit, giocatori mai esorditi).

Normalizzazione delle statistiche:

3P% pre-1979 → -1

metriche avanzate mancanti → -100 + flag _available

debutto NBA → reset statistiche base.

Creazione colonne utili: PickBand, Status, ecc.
Output finale → drafted_cleaned.csv.

### 📘 Notebook 2 — Value Analysis (WS & VORP)

Obiettivo: analizzare il valore prodotto dalle Draft Class NBA.

Attività:

Aggregazione annuale di Win Shares e VORP.

Identificazione di best e worst draft class.

Grafici di andamento per WS e VORP nel tempo.

### 📘 Notebook 3 — College Analysis

Obiettivo: valutare la capacità dei college di produrre talento NBA.

Attività:

Somma delle WS per college.

Classifica dei Top 20 college.

Per i migliori 3 college → estrazione dei migliori 5 giocatori per WS.

### 📘 Notebook 4 — Player Quality & Career Analysis

Obiettivo: classificare i giocatori e studiare l’evoluzione della carriera.

Attività:

Creazione della colonna Tier:

Star / Starter / Role Player / Flop / N/A.

Distribuzione dei Tier globalmente e per decade.

Longevità media della carriera in funzione del pick.

Confronto tra gruppi: Top10, First Round, Second Round.

### 📘 Notebook 5 — Predictive Model (Expected WS)

Obiettivo: predire l’impatto di carriera al momento del Draft.

Modelli utilizzati:

Linear Regression (baseline su Pick + DraftYear).

Random Forest con One-Hot Encoding (modello avanzato).

Output del modello:

Expected WS → Win Shares attese.

Delta = WS_real – WS_expected → misura di over/underperformance.

Risultati finali:

Il modello individua correttamente steal storiche (Ginóbili, Marion, Divac…).

Identifica i principali bust (Anthony Bennett, LaRue Martin…).

Random Forest ottiene MAE ≈ 7 e RMSE ≈ 15, molto meglio del modello lineare.

## 🔶 PARTE 2 — SISTEMA INTELLIGENTE PER TALENT SCOUT NBA

(Questa è la parte in piena linea con Sistemi Intelligenti per Internet)

🎯 Obiettivo della Parte 2

Sviluppare un motore di ricerca + sistema di raccomandazione che assista un direttore sportivo o scout nel trovare il giocatore ideale in base a una descrizione testuale.

Esempio input:

"Cerco una guardia tiratrice con ottime percentuali da 3, buon FT%, forte rimbalzista offensivo."

Il sistema deve restituire un ranking dei giocatori più simili al profilo richiesto.

### 📌 Preparazione del corpus

Per consentire al motore di ricerca di lavorare su informazioni strutturate, ogni giocatore viene trasformato in un documento testuale che descrive le sue caratteristiche principali. Questa rappresentazione include ruolo, percentuali di tiro, efficienza ai liberi, capacità di creazione offensiva, rimbalzi, difesa, metriche avanzate e ulteriori annotazioni qualitative. Un documento può dunque assumere una forma come: “Guardia, 40% da tre, 88% ai liberi, 6 rimbalzi, buon difensore, ottima efficienza offensiva”. L’intero insieme dei giocatori costruisce il corpus testuale che sarà in seguito indicizzato.

### 📌 Step B Indicizzazione dei documenti

Una volta definito il corpus, esso viene sottoposto a un processo di indicizzazione basato sugli strumenti classici dell’Information Retrieval, come TF-IDF o BM25. La pipeline prevede la tokenizzazione del testo, la rimozione delle stopword, la normalizzazione linguistica, la creazione del vocabolario e infine la generazione delle matrici vettoriali che rappresentano ogni documento. L’indice risultante è persistente, efficiente e pronto per essere interrogato da qualsiasi query dello scout.

### 📌 Step C Comprensione della query naturale

Quando l’utente fornisce una descrizione del tipo “Mi serve un lungo forte a rimbalzo e stoppate”, il sistema analizza la frase per individuarne le parole chiave e interpretarli come concetti tecnici. I termini rilevanti vengono quindi mappati automaticamente sulle feature numeriche corrispondenti: ad esempio “tiratore da tre” è collegato alla statistica 3P%, “liberi” al FT%, “rimbalzista” ai rimbalzi offensivi e difensivi, “playmaker” agli assist, “difensore” alle metriche difensive come BLK, STL o Defensive WS. In questa fase vengono anche assegnati pesi ai vari concetti, così da modellare l’importanza relativa delle diverse caratteristiche.

### 📌 Step D — Ranking dei giocatori

Dopo aver interpretato la query e pesato le feature, il sistema confronta il profilo richiesto con tutti i giocatori presenti nell’indice. La similarità viene calcolata combinando sia il punteggio IR (come la coseno-similarità dei vettori TF-IDF o lo score BM25) sia l’allineamento numerico delle statistiche pesate. Il risultato è un ranking finale dei giocatori più compatibili con il profilo cercato. Oltre a presentare la lista ordinata, il sistema può anche generare una breve spiegazione che giustifica perché un determinato giocatore si trova in cima alla classifica, evidenziando le caratteristiche maggiormente allineate alla query.

### 📌 Step E — Interfaccia per lo scout

Il sistema è utilizzabile tramite una semplice interfaccia a riga di comando o attraverso un notebook interattivo. Lo scout inserisce liberamente una descrizione del giocatore desiderato e il sistema restituisce automaticamente una shortlist dei migliori candidati, con la possibilità di visualizzare anche i punteggi di similarità o altre informazioni utili alla decisione. In questo modo, il motore di ricerca diventa un vero strumento di supporto alle attività di scouting.


- PDF Riferimento per lo svolgimento del progetto -
SII_TXPR 1,2 per motori di ricerca e IR
SII_CRFE_3 1,2 Per search engines web search, indici e BM25, Ranking
Recommender System 1,2,3,4,5 