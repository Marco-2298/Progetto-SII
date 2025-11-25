🔵 INTRODUZIONE AL PROGETTO

L’obiettivo del progetto è analizzare retrospettivamente i Draft NBA utilizzando un dataset storico contenente tutte le scelte dal 1947 al 2024, includendo statistiche di carriera aggiornate per ogni giocatore.

Il fine è studiare:

quali draft hanno generato il maggior valore complessivo,

quali college producono più talenti,

come classificare i giocatori in categorie qualitative,

la relazione tra posizione di scelta e longevità,

l’evoluzione delle prestazioni dei giocatori nei primi anni di carriera.

Successivamente, il lavoro sarà esteso con una seconda parte dedicata a un sistema intelligente basato sui concetti del corso, per assistere uno scout NBA nella ricerca del profilo ideale di giocatore tramite un motore di ricerca testuale e un recommender content-based.

PARTE 1 — ANALISI STORICA DEI DRAFT NBA

(Basata su un unico dataset storico 1947–2024)

📌 Step 1 — Esplorazione iniziale del dataset

Caricamento del dataset CSV contenente tutte le scelte NBA dal 1947 al 2024.

Verifica dei campi disponibili (Pick, Player, College, WS, VORP, Seasons, Ruolo…).

Controllo dei valori mancanti, dei tipi di dato e consistenza generale.

📌 Step 2 — Pulizia e normalizzazione

Uniformazione dei nomi delle colonne.

Gestione dei valori nulli per WS, College, Seasons, ecc.

Creazione di colonne derivate utili (es. fascia di pick: Top10, FirstRound, SecondRound).

📌 Step 3 — Analisi del valore generato dalle classi di Draft

Obiettivo: capire quali anni sono stati più produttivi.

Calcolo del valore totale generato per anno (WS e VORP aggregati).

Visualizzazione delle migliori e peggiori classi storiche.

Discussione di draft particolarmente impattanti o deludenti.

📌 Step 4 — Analisi dei college più produttivi

Obiettivo: individuare quali università tendono a produrre giocatori di maggior impatto.

Aggregazione delle Win Shares per college.

Classifica dei 20 college più produttivi.

Interpretazione dei risultati (programmi NCAA più efficaci).

📌 Step 5 — Classificazione qualitativa dei giocatori (Tier Analysis)

Obiettivo: categorizzare i giocatori sulla base dell’impatto reale.

Creazione di una colonna Tier con valori ad esempio:

⭐ Star (WS ≥ 50)

🔥 Starter (WS 20–49)

🔄 Role Player (WS 5–19)

💀 Flop (WS < 5)

Analisi:

distribuzione dei tier nel dataset,

distribuzione dei tier per decade o per posizione di pick.

📌 Step 6 — Analisi della longevità in base al pick

Obiettivo: capire se la posizione nel draft influisce sulla lunghezza della carriera.

Calcolo della media delle stagioni giocate per ogni pick.

Confronto tra gruppi:

Top 10

Fine primo giro

Secondo giro

Undrafted

Interpretazione dei risultati (la scelta alta garantisce una carriera più lunga?).

📌 Step 7 — Analisi evolutiva dei giocatori: Rookie → Sophomore

Poiché le statistiche del dataset sono aggiornate al 2024 e includono anche anni futuri dei giocatori recenti, una previsione “hhistorica” non è metodologicamente valida.

Tuttavia, è possibile analizzare come i giocatori migliorano dal primo al secondo anno, un insight molto utile.

Passi:

Filtrare giocatori con almeno 2 stagioni (Seasons >= 2).

Confrontare WS, PTS, AST, REB fra anno da rookie e sophomore.

Identificare i “miglioratori” e gli “stagnanti” per ruolo o per fascia di pick.

📌 Step 8 — Sintesi e discussione dei risultati

Identificazione dei migliori draft all-time.

College con maggiore impatto storico.

Percentuale di flop vs star per generazione.

Relazione tra pick → longevità → probabilità di diventare star.

Miglioratori più significativi dopo il primo anno (rookie development study).

🔶 PARTE 2 — SISTEMA INTELLIGENTE PER TALENT SCOUT NBA

(Questa è la parte in piena linea con Sistemi Intelligenti per Internet)

🎯 Obiettivo della Parte 2

Sviluppare un motore di ricerca + sistema di raccomandazione che assista un direttore sportivo o scout nel trovare il giocatore ideale in base a una descrizione testuale.

Esempio input:

"Cerco una guardia tiratrice con ottime percentuali da 3, buon FT%, forte rimbalzista offensivo."

Il sistema deve restituire un ranking dei giocatori più simili al profilo richiesto.

📌 Step A — Preparazione del corpus

Trasformare ogni giocatore in un “documento testuale”:
“Guardia, 40% da 3, 88% FT, 6 rimbalzi, buon difensore…”

Creazione del corpus JSON o DataFrame da indicizzare.

📌 Step B — Indicizzazione (Information Retrieval)

Utilizzo di BM25 o TF-IDF per l’indicizzazione dei profili.

Costruzione di un indice persistente.

📌 Step C — Analisi della query naturale

Parsing testuale dell’input utente.

Mappatura delle parole chiave su attributi giocatore:

“tiratore” → 3P%

“rimbalzista” → REB

“playmaker” → AST

“difensore” → Defensive WS

Applicazione di pesi alle feature.

📌 Step D — Ranking dei giocatori

Similarità tra query e documenti indicizzati → ranking finale.

Output: top‐N giocatori più compatibili.

Possibilità di spiegazione: “questo giocatore è top-1 perché…”

📌 Step E — Interfaccia da Talent Scout

Interfaccia a riga di comando o piccola app Python.

L’utente inserisce un profilo testuale.

Il sistema restituisce la “shortlist” dei giocatori ideali.

📌 Step F — Conclusioni

Confronto tra Parte 1 (analisi scientifica) e Parte 2 (sistema intelligente).

Possibili estensioni:

integrazione con LLM per interpretazioni più evolute,

sistema ibrido tra content-based e rule-based,

profili per team (non solo per singoli giocatori).



-Esecuzione del progetto-

1) Attivare ambiente virtuale
2) Installa i requirements.txt
3) python -m pip install ipykernel

-

Passo 2 — Crea ambiente con Python 3.11
Nel terminale della cartella del progetto:
python3.11 -m venv env
Se non va, prova:
python3 -m venv env
(o anche)
py -3.11 -m venv env
Passo 3 — Attiva l’ambiente
Mac / Linux:
source env/bin/activate
Windows:
env\Scripts\activate
Vedrai (env) comparire.
Passo 4 — Installa tutto
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn jupyter ipykernel
Passo 5 — Seleziona il kernel in VS Code
Apri notebook .ipynb
In alto a destra → click su kernel → Select Kernel
Scegli quello che termina con:
/env/bin/python
🔥 A questo punto il tuo notebook funzionerà al 100%.




- PDF Riferimento per lo svolgimento del progetto -
SII_TXPR 1,2 per motori di ricerca e IR
SII_CRFE_3 1,2 Per search engines web search, indici e BM25, Ranking
Recommender System 1,2,3,4,5 