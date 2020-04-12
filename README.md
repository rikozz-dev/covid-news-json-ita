# covid-news-json-ita

Benvenuto nella repo di covid-news-json-ita

## Cos'è?

è una libreria di files *.json in cui sono salvati tutte le città italiane suddivise per regione

## Dove posso osservare tutto in tempo reale?

La mappa interattiva dei contagi è hostata qui > [PRYSM/covid-news](https://www.prysmlab.com/covid-news)

insieme ai dati provenienti da altre fonti attendibili quali [Protezione Civile](https://www.protezionecivile.it/attivita-rischi/rischio-sanitario/emergenze/coronavirus),
[ECDC](https://www.ecdc.europa.eu/en/geographical-distribution-2019-ncov-cases), [World Healt Organization](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports), 
[Johns Hopkins CSSE](https://systems.jhu.edu/), [CDC](https://www.cdc.gov/coronavirus/2019-ncov/index.html).

## Come si usa?

Semplice, all'interno della cartella 'reg-jsons', ogni regione ha il suo file JSON, denominato

```bash
  reg-nomeregione.json
```

dove ovviamente 'nomeregione' è da sostituire con il nome della regione di riferimento.

**Creando o modificando un qualsiasi file copiarlo nella cartella 'reg-jsons-archive', rinominandolo 'reg-nomeregione-yyyy-mm-dd-username.json', (dove: yyyy = anno, es. 2020; mm = mese, es. 04; dd = giorno es. 01; username = username di github), quindi se dobbiamo archiviare il file 'reg-lazio.json' e ci chiamiamo gianfranco-69 lo rinomineremo 'reg-lazio-2020-04-09-gianfranco-69.json', dove la data inserita sta a dichiarare la data in cui il file è stato creato.**

Facendo un esempio, se voglio inserire 'Roma', dovrò andare a cercare il file 'reg-lazio.json' ed inserire Roma secondo la struttura proposta di seguito.
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

è disponibile un template ('reg-template.json') da cui fare copia/incolla per l'inserimento di nuovi dati o l'aggiornamento di dati esistenti

la struttura del singolo dato è

```json
  {
      "denominazione_citta": "Alghero",
      "sigla_provincia": "SS",
      "lat": 40.557952,
      "lng": 8.319295,
      "totale_casi": 4,
      "tamponi_eseguiti": "56",
      "isolamento": "???",
      "morti": "1",
      "dimessi_guariti" : "???",
      "data_aggiornamento": "2020-04-05T01:00",
      "fonti_notizie": [
          { "nome_fonte": "Giornale 123", "link_fonte": "https://www.xxxxxxxx.it/zzzzzz", "data_fonte": "2020-03-28T12:00", "descrizione_notizia": "+1 contagio" },
          { "nome_fonte": "Giornale 456", "link_fonte": "https://www.nnnnnnnn.it/yyyyyy", "data_fonte": "2020-04-01T22:30", "descrizione_notizia": "+56 tamponi, +1 contagio" },
          { "nome_fonte": "Giornale 789", "link_fonte": "https://www.cccccccc.it/aaaaaa", "data_fonte": "2020-04-05T01:00", "descrizione_notizia": "+2 contagi" }
      ]
  }
```

di seguito le indicazioni sui valori dei singoli campi

```
  TIPO DI DATO          > :FORMATO          > DESCRIZIONE
  
  denominazione_citta   > :string           > il nome della città
  sigla_provincia       > :string           > la sigla della provincia in cui è situata la suddetta città
  lat                   > :float            > latitudine del comune
  lng                   > :float            > latitudine del comune
  totale_casi           > :int              > totale dei casi di Covid-19 (compresi i morti ed i dimessi guariti, NON comprende le persone in isolamento precauzionale ed i tamponi eseguiti)
  tamponi_eseguiti      > :int | :string    > totale dei tamponi (negativi e positivi) eseguiti sulla popolazione, se sconosciuto => "???"
  isolamento            > :int | :string    > totale delle persone in isolamento preventivo, se sconosciuto => "???"
  morti                 > :int | :string    > totale dei morti confermati, se sconosciuto => "???"
  dimessi_guariti       > :int | :string    > totale delle persone guarite, se sconosciuto => "???"
  data_aggiornamento    > :datetime         > data di aggiornamento del dato, in formato yyyy-mm-ddThh:ii (ISO8601>W3_STANDARD)
  fonti_notizie         > :array            > insieme di dati delle fonti 
  nome_fonte            > :string           > nome della fonte da cui si sono prese le notizie
  link_fonte            > :string           > link della fonte da cui si sono prese le notizie  
  data_fonte            > :datetime         > data della fonte da cui si sono prese le notizie in formato yyyy-mm-ddThh:ii (ISO8601>W3_STANDARD) 
  descrizione_notizia   > :string           > una micro descrizione della notizia con i numeri aggiornati dalla fonte, separati da una virgola ,
```

durante gli aggiornamenti su totale_casi, tamponi_eseguiti, isolamento, morti, dimessi_guariti, i valori di questi vanno sommati ai nuovi valori da aggiornare, quindi se per esempio tamponi_eseguiti è 12, se ne aggiungono 34, il nuovo valore per tamponi_eseguiti sarà 46

di seguito una panoramica delle tipologie di dati, di come sono strutturati e di come gestirli

```
  :string     >   testo comune, deve essere necessariamente accompagnato dalle virgolette " davanti e dietro; es -> "San Vero Milis"
  :float      >   valore numerico con la virgola, la virgola in realtà è un punto .; es -> 3.14159
  :int        >   valore numerico senza la virgola; es 69
  :datetime   >   valore :string con il formato yyyy-mm-ddThh:ii (ISO8601>W3_STANDARD), preceduto e seguito dalle virgolette "; es (per le 14:45 del 1 Aprile 2020) -> "2020-04-01T12:45"
  :array      >   insieme di valori [1,2,3,..] in questo caso ogni valore deve seguire il formato { "dato_generico": "valore", "dato_numerico": 123 }, serve sempre la virgola tra un valore e l'altro
```

## Importante

puoi usare questa libreria semplicemente sfruttando i RAW di GitHub, con il link strutturato in

```
	https://raw.githubusercontent.com/rikozz-dev/covid-news-json-ita/master/reg-jsons/reg-nomeregione.json
```

ovviamente 'reg-nomeregione.json' va cambiato secondo il nome della regione di interesse, per esempio per la Sardegna sarà 'reg-sardegna.json'

**SE USI QUESTA LIBRERIA NEI TUOI PROGETTI CITA LA FONTE**

perché ti stanno fornendo la risorsa gratuitamente ed il minimo che puoi fare è citare questa libreria

**LE CITTA' VANNO MESSE IN ORDINE ALFABETICO PER UNA QUESTIONE DI FACILITA' NELL'AGGIORNARE I DATI DA PARTE DI TUTTI**

se non sono in ordine per favore dai tu il tuo contributo riordinandole

**NON CARICARE I DATI SE NON SEI SICURO DI QUELLO CHE STAI SCRIVENDO**

è per questo che vogliamo che tu inserisca sempre la fonte, con un link alla notizia

**OGNI AGGIORNAMENTO DATI PREVEDE L'INSERIMENTO DI UNA NUOVA FONTE AUTOREVOLE**

per evitare di creare inutili allarmismi e/o false notizie

## Credits

Autore: [Riccardo Ortu](https://www.instagram.com/rikozz_)

### Per la Sardegna

[Giacomo Collu](https://www.instagram.com/giacomo_collu), collaboratore

[Riccardo Ortu](https://www.instagram.com/rikozz_), creatore, inserimento dati

[Roberto Martis](https://www.instagram.com/rootvanterr), inserimento dati

.

.

### Grazie per aver letto questa breve guida
