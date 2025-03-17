***
**ESAME**
prova scritta sul materiale

esercizi e domande teoriche a risposta aperta
2 ore
***

### Cos'è una base di dati?

==*Un insieme di dati organizzati utilizzati per il supporto allo svolgimento di attività*==

POVs
1. metodologico
2. tecnologico

#### Che cos'è l'informatica?

*La scienza del trattamento razionale, specialmente per mezzo di macchine automatiche, dell'informazione, considerata come supporto alla conoscenza umana e alla comunicazione*

due anime:
- metodologica --> i metodi per la soluzione di problemi e la gestione delle informazioni
- tecnologica --> i calcolatori elettronici e i sistemi che li utilizzano

##### Sistema informativo:
- componente di un'organizzazione che gestisce le informazioni di interesse
- ogni organizzazione ha un sistema informativo, eventualmente non esplicitato nella struttura
- ==*indipendente da qualsiasi automatizzazione*==


##### Gestione delle informazioni
Raccolta, acquisizione
Archiviazione, conservazione
Elaborazione, trasformazione, produzione
Distribuzione, comunicazione, scambio


**Sistemi informativi e automazione**
- esistono organizzazioni la cui ragion d’essere è la gestione di informazioni (p.es. servizi anagrafici e banche) e che operano da secoli

#### Sistema informatico
- porzione automatizzata del sistema informativo:
    - la parte del sistema informativo che gestisce informazioni con tecnologia informatica


![[Pasted image 20250224163805.png]]

![[Pasted image 20250224163829.png]]

![[Pasted image 20250224163850.png]]

![[Pasted image 20250224163921.png]]

![[Pasted image 20250224163945.png]]


*Esempio sistema soldoni s.r.l. *


#### Gestione delle informazioni

nelle attività umane, le informazioni vengono gestite in forme diverse
1. idee informali
2. linguaggio naturale
3. disegni, grafici, schemi
4. numeri e codici
e su vari supporti:
- mente, carta, dispositivi elettronici



**Informazioni e dati**
Nei sistemi informatici (e non solo), le informazioni vengono rappresentate in modo essenziale, spartano: attraverso i dati

**==I dati sono fatti elementari, informazioni codificate, che hanno bisogno di essere interpretate per fornire conoscenza==**


- I dati costituiscono spesso una risorsa strategica, perché più stabili nel tempo di altre componenti (processi, tecnologie, ruoli umani)


#### Base di dati
*accezione generica, metodologica:*
- insieme organizzato di dati utilizzati per il supporto allo svolgimento delle attività di un ente (azienda, ufficio, persona)
*accezione specifica, metodologica e tecnologica:*
- insieme di dati gestito da un DBMS


### DBMS
==Sistema che gestisce collezioni di dati==
- grandi
- persistenti
- condivisi
garantendo
- privatezza
- affidabilità
- efficienza
- efficacia



#### ==Le basi di dati sono molto grandi==

- Quindi, i dati sono fatti elementari, informazioni codificate, che hanno bisogno di essere interpretate per fornire conoscenza
- il limite deve essere solo quello fisico dei dispositivi

#### ==Le basi di dati sono persistenti==
- Hanno un tempo di vita indipendente dalle singole esecuzioni dei programmi che le utilizzano

#### ==Le basi di dati sono condivise==
- Ogni organizzazione (specie se grande) è divisa in settori o comunque svolge diverse attività
- Ciascun settore/attività ha un (sotto)sistema informativo (non necessariamente disgiunto)


### Problemi:

- ridondanza
    - informazioni ripetute
- rischio di incoerenza
    - le versioni possono non coincidere


![[Pasted image 20250224113252.png]]

![[Pasted image 20250224113401.png]]

**Le basi di dati sono condivise:**
- Una base di dati è una risorsa integrata, condivisa fra applicazioni
- conseguenze:
    - Attività diverse su dati condivisi: 
        - meccanismi di autorizzazione
    - Accessi di più utenti ai dati condivisi: 
        - controllo della concorrenza

#### I DBMS garantiscono privatezza
si possono definire meccanismi di autorizzazione

#### I DBMS garantiscono affidabilità

**Affidabilità**
- resistenza a malfunzionamenti hw e sw
- una base di dati deve essere conservata a lungo termine
tecnica fondamentale: *gestione delle transazioni*

#### I DBMS devono essere efficienti
- Cercano di utilizzare al meglio le risorse di spazio di memoria (principale e secondaria) e tempo (di esecuzione e di risposta)
- I DBMS, con tante funzioni, rischiano l'inefficienza e per questo ci sono grandi investimenti e competizione 
- L’efficienza è anche il risultato della qualità delle applicazioni

#### I DBMS devono essere efficaci
Cercano di rendere produttive le attività dei loro utilizzatori


### Descrizione dei dati nei DBMS
Rappresentazione dei dati a livelli diversi
- permettono l'indipendenza dei dati dalla rappresentazione fisica:
    - i programmi fanno riferimento alla struttura a livello più alto, e le rappresentazioni sottostanti possono essere modificate senza necessità di modifica dei programmi



### Modello dei dati

- Insieme di costrutti utilizzati per organizzare i dati di interesse e descriverne la dinamica
- Componente fondamentale: meccanismi di strutturazione (o costruttori di tipo)
- Come nei linguaggi di programmazione esistono meccanismi che permettono di definire nuovi tipi, così ogni modello dei dati prevede alcuni costruttori


**In ogni base di dati esistono:**
1. ==Lo schema==: invariante nel tempo, che ne descrive la struttura (aspetto intensionale)
2. ==L'istanza==: i valori attuali, che possono cambiare anche molto rapidamente (aspetto estensionale)


**Due tipi di modelli**
1. modelli **logici**
2. modelli **concettuali**

#### Modelli logici
- ==adottati nei dbms esistenti per l'organizzazione dei dati==
    - utilizzati dai programmi
    - indipendenti dalle strutture fisiche
- ex. relazionale, reticolare, gerarchico, a oggetti, basato su XML

### Modelli concettuali
- permettono di rappresentare i dati in modo indipendente da ogni sistema
    - cercano di descrivere i concetti del mondo reale
    - sono utilizzati nelle fasi preliminari di progettazione
- ex. *entity-relationship*

## Architettura di un dbms

![[Pasted image 20250224174930.png]]

- **schema logico**: descrizione della base di dati nel modello logico (ex. struttura tabella)
- **schema interno (o fisico)**: rappresentazione dello schema logico per mezzo di strutture di memorizzazione (file: ad esempio, record di puntatori)


- **il livello logico è indipendente da quello fisico:**
    - – una tabella è utilizzata nello stesso modo qualunque sia la sua realizzazione fisica (che può anche cambiare nel tempo)


#### Architettura standard (ANSI/SPARC) a tre livelli per dbms

![[Pasted image 20250224175540.png]]
#### Architettura (ANSI/SPARC): schemi
- **schema logico**: descrizione dell’intera base di dati nel modello logico “principale” del DBMS
- **schema interno**: rappresentazione dello schema logico per mezzo di strutture fisiche di memorizzazione
- ==**schema esterno**: descrizione di parte della base di dati in un modello logico (“viste” parziali, derivate, anche in modelli diversi)==

#### Indipendenza dei dati
- conseguenza dell'articolazione in livelli
- l'accesso avviene solo tramite il livello esterno (che può coincidere con il livello logico)
- 2 forme
    - i. fisica
    - i. logica

**Indipendenza fisica**
- il livello logico e quello esterno sono indipendenti da quello fisico
    - una relazione è utilizzata nello stesso modo qualunque sia la sua realizzazione fisica
    - la realizzazione fisica può cambiare senza che debbano essere modificati i programmi
**Indipendenza logica**
- il livello esterno è indipendente da quello logico
- aggiunte o modifiche alle viste non richiedono modifiche al livello logico
- modifiche allo schema logico che lascino inalterato lo schema esterno sono trasparenti





**==Disponibilità di vari linguaggi==**


### MySQL

*"Trovare i corsi tenuti in aule a piano terra"*

![[Pasted image 20250224180441.png]]

`SELECT Corso, Aula, Piano`
`FROM Aule, Corsi`
`WHERE Nome = Aula`
    `AND Piano = "Terra"`


**==Facciamo una distinzione==**

**DML** (data manipulation language)
- per l’interrogazione e l’aggiornamento di (istanze di) basi di dati
**DDL** (data definition language)
- per la definizione di schemi (logici, esterni, fisici) e altre operazioni generali
- ex:
![[Pasted image 20250224180944.png]]

