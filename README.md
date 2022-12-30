# [ICon] Consigliatore di Birre

### Gruppo di lavoro
- [Ester Molinari](https://github.com/burraco135), 716555
- [Giacomo Signorile](https://github.com/GiacomoSignorile), 704897

###### AA 2022-2023

## Introduzione
> Paragrafo sul dominio di interesse

Inizialmente, il dominio di interesse del KBS era basato su un dataset di [1.5 milioni di recensioni di birre](https://www.kaggle.com/datasets/rdoume/beerreviews) per poi essere sostituito da un dataset basato su [profili e valutazioni di birre](https://www.kaggle.com/datasets/ruthgn/beer-profile-and-ratings-data-set), che sfrutta i dati del dataset precedente e un dataset che analizza le [parole contenute nelle recensioni di birre](https://www.kaggle.com/datasets/stephenpolozoff/top-beer-information). Tutti i dataset raccolgono i dati forniti dal sito [BeerAdvocate](https://www.beeradvocate.com/). Durante la fase di progettazione abbiamo sfruttato l'organizzazione dei dati per realizzare i facts della KB a cui abbiamo aggiunto le features del secondo dataset, utilizzato a tutti gli effetti.

## Sommario
> Paragrafo sul KBS e su come integri moduli che dimostrino competenze sui diversi argomenti (specificati sotto)

Il nostro KBS si basa su una **ontologia** realizzata dall'interpretazione dei dati inseriti da alcuni esperti del dominio che vengono memorizzati sottoforma di **database di fatti** con le loro **regole generali** nel Sistema di learning. Mediante una **interfaccia utente**, l'utente può comunicare con il Motore Inferenziale per interrogare il sistema e ricevere una risposta. Ogni risposta verrà sfruttata dal KBS per imparare le preferenze di utenti simili. I dati nella KB vengono sottoposti ad **Apprendimento Supervisionato** prima di essere inseriti e presentano regole derivate dai risultati dell'**Apprendimento probabilistico** applicato su di essi.

Il nostro dataset `beer_profile_and_ratings.csv` presenta numerose feature non normalizzate o con valori nulli, quindi prima di popolare la KB abbiamo applicato regressione e classificazione lineare per ottenere dei valori utilizzabili dalle regole del KBS. Dopo aver corretto il dataset, abbiamo effettuato una operazione di divisione del dominio in sotto-domini che permettono di ottenere relazioni di sottoinsiemi interrogabili tramite regole Prolog.

La directory `csv` è strutturata nel seguente modo:

```
|-- csv
|   |-- beer.csv
|   |-- brewery.csv
|   |-- beer_brewery.csv
|   |-- beer_style.csv
|   |-- beer_body.csv
|   |-- beer_alcohol.csv
|   |-- beer_bitter.csv
|   |-- beer_sweet.csv
|   |-- beer_sour.csv
|   |-- beer_salty.csv
|   |-- beer_fruits.csv
|   |-- beer_hoppy.csv
|   |-- beer_spices.csv
|   |-- beer_malty.csv
```

Tutti questi file servono per popolare la KB prima di applicare le regole del KBS.

## Elenco argomenti di interesse
- [Apprendimento Supervisionato](#apprendimento-supervisionato)
- [Apprendimento Probabilistico](#apprendimento-probabilistico)
- [Sistema Basato su Conoscenza](#sistema-basato-su-conoscenza)

## Apprendimento Supervisionato

### Sommario
> Un paragrafo che chiarisca la rappresentazione della conoscenza scelta per la KB (modelli di ragionamento/apprendimento), dati, BK, ...

### Strumenti utilizzati
> Breve: non serve spiegare come funzionano se implementano modelli ben noti (basta indicare dei riferimenti bibliografici)
Dilungarsi solo su eventuali modelli/algoritmi originali ideati dal gruppo.

### Decisioni di Progetto
> Configurazione dei componenti (e.g. API/librerie) utilizzati, ad es. parametri, soglie, ecc. e di eventuali metodi specifici utilizzati a tale scopo.

### Valutazione
> Paragrafi che richiamino (non spieghino, se standard) le metriche adottate + tabelle sui risultati e loro discussione.

[Torna su](#elenco-argomenti-di-interesse)

## Apprendimento Probabilistico

### Sommario
> Un paragrafo che chiarisca la rappresentazione della conoscenza scelta per la KB (modelli di ragionamento/apprendimento), dati, BK, ...

### Strumenti utilizzati
> Breve: non serve spiegare come funzionano se implementano modelli ben noti (basta indicare dei riferimenti bibliografici)
Dilungarsi solo su eventuali modelli/algoritmi originali ideati dal gruppo.

### Decisioni di Progetto
> Configurazione dei componenti (e.g. API/librerie) utilizzati, ad es. parametri, soglie, ecc. e di eventuali metodi specifici utilizzati a tale scopo.

### Valutazione
> Paragrafi che richiamino (non spieghino, se standard) le metriche adottate + tabelle sui risultati e loro discussione.

[Torna su](#elenco-argomenti-di-interesse)

## Sistema Basato su Conoscenza

### Sommario
> Un paragrafo che chiarisca la rappresentazione della conoscenza scelta per la KB (modelli di ragionamento/apprendimento), dati, BK, ...

Durante la fase di progettazione della KB avevamo proposto due tipi di rappresentazione dei fatti mediante proposizioni:

```prolog
% rappresentazione standard
verbo(soggetto,oggetto).

% rappresentazione classe
prop(soggetto,verbo,oggetto).
```

Abbiamo scelto di utilizzare la prima rappresentazione dopo aver consultato il dataset in formato `.csv`. Abbiamo sfruttato la funzione `csv_read_file()` di Prolog insieme alla funzione `maplist()` in modo da popolare la KB senza dover inserire i valori manualmente. Per ottenere delle proposizioni composte da `verbo(soggetto,oggetto)` abbiamo scomposto il `.csv` file composti da 2 colonne, in modo da facilitare l'inserimento nella KB.

Dal punto di vista pratico, Prolog elabora i seguenti file (da aggiornare!):

```prolog
csv/beer.csv            % beer(beer_id,beer_name)
csv/brewery.csv         % brewery(brewery_id,brewery_name)
csv/beer_brewery.csv    % madeby(beer_id,brewery_id)
csv/style_style.csv     % style(beer_id,style_name
```

### Strumenti utilizzati
> Breve: non serve spiegare come funzionano se implementano modelli ben noti (basta indicare dei riferimenti bibliografici)
Dilungarsi solo su eventuali modelli/algoritmi originali ideati dal gruppo.

### Decisioni di Progetto
> Configurazione dei componenti (e.g. API/librerie) utilizzati, ad es. parametri, soglie, ecc. e di eventuali metodi specifici utilizzati a tale scopo.

### Valutazione
> Paragrafi che richiamino (non spieghino, se standard) le metriche adottate + tabelle sui risultati e loro discussione.

[Torna su](#elenco-argomenti-di-interesse)

## Conclusioni
> Un paragrafo che delinei anche possibili sviluppi (per altri gruppi)

## Riferimenti Bibliografici
[1] ...

[2] ...

[3] ...

[Torna su](#elenco-argomenti-di-interesse)
