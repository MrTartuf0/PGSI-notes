***
### Personaggi e interpreti

- **progettisti** e realizzatori di dbms
- **progettisti alla base di dati** e amministratori della base di dati (DBA)
- progettisti e programmatori **di applicazioni**
- **utenti**
    - **utenti finali** (terminalisti) eseguono applicazioni predefinite (transazioni)
    - **utenti casuali**: eseguono operazioni non previste a priori, usando linguaggi interattivi

### Database admin (DBA)

- persona o gruppo di persone responsabile del controllo centralizzato e della gestione del sistema, delle prestazioni, delle affidabilità, delle autorizzazioni
- Le funzioni del DBA includono quelle di progettazione, anche se in progetti complessi ci possono essere distinzioni

### Vantaggi e svantaggi del dbms

**Pro**
- dati come risorsa comune, base di dati come modello della realtà
- gestione centralizzata con possibilità di standardizzazione ed "economia di scala"
- disponibilità di servizi integrati
- riduzione di ridondanze e inconsistenze
- indipendenza dei dati
**Contro**
- costo dei prodotti e transizione verso di essi



# Il modello relazionale

- prodotto da E.F. Codd nel 1970 per favorire ==l'indipendenza dei dati==
- disponibile in dbms reali a partire dagli anni '80
- si basa su:
    - ==concetto matematico di relazione==, proprio della teoria degli insiemi
    - concetto intuitivo di ==tabella==
- le relazioni hanno naturale rappresentazione per mezzo di tabelle


### Indipendenza dei dati

- è importante che ci sia una separazione tra il livello logico e quello fisico
- deve essere possibile interagire con il livello logico senza conoscere i dettagli del livello fisico (*indipendenza fisica*)
- I modelli preesistenti il modello relazionale (gerarchico e reticolare) non garantivano l’indipendenza dei dati, in quanto includevano riferimenti alla struttura realizzativa (uso di puntatori)


#### Relazione: 3 accezioni

1) r. matematica: *come nella teoria degli insiemi*
2) r. secondo il modello relazionale dei dati
3) r. che rappresenta una classe di fatti, nel ==modello Entity-Relationship==


**Relazione matematica**

- d1 e d2 due insiemi
- **==prodotto cartesiano==**
    - insieme di tutte le coppie v1, v2 tali che v1 appartiene a d1 e v2 appartiene a d
- **relazione (matematica)** su d1 e d2
    - un sottoinsieme di d1xd2

**Relazioni e tabelle**
- le relazioni possono essere rappresentate facilmente sotto forma tabellare
    - ogni colonna rappresenta uno degli n domini Di
    - ogni riga rappresenta un elemento della relazione


**Relazioni e dati**
- Le relazioni (e le corrispondenti tabelle) possono essere usate per rappresentare i dati di interesse in una qualche applicazione.

- ==una relazione matematica è un insieme di n-uple **ordinate** tali che v1 appartiene d1 ... vn appartiene a dn==
- una relazione è un insieme; quindi:
    - ***non c'è ordinamento fra le n-uple***
    - ***le n-uple sono distinte***
    - ***ciascuna n-upla è ordinata**:* l'i-esimo valore proviene dall'i-esimo dominio
        - ordinamento fra i domini


==Nell'uso delle relazioni per rappresentare i dati **l'ordinamento** delle n-uple è importante==

![[Pasted image 20250226175452.png]]
*(se invertiamo i valori nelle ultime due colonne l'informazione cambia)*


### Notazione posizionale e non

- L’ordinamento fra i domini di una relazione è una caratteristica non soddisfacente di relazione matematica quando vogliamo usare una relazione per rappresentare i dati
- **È preferibile avere una notazione non posizionale**, in cui ciascun dato possa essere identificato indipendentemente dalla propria posizione nella n-upla


**Attributi**
- possiamo ottenere una notazione non posizionale associando a ciascun dominio su cui è definita la relazione, un nome (**attributo**) che ne descrive il ruolo

![[Pasted image 20250226175709.png]]

![[Pasted image 20250226180730.png]]

==**UNA RELAZIONE SU X E' UN INSIEME DI TUPLE SU X**==

#### Commenti
La differenza tra questa definizione di relazione e la precedente (relazione matematica) sta nella ==differenza tra n-upla e tupla==:

- in una **n-upla** gli elementi sono individuati per posizione
- in una **tupla** gli elementi sono individuati per mezzo degli attributi



- una **tabella** rappresenta una **relazione se**
    - i valori di ogni colonna sono fra loro omogenei
    - le righe sono diverse fra loro
    - le intestazioni delle colonne sono diverse tra loro
- *in una tabella che rappresenta una relazione:*
    - l'ordinamento tra le righe ==è irrilevante==
    - l'ordinamento tra le colonne ==è irrilevante==


## Riferimenti fra relazioni
In molti casi è necessario creare dei riferimenti tra dati in relazioni diverse

![[Pasted image 20250226182026.png]]


#### Il modello relazionale è basato su valori

Nel modello relazionale i riferimenti fra dati in relazioni diverse sono rappresentati per mezzo di valori comuni che compaiono nelle tuple

***vantaggi:***
- indipendenza dalle strutture fisiche che possono cambiare dinamicamente
- Si rappresenta solo ciò che è rilevante dal punto di vista dell’applicazione
- L’utente finale vede gli stessi dati dei programmatori
- I dati sono portabili più facilmente da un sistema ad un altro



## Riassunto definizioni

==**Schema di relazione**==
un nome di relazione R e un insieme di attributi X={A1 , ..., An }, denotato con R(A1 ,..., An ) o R(X)

==**Schema di base di dati**==
insieme di schemi di relazione: R = {R1 (X1 ), ..., Rk (Xk )}

==**Tupla**==
- Una tupla su un insieme di attributi X è una funzione che associa a ciascun attributo A in X un valore del dominio di A 
- t[A] denota il valore della tupla t sull'attributo A

**==Istanza di relazione / base di dati==**
- (Istanza di) relazione su uno schema R(X): insieme r di tuple su X
- (Istanza di) base di dati su uno schema R= {R1 (X1 ), ..., Rn (Xn )}: insieme di relazioni r = {r1 ,..., rn } (con ri istanza di relazione su Ri )



## Informazione incompleta

- il modello relazionale impone ai dati una struttura rigida
    - le informazioni sono rappresentate per mezzo di tuple
    - solo alcuni formati di tuple sono ammessi: quelli che corrispondono agli schemi di relazione
- ==i dati disponibili possono non corrispondere al formato previsto==

possibile soluzione con valori non utilizzati?

- i vnu potrebbero non esistere
- potrebbero diventare significativi

#### informazione incompleta nel modello relazionale
- si adotta la tecnica del **valore nullo**
    - `NULL`
    - denota l'assenza di un valore del dominio


**Tipi di valore nullo**
1) sconosciuto
2) inesistente
3) senza informazione

- i dbms non distinguono i tipi di valore nullo


## Vincoli di integrità

- ==esistono istanze di basi di dati che non rappresentano informazioni possibili per l'applicazione d'interesse pur sintatticamente corrette==

- **vincolo d'integrità** = proprietà che deve essere soddisfatta dalle istanze che rappresentano informazioni corrette per l'applicazione
- un vincolo è una funzione booleana: associa ad ogni istanza il valore **vero** o **falso**


Ma perché?
- permettono descrizione più accurata della realtà
- contributo alla "qualità dei dati"
- utili nella progettazione
- usati dai dbms nell'esecuzione delle interrogazioni

==**NB**==: non tutte le proprietà di interesse sono rappresentabili per mezzo di vincoli formulabili in modo esplicito


### Tipi di vincoli

- ==vincoli intrarelazionali==: sono definiti su una singola relazione
    - vincoli di tupla: valutabili su una singola tupla
    - vincoli su valori (*o **di dominio***): valutabili su un singolo valore
- ==vincoli interrelazionali==: su più relazioni


## Chiave

==insieme di attributi che identificano le tuple di una relazione==

- un insieme K di attributi è **superchiave** per una relazione r se r non contiene due tuple con t1[K] = t2[K]
- K è **chiave** per r se è una superchiave minimale per r (cioè non contiene un’altra superchiave)


### Vincoli, schemi e istanze

- I vincoli corrispondono a proprietà del mondo reale modellato dalla base di dati
- Interessano a livello di schema (con riferimento cioè a tutte le istanze)
- Ad uno schema associamo un insieme di vincoli e consideriamo corrette (valide, ammissibili) le istanze che soddisfano tutti i vincoli
- Un'istanza può soddisfare altri vincoli (“per caso”)


### Esistenza delle chiavi

- **==una relazione non può contenere tuple distinte ed uguali==**
- ==ogni relazione ha come superchiave l'insieme degli attributi su cui è definita==
- e quindi ha (almeno) una chiave


##### L'importanza delle chiavi

- La presenza di **un vincolo di chiave** garantisce l’**esistenza di un insieme di attributi** (quelli che formano la chiave) **che consentono di identificare univocamente le tuple della relazione**
- La presenza delle chiavi garantisce quindi l’accessibilità a ciascun dato della base di dati
- Le chiavi permettono di correlare i dati in relazioni diverse:


##### In presenza di valori nulli:
i valori della chiave non permettono
- di identificare le tuple
- di realizzare facilmente i riferimenti ad altre relazioni

![[Pasted image 20250226192512.png]]
la presenza di valori nulli nelle chiavi deve essere limitata



==**una chiave primaria** è una chiave in cui non sono ammessi valori nulli==
- notazione: *sottolineatura*


