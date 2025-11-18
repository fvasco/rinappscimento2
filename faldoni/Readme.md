# RinAppScimento 2 – Estensibilità tramite Faldoni

RinAppScimento supporta un sistema di **estensioni modulari** che permette alla
comunità di creare e condividere nuove **classi di personaggi**, completamente
integrabili nell’applicazione.

Chiunque può pubblicare un proprio **faldone** — un file YAML —
che potrà essere importato direttamente nell’app per ampliare il set di
contenuti disponibili.

---

## 📁 Cos’è un Faldone?

Un *faldone* è un file YAML che definisce una o più classi personalizzate,
insieme ai loro bonus, abilità, equipaggiamento iniziale e tabelle casuali.

L’app legge automaticamente la struttura e rende utilizzabili i nuovi contenuti.

---

## 🧩 Struttura di un Faldone (con commenti inline)

Di seguito un esempio annotato del formato utilizzato:

```yaml
# Nome del faldone, mostrato nell’app
nome: Faldone di esempio
licenza: Creative Commons, Attribuzione 4.0 Internazionale

# Elenco delle classi contenute in questo faldone
classi:
- nome: Iettatore              # Nome della classe
  autori:                      # Elenco degli autori del contenuto
  - Rosario Chiàrchiaro
  # Descrizione lunga della classe
  descrizione: Lo iettatore un maestro nell'arte di far cadere i dadi in modo sfavorevole
    per gli avversari.
  # Equipaggiamento iniziale
  averi: Un set di dadi truccati, un amuleto portafortuna e una fama che lo precede.

  # Ogni elemento in "bonus" rappresenta un beneficio che la classe possiede
  bonus:
  - tipo: "statistica"         # Modifica una statistica
    statistica: carisma        # Nome della statistica: forza, destrezza, saggezza, carisma
    quantita: 1                # Quantità del bonus
  - tipo: "salute"             # Aggiunge punti salute
    quantita: 1
  - tipo: "salvezza"           # Bonus ai tiri salvezza
    quantita: 2
  - tipo: "oggetto"            # Fornisce un oggetto iniziale
    nome: Dadi Truccati
    ingombro: 0                # Ingombro in slot: 0, 1, 2
  - tipo: "abilita"            # Aggiunge un'abilità speciale
    nome: Malocchio dei Dadi
    descrizione: Può lanciare un malocchio sui dadi degli avversari, effettua una
      prova carisma per costringerlo a rilanciare un dado a loro scelta.

  # Lista degli avanzamenti ottenuti salendo di livello
  avanzamenti:
  - 'Miglioria: +1 ad una Statistica a scelta.'
  - 'Maestro dell''Iettatura: Può influenzare il risultato dei dadi una volta per
    sessione per sessione facendo tirare con vantaggo o svantaggio.'
  - 'Occhio del Destino: Una volta al giorno, può stabilire il risultato di un dado.'
  - 'Fortuna Inversa: Guadagna un bonus permanente di +1 a Carisma.'

  # Elenchi con tabelle collegate per oggetti o scelte iniziali
  elenchi:
  - nome: Amuleto Portafortuna
    descrizione: Un amuleto che si dice porti fortuna a chi lo possiede. Effettua
      una prova di Carisma per convincere qualcuno della sua efficacia.
    tabella: AMULETI
    quantita_iniziale: 1

  # Tabelle collegate solo a questa classe
  tabelle:
    AMULETI:
    - Amuleto del Gatto Nero
    - Ciondolo della Mano di Fatima
    - Braccialetto delle Quattro Foglie
    - Collana del Quadrifoglio
    - Anello del Serpente

  # Dadi che può accumulare durante il gioco
  dadi:
  - nome: Dadi Truccati
    descrizione: Hai un dado per livello che puoi aggiungere o sottrarre ad un dado
      qualsiasi lanciato da un avversario.
    facce: 6
    quantita_iniziale: 1
  - nome: Iella
    descrizione: Puoi stabilire un evento sfortunato che colpirà un avversario. Puoi
      portare iella una volta per livello per ogni sessione di gioco. La iella non
      può uccidere e non può essere evitata con tiri salvezza.
    # Un dado ad una faccia è un contatore
    facce: 1
    quantita_iniziale: 1

# Tabelle generali del faldone, disponibili per tutte le classi al suo interno
# Le tabelle comuni sono: FALLIMENTI, NOMI, MIRACOLI, MOTIVAZIONI_PER_CAMPARE, PAROLE_OCCULTE_AZIONI, PAROLE_OCCULTE_OGGETTI
tabelle:
  NOMI:
  - Tizio
  - Caio
  - Sempronio

```
