# covid-news-json-ita

Benvenuto nella repo di covid-news-json-ita

## Cos'è?

è una libreria di files *.json in cui sono salvati tutte le città italiane suddivise per regione

## Dove posso osservare tutto in tempo reale?

La mappa interattiva dei contagi è hostata [qui www.prysmlab.com/covid-news](https://www.prysmlab.com/covid-news)

insieme ai dati provenienti da altre fonti attendibili quali [Protezione Civile](https://www.protezionecivile.it/attivita-rischi/rischio-sanitario/emergenze/coronavirus),
[ECDC](https://www.ecdc.europa.eu/en/geographical-distribution-2019-ncov-cases), [World Healt Organization](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports), 
[Johns Hopkins CSSE](https://systems.jhu.edu/), [CDC](https://www.cdc.gov/coronavirus/2019-ncov/index.html).

## Come si usa?

Semplice, all'interno della cartella 'reg-jsons', ogni regione ha il suo file JSON, denominato

```bash
  reg-nomeregione.json
```

dove ovviamente 'nomeregione' è da sostituire con il nome della regione di riferimento.

**Prima di modificare un qualsiasi file copiarlo nella cartella 'reg-jsons-archive', rinominandolo 'reg-nomeregione-yyyy-mm-dd.json', (dove: yyyy = anno, es. 2020; mm = mese, es. 04; dd = giorno es. 01;), quindi se dobbiamo archiviare il file 'reg-lazio.json' lo rinomineremo 'reg-lazio-2020-04-09.json', dove la data inserita sta a dichiarare la data in cui il file archiviato è stato creato.**

Facendo un esempio, se voglio inserire 'Roma', dovrò andare a cercare il file 'reg-lazio.json' ed inserire roma secondo la struttura proposta di seguito.
Se il file 'reg-lazio.json' non esiste, lo creo secondo il formato JSON.

```json
  [
    {
      "dato_generico": "valore",
      "dato_numerico": 123
    },
    {
      "dato_generico": "valore 2",
      "dato_numerico": 456
    }
  ]
```

la struttura del singolo dato è

```json
  {
      "denominazione_citta": "Alghero",
      "sigla_provincia": "SS",
      "lat": 40.557952,
      "lng": 8.319295,
      "totale_casi": 4,
      "isolamento": "???",
      "morti": "1",
      "dimessi_guariti" : "???",
      "data": "2020-04-05T01:00",
      "link_fonte": "https://www.xxxxxxxxx.it/zzzzz"
  }
```

di seguito le indicazioni sui valori dei singoli campi

```
  TIPO DI DATO          > :FORMATO          > DESCRIZIONE
  
  denominazione_citta   > :string           > il nome della città
  sigla_provincia       > :string           > la sigla della provincia in cui è situata la suddetta città
  lat                   > :float            > latitudine del comune
  lng                   > :float            > latitudine del comune
  totale_casi           > :int              > totale dei casi di Covid-19 (compresi i morti ed i dimessi guariti, non comprende le persone in isolamento precauzionale)
  isolamento            > :int | :string    > totale delle persone in isolamento preventivo
  morti                 > :int | :string    > totale dei morti confermati
  dimessi_guariti       > :int | :string    > totale delle persone guarite
  data                  > :string           > data di aggiornamento del dato, in formato yyyy-mm-ddThh:ii (W3_STANDARD)
  link_fonte            > :string           > link della fonte da dove sono stati presi i dati
```

di seguito una panoramica dei dati, di come sono strutturati e di come gestirli

```
  :string     >   testo comune, deve essere necessariamente accompagnato dalle virgolette " davanti e dietro; es. "San Vero Milis"
  :float      >   valore numerico con la virgola, la virgola in realtà è un punto .; es. 3.14159
  :int        >   valore numerico senza la virgola; es. 2002, 18, 69
```

## Importante

**SE USI QUESTA LIBRERIA NEI TUOI PROGETTI CITA LA FONTE**

perché ti stanno fornendo la risorsa gratuitamente ed il minimo che puoi fare è citare questa libreria

**LE CITTA' VANNO MESSE IN ORDINE ALFABETICO PER UNA QUESTIONE DI FACILITA' NELL'AGGIORNARE I DATI DA PARTE DI TUTTI**

**NON CARICARE I DATI SE NON SEI SICURO DI QUELLO CHE STAI SCRIVENDO**

## Credits

Autore: [Riccardo Ortu](https://www.instagram.com/rikozz_)

Collaboratore: [Giacomo Collu](https://www.instagram.com/giacomo_collu)


In attesa di nuovi collaboratori siamo solo noi due :)
