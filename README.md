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