***
## Linguaggi per le basi di dati

- Le Basi di Dati sono usate per rappresentare le informazioni di interesse per applicazioni che gestiscono dati
- I linguaggi per la specifica delle operazioni (interrogazioni e aggiornamento) sui dati costituiscono quindi una componente essenziale delle Basi di Dati


- un **==aggiornamento==** può essere visto come una funzione che data un'istanza di una base di dati produce un'istanza sullo stesso schema
- un **==interrogazione==** può essere invece vista come una funzione che data un'istanza di una base di dati, produce un'istanza di una relazione su un dato schema


1. Linguaggi procedurali
    1. specificano le modalità di generazione del risultato ("come")
2. Linguaggi dichiarativi
    1. specificano le proprietà del risultato ("che cosa")


**Algebra e calcolo relazionale** sono due linguaggi teorici, non sono cioè disponibili nei DBMS
- l'algebra relazionale è un linguaggio procedurale
- il calcolo relazionale è un linguaggio dichiarativo
- ==entrambi consentono di fare interrogazioni ma non aggiornamento==

## Algebra relazionale

è un linguaggio costituito da un insieme di operatori
- definiti su relazioni
- che producono relazioni

poiché il risultato di ciascun operatore è ancora una relazione, è possibile comporre gli operatori

#### Operatori

- operatori insiemistici (*unione, intersezione, differenza*)
- operatori di *ridenominazione, selezione e proiezione*
- operatori di join: *join naturale, prodotto cartesiano, theta join*


**Operatori insiemistici**

- le relazioni sono insiemi
- gli operatori operano su relazioni e producono relazioni
- È quindi possibile applicare ==unione, intersezione, differenza==

==NB==: una relazione non è soltanto un insieme di tuple, ma un insieme di **==tuple omogenee==**

quindi non ha senso definire gli operatori di unione, intersezione e differenza su relazioni definite su attributi diversi

L'unione di due relazioni su schemi diversi sarebbe un insieme di tuple disomogenee


ES. unione
![[Pasted image 20250312190800.png]]


ES. intersezione
![[Pasted image 20250312190839.png]]


ES. differenza
![[Pasted image 20250312190900.png]]




##### Ridenominazione: motivazione

per garantire che le operazioni insiemistiche diano luogo a relazioni su tuple omogenee, abbiamo imposto che le operazioni insiemistiche su relazioni operino su relazioni definite sugli stessi attributi


![[Pasted image 20250312191007.png]]

### Ridenominazione

Per risolvere il problema evidenziato introduciamo uno specifico operatore di ridenominazione denotato con rho

==Tale operatore ci permette di ridenominare uno o più attributi, allo scopo di adeguare i nomi degli attributi a seconda delle necessità==

![[Pasted image 20250312191220.png]]

**L’operatore di ridenominazione modifica lo schema, non l’istanza della base di dati**

**Nelle due liste indicheremo solo gli attributi ridenominati**

![[Pasted image 20250312192036.png]]




### Selezione

denotato con sigma

il risultato ha lo stesso schema dell'operando 
il risultato contiene un sottoinsieme delle tuple dell’operando:
- quelle che soddisfano una certa condizione (==condizione di selezione==)



### Proiezione

- denotato con pigreco
- il risultato:
    - ha un sottoinsieme degli attributi dell’operando
    - **contiene le tuple che si ottengono dall’operando considerando soltanto gli attributi che compaiono nel risultato**

*Esempio:*
![[Pasted image 20250312192742.png]]
**vogliamo sapere matricola e cognome di tutti gli impiegati**

![[Pasted image 20250312192752.png]]


**Selezione:**
- *decomposizione orizzontale* (eliminazione di righe)
**Proiezione**:
- *decomposizione verticale* (eliminazione di colonne)


##### Cardinalità delle proiezioni

Il risultato di una proiezione contiene al più tante tuple quante l’operando

ne può contenere di meno qualora alcune tuple assumano gli stessi valori su tutti gli attributi della proiezione
==Le tuple uguali “collassano” in una sola tupla==


==piY (r) contiene lo stesso numero di tuple di r se e solo se Y è superchiave per r==


Combinando selezione e proiezione, possiamo estrarre interessanti informazioni da una relazione 

**Non possiamo però correlare dati in relazioni diverse**

## Join

permette di correlare dati in relazioni diverse
utilizza la caratteristica del modello relazionale di essere basato su valori

- join naturale
- theta join

es.
![[Pasted image 20250312194542.png]]

**Join naturale:**
==Gli attributi del risultato sono l’unione degli attributi degli operandi==

Dalla definizione si vede come le tuple del risultato sono ottenute combinando tuple degli operandi con valori uguali sugli attributi comuni


#### Cardinalità del join

![[Pasted image 20250312194916.png]]

![[Pasted image 20250312194926.png]]

![[Pasted image 20250312195225.png]]


### Join esterno (outer join)

La caratteristica del Join di tralasciare le tuple di una relazione che non hanno tuple corrispondenti nell’altra è utile in molti casi

Esistono però casi in cui tale caratteristica è “pericolosa”, in quanto ci fa omettere informazioni importanti


**==Le tuple che non hanno una corrispondenza vengono estese con valori nulli==**


tipi di outer join:
1. sinistro
2. destro
3. completo

Se le due relazioni hanno tutti gli attributi in comune, allora il join equivale all’intersezione

Se le due relazioni non hanno nessun attributo in comune, allora la condizione che due tuple abbiano valori uguali su attributi comuni risulta sempre banalmente verificata

==Il risultato conterrà quindi le tuple ottenute combinando, in tutti i modi possibili, le tuple degli operandi==

In questo caso il join viene chiamato prodotto cartesiano e contiene un numero di tuple |r1 | X |r2|

![[Pasted image 20250312200412.png]]

