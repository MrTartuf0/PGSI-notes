***

- i riferimenti fra dati in relazioni diverse sono rappresentati per mezzo di valori comuni che compaiono nelle tuple

### Integrità referenziale

- Informazioni in relazioni diverse sono correlate attraverso valori comuni
- In particolare, valori delle chiavi (primarie)
- ==Le correlazioni debbono essere "coerenti"==


### Vincolo di integrità referenziale

- Un vincolo di integrità referenziale (“foreign key”) fra gli attributi X di una relazione R1 e un’altra relazione R2 impone ai valori su X in R1 di comparire come valori della chiave primaria di R2


ES. ==Vincoli di integrità referenziale fra==: gli attributi Prov e Numero di INFRAZIONI e la relazione AUTO
![[Pasted image 20250310110021.png]]




![[Pasted image 20250310105823.png]]
*violazione del vincolo d'integrità referenziale*

- I vincoli di Integrità referenziale giocano un ruolo fondamentale nel concetto di “modello basato su valori.”
- In presenza di valori nulli i vincoli possono essere resi meno restrittivi


### Integrità referenziale e valori nulli

In alcuni casi è però ragionevole ammettere la presenza di valori nulli anche in corrispondenza di attributi sottoposti a vincolo di integrità referenziale

![[Pasted image 20250310191015.png]]

- Vincolo di integrità referenziale tra l’attributo Studente della rel. ESAMI e la rel. STUDENTI
- **Non è ragionevole ammettere valori nulli su Studente: non può esistere un esame sostenuto da nessuno studente**


![[Pasted image 20250310191159.png]]

- Vincolo di integrità referenziale tra l’attributo Progetto della rel. IMPIEGATI e la rel. PROGETTI
- In questo caso è ragionevole ammettere valori nulli su Progetto: ci può essere un impiegato che in un dato momento non sia impegnato in nessun progetto


### Azioni compensative

- A seguito di operazioni di modifica/cancellazione di tuple in una relazione R1 si può creare una situazione inconsistente in un’altra relazione R2 se esiste un vincolo di integrità referenziale tra un attributo di R2 e R1

![[Pasted image 20250310105201.png]]

a quale progetto fa riferimento  XYZ?


**I DBMS offrono la possibilità di specificare delle azioni che devono essere intraprese quando si verifica una violazione di un vincolo di integrità referenziale a seguito di una modifica/cancellazione**

![[Pasted image 20250310105310.png]]

#### Eliminazione in cascata

![[Pasted image 20250310105500.png]]
- Vincolo di integrità referenziale tra l’attributo Studente della rel. ESAMI e la rel. STUDENTI
- Supponiamo di cancellare lo studente Rossi Mario
- ==Le righe relative agli esami di Rossi Mario vengono cancellate come conseguenza==


#### Introduzione di valori nulli

![[Pasted image 20250310105635.png]]

- Vincolo di integrità referenziale tra l’attributo Progetto della rel. IMPIEGATI e la rel. PROGETTI
- Supponiamo di rimuovere il progetto XYZ da PROGETTI
- L’attributo Progetto di tutti gli impiegati coinvolti nel progetto XYZ assumono valore NULL


#### Commenti

- I vincoli di Integrità referenziale giocano un ruolo fondamentale nel concetto di “modello basato su valori.”
- In presenza di valori nulli i vincoli possono essere resi meno restrittivi
- Sono possibili meccanismi per il supporto alla loro gestione ("azioni" compensative a seguito di violazioni)


### Vincoli su più attributi

- Quando si definisce un vincolo di integrità referenziale che coinvolge più attributi, l’ordine con cui appaiono gli attributi nella definizione del vincolo è significativo
- Se cioè definiamo un vincolo di integrità referenziale tra due attributi a1 e a2 di una relazione R1 e la chiave b1 e b2 di una relazione R2 , stiamo chiedendo che a1 assuma valori che appaiono in b1 e a2 valori che appaiono in b2

ES.
![[Pasted image 20250310110706.png]]
vincolo d'integrità referenziale tra:
- Prov e Numero di INFRAZIONI e Prov e Numero di AUTO
- ProvB e NumB di INCIDENTI e AUTO


