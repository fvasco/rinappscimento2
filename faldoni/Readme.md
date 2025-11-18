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
  descrizione: Lo iettatore... # Descrizione lunga della classe
  averi: Un set di dadi...     # Equipaggiamento iniziale o beni posseduti

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
    descrizione: Può lanciare...

  # Lista degli avanzamenti ottenuti salendo di livello
  avanzamenti:
  - 'Miglioria: +1 ad una Statistica a scelta.'
  - 'Maestro dell''Iettatura...'
  - 'Occhio del Destino: ...'
  - 'Fortuna Inversa...'

  # Elenchi con tabelle collegate per oggetti o scelte iniziali
  elenchi:
  - nome: Amuleto Portafortuna  # Nome dell’oggetto
    descrizione: Un amuleto che... # Descrizione
    tabella: AMULETI             # Tabella da cui viene estratto
    quantita_iniziale: 1

  # Tabelle collegate solo a questa classe
  tabelle:
    AMULETI:
    - Amuleto del Gatto Nero
    - Ciondolo della Mano di Fatima
    - Braccialetto delle Quattro Foglie
    - Collana del Quadrifoglio
    - Anello del Serpente

# Tabelle generali del faldone, disponibili per tutte le classi al suo interno
# Le tabelle comuni sono: FALLIMENTI, NOMI, MIRACOLI, MOTIVAZIONI_PER_CAMPARE, PAROLE_OCCULTE_AZIONI, PAROLE_OCCULTE_OGGETTI
tabelle:
  NOMI:
  - Tizio
  - Caio
  - Sempronio
```
