🏀 SII – NBA Draft Analysis + Scout Recommender System

Studente: Marco D’Albis
Anno: 2024/2025
Corso: Sistemi Intelligenti per Internet

📌 Obiettivi del progetto

Il progetto è articolato in due parti:

🟦 Parte 1 — Analisi dei Draft NBA (1989–2021)

Analisi retrospettiva dei draft NBA tramite dataset pubblico:

Valutazione del valore totale generato da ogni classe (Win Shares, VORP)

Identificazione dei college più produttivi

Classificazione dei giocatori in tier:

⭐ Star

🔥 Starter

🔄 Role player

💀 Flop

Analisi della longevità media in base alla posizione di scelta

Focus specifico sul Draft 2021: aspettative vs realtà

Gli script/notebook relativi sono nella cartella analysis/.

🟩 Parte 2 — Scout Recommender System (progetto SII)

Costruzione di un sistema di raccomandazione + motore di ricerca testuale per supportare uno scout NBA.

Esempio di input:

“Cerco una guardia tiratrice con ottime percentuali da 3, buon FT%, buon rimbalzo offensivo e difensivo.”

Funzionalità integrate:

Indicizzazione dei giocatori come documenti (IR)

Text parsing della query naturale

Ranking tramite BM25 e pesi dinamici

Output ordinato dei profili giocatori più compatibili

Codice nella cartella recommender/.