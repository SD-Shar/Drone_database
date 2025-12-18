# Flask-prosjekt -- Dokumentasjon

## 1. Forside

**Drone Database**\
**Rebecca**\
**2IMI**\
**11/2025**


**Kort beskrivelse av prosjektet:**

Denne databasen er basert på en scene fra en indie animasjonsserie (indie er tatt fra det engelske ordet "independent" som i denne konteksten betyr at serien er produsert av en uavhengig gruppe med kunstnere og animatører) på youtube som heter MURDER DRONES. I serien er det en scene som viser en enkel database med droner, og jeg tenkte at å bruke det som utgangspunk for prosjektet mitt ville vært gøy og en god mulighet for læring.

Jeg har tatt litt kreativ frihet ved å lage en lignende database med det jeg kunne fra før og har lært mens vi har jobbet med databaser, og stylet det til å se litt ut som serien. I tillegg har jeg lagt til flere elementer, tabeller og krav fra oppgaven vi har fått, til å vise kompetansen min med databaser i mariadb, bruk av python, flask og css.
 
 **Litt om MURDERDRONES:**

Murder Drones er en indie-animasjonsserie på YoutTube, produsert av GLITCH Productions og laget/skrevet av Liam Vickers. Det er en horror-komedie på 8 episoder og tar plass i året 3071 på en eksoplanet ved navn "Copper 9". Serien følger hovedkarakteren Uzi, en *worker drone* (robot) som møter en *disassembly drone* ved navn "N" (Bokstaven kommer fra serienummeret hans, som er på armen.)

Jeg har tatt inspirasjon fra dette og lagt det til i databasen (som du vil se lenger ned). *Worker Drones* var lagd for å utvinne ressurser fra eksoplaneter, men etter en kjernekollaps på planeten, utryddet det allt av mennenske liv. Uten mennesker adapterte *worker dronene* til en egen sivilisasjon for seg selv. På grunn av dette ble det sent "disassembly drones", som skulle fjerne *worker drones* fra planeten, siden menneskene ville ikke ha sansende og frittgående KI. *Worker dronene* gav *disassembly drones* kallenavnet "Murder Drones". (herav tittelen)

------------------------------------------------------------------------

## 2. Systembeskrivelse

**Formål med applikasjonen:**
```markdown
Databasen inneholder 2 tabeller. En tabell for *worker drones* og en tabell for *disassembly drones*.
Begge tabeller har ID, navn og status for hver drone. *Disassembly drones* har i tilegg også et tilfeldig serienummer hver.
(Dette er en referanse til serien, der alle disassembly drones har et designert serienummer.)

Det er mulig å slette droner, legge til droner og redigere de via "view profile" knappen.
Alle dronene får en ID automatisk som ikke endrer seg. 

```

### Brukerflyt:

#### Startside:

(Se brukerveiledning for mer oversikt)


**Worker Drones**
```markdown
Når programmet kjøres, åpnes det til startsiden "/overview" der det vises overskrift,
to tabeller ved siden av hverandre og to "legg til" knapper under hver tabell.

Den første kolonnen til venstre er til *wokerdrones* og viser en tabell med ID, navn, status
og muligheten til å slette dronen, se på informasjonen eller redigere det via "view profile".
```

**Disassembly Drones**
```markdown
Den neste kolonnen inneholder en tabell som viser *disassembly drones*.
Tabellen vist er helt lik *workerdrones*, med ID, navn, og status og muligheten til å redigere og/eller slette.

*Disassembly drones* har noe ekstra tilknyttet til dataen som kan bli funnet
ved å klikke på en *disassembly drone* profil.
Under navnet på dronen vil det stå et tilfeldig serienummer for hver *disassembly drone*.
```

**Delete (slett funksjon):**
```markdown
For alle droner er det en slett knapp ved siden av med navnet "Delete".
Hvis du ønsker å slette en drone vil det komme opp en pop-up-vindu som spør om du er helt sikker på valget ditt.
Om du velger å slette dronen vil den automatisk oppdatere tabellen og slette dronen fra databasen permanent.
```

**View profile (redigering av droner):**
```markdown
Alle droner i databasen har en "view profile" knapp, den vil lede brukeren til en redigerigs side (edit_WD/DD.html),
der brukeren har muligheten til å endre navn og status på dronen.

Etter man har endret navn og/eller status kan man trykke på "Update Dissassembly/Worker drone"
og da vil den oppdatere automatisk og lede brukeren tilbake til startsiden med den nye endringen(e).
Det er ikke mulig å endre serienummeret til en *disassembly drone*.
```



## Installasjon

1. **Klon prosjektet:**
```markdown
   git clone https://github.com/SD-Shar/Drone_database.git
```

2. **Installer krav:**
  ```markdown
   ```bash
   pip install flask
   pip install mysql.connector
   .env - med eget passord
```

### Teknologier brukt:
```markdown

-   Python / Flask\
-   MariaDB\
-   HTML / CSS / JS\

```

------------------------------------------------------------------------

## 3. Server-, infrastruktur- og nettverksoppsett

### Servermiljø
```markdown
*Ubuntu v.25, Mariadb, Raspberry pi*
```
### Nettverksoppsett
```markdown
-   IP-adresser\
ip-adresser for server (raspberry pi): 10.200.14.11 
ip adresse for klient(windows): 10.2.0.31

-   Porter\ (mariadb - sudo ufw)
To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
80                         ALLOW       Anywhere
Samba                      ALLOW       Anywhere
3306/tcp                   ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
Samba (v6)                 ALLOW       Anywhere (v6)
3306/tcp (v6)              ALLOW       Anywhere (v6)
```

Eksempel (henting av informasjon, som View Profile):
```markdown
    Klient → Flask → MariaDB → Flask → Klient
```


### Tjenestekonfigurasjon

```markdown
-   systemctl / Supervisor\
-   Filrettigheter\
-   Miljøvariabler

```

------------------------------------------------------------------------

## 4. Prosjektstyring -- GitHub Projects (Kanban)
```markdown
-   Backlog / In Progress / Done\

Refleksjon:

- Jeg brukte Kanban litt senere enn jeg skulle i prodjektet fordi jeg visste ikke om det, og at vi skulle bruke det.
Jeg har brukt en personlig logg hver dag for å skrive ned plan for dagen og holde styr på hva jeg skal gjøre og har gjort.
Jeg tok screenshots for å sammenligne hva jeg ville ha som gjorde oppdateringer mye mer oversiktlige.

- Med bruk av Kanban var ting litt mer oversiktlig og jeg kunne dele opp det jeg skulle gjøre i små oppgaver. 
```

------------------------------------------------------------------------

## 5. Databasebeskrivelse

### Databasenavn:
```markdown
drone_db
```

### Tabeller:

```markdown

workerD tabell:
+--------+--------------+------+-----+---------+----------------+
| Field  | Type         | Null | Key | Default | Extra          |
+--------+--------------+------+-----+---------+----------------+
| id     | int(11)      | NO   | PRI | NULL    | auto_increment |
| name   | varchar(255) | YES  |     | NULL    |                |
| status | varchar(255) | YES  |     | NULL    |                |
+--------+--------------+------+-----+---------+----------------+

disassemblyD tabell:
+--------+--------------+------+-----+---------+----------------+
| Field  | Type         | Null | Key | Default | Extra          |
+--------+--------------+------+-----+---------+----------------+
| id     | int(11)      | NO   | PRI | NULL    | auto_increment |
| name   | varchar(255) | YES  |     | NULL    |                |
| status | varchar(255) | YES  |     | NULL    |                |
| serial | varchar(255) | YES  |     | NULL    |                |
+--------+--------------+------+-----+---------+----------------+

```

**### SQL-eksempel:** 
```markdown
``` sql

CREATE TABLE workerD (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  status VARCHAR(255)
);

CREATE TABLE disassemblyD (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  status VARCHAR(255)
);

```
------------------------------------------------------------------------

## 6. Programstruktur 

    Prosjekt_uke/
     ├── app.py
     ├── templates/
     ├── static/
     ├── brukerveiledning
     └── .env

Databasestrøm:

    HTML → Flask → MariaDB → Flask → HTML-tabell

------------------------------------------------------------------------

## 7. Kodeforklaring
```markdown
```python

@app.route("/")
def index():
    return redirect("/overview")

def get_connection():
    return mysql.connector.connect(
        host="localhost",
        user="username",
        password="password",
        database="name"
    )

```
Den øverste (@app.route) henter startsiden (overview.html), og get_connection(): henter database informasjonen.
get_connection(): vil bli hentet igjen i de andre kodedelene når de henter data fra databasen.


```markdown
```python
@app.route('/overview')
def drones():
    
    mydb = get_connection()
    mycursor = mydb.cursor()
    mycursor.execute("SELECT * FROM workerD")
    workerD = mycursor.fetchall() #liste??
    
    mycursor.execute("SELECT * FROM disassemblyD")
    disassemblyD = mycursor.fetchall() #liste??
    
    return render_template('overview.html', workerD=workerD, disassemblyD=disassemblyD)
```
Først så henter @app.route drone-informasjonen fra databasen.
Den definerer "drones" (def drones()), kaller på get_connection, definerer mycursor til mydb.cursor() ,
så gjør den mycursor.execute() og henter alt (SELECT * FROM) fra både *worker drones* og *disassembly drones*.
Den setter opp informasjonen som en liste med mycursor.fetchall() og return render_template til hoved-siden.



```markdown
```python
import random

def serialNumber():
    s = list(''.join(random.choice('01') for _ in range(9)))
    x_pos = random.randrange(9)
    s[x_pos]= 'X'
    return ''.join(s)
```


Dette er koden brukt for å generere et tilfeldig serienummer til disassembly dronene.

"s" er listen av number, "x_pos" står for x position som velger random plass i listen, så settes x_pos inn i s.
Den bruker "join(random.choice('01')) for _ in range (9)" som skal velge et random tall, enten 0 eller 1,
og printe ut det helt til den fyller ut range (9).
Så setter den X i et random sted i stringen (random.randrange(9)).
Deretter setter den inn den ukjente x-verdien og definerer den som "X"
og "return" printer en sammendratt string av tilfeldige 0 og 1 tall, med en inblandet "X"

```markdown
```python
@app.route("/overview/add_WD", methods=["GET", "POST"])
def add_WD():
    
    if request.method == "POST":
        name = request.form["name"]
        status = request.form["status"]
    (...)    

```

Dette utdraget av kode er tatt ut fra starten av koden som legger til nye *worker drones*.
Den tar @app.route til html siden "add_WD" og bruker "GET" og "POST" til å hente informasjon og plassere den inn i tabellen (som klipp og lim).
"if request.method == "POST":" sier at når man skal plassere dataen inn i tabellen fra det den har hentet,
skal den sette navnet i feltet "name" og status i feltet "status". 


------------------------------------------------------------------------

## 8. Sikkerhet og pålitelighet

-   .env\
-   Miljøvariabler\
-   Parameteriserte spørringer\
-   Validering\
-   Feilhåndtering

------------------------------------------------------------------------

## 9. Feilsøking og testing


**### Feil jeg møtte**
```markdown
-   Typiske feil jeg fikk var skrivefeil eller forvirrende funksjonsnavn.
Jeg hadde først brukt "/main" for min "main page" som jeg fant ut var en innebygd kommando.
Dette gjorde at ting var litt forvirrende på starten, men etter jeg fikk fikset det så gikk det greit.

Noe annet jeg hadde gjort galt på begynnelsen var at jeg ikke hadde seperert funksjonsnavnene til
*disassembly drones* og *worker drones* og hadde bare brukt "def drones():" for begge.
Noen småting var også ikke linket sammen p.g.a. skrivefeil på funksjoner og noen ganger id navn på html elementer.
```

**### Løsning**
```markdown
-   Hvordan jeg løste det: Dobbelsjekking av alt!
```

**### Testmetoder:**
```markdown
- Lagde test filer for å få en raskere/live oppdatering på css.
Jeg lagde en seperat mappe og kopierte html sidene,
i tilegg til css så jeg kunne gjøre små endringer i css uten
å måtte kjøre koden via terminalen hver gang for å se endringene.

```

------------------------------------------------------------------------

## 10. Konklusjon og refleksjon

**Hva lærte jeg?**
```markdown
- Jeg lærte at "main" var en innebygd back-end kommando som ikke er lurt å gi navn til index siden. 
Jeg lærte litt mer om databaser; hvordan automatisk oppdatering fungerer og hvordan Mariadb håndterer nye kolonner og tabeller.
Jeg lærte også hvordan man kan lage en tilfeldig nummergenerator i python, med en extra variabel innblandet.

I tillegg så lærte jeg om funksjonene "GET" og "POST"
og at det trengs for å hente og lime inn/plassere informasjon tatt fra databasen.
```

**Hva fungerte bra?**
```markdown
- Jeg vil si at prosjektet gikk ganske bra generelt,
jeg ble ferdig relativt raskt og hadde god tid til å fikse småting som farger, style og utseende.
Jeg ble fornøyd med hvordan resultatet så ut og hvordan html og css samarbeidet. 
```

**Hva ville jeg gjort annerledes?**
```markdown
- Til neste gang ville jeg vært mer oppmerksom på navnene jeg gir funksjoner og filer, dobbeltsjekke alt, i tillegg til å ikke gi noen filnavn "main".
```

**Hva var utfordrende?**
```markdown
- Noe som var litt utfordrene var når jeg ikke visste hva som skapte feilene,
dette fant jeg ut av eventuelt men det å måtte lese gjennom hele koden flere ganger ble ganske slitsomt etterhvert.

Det var også helt nytt for meg å lage en tilfeldig serienummer generator,
og jeg fant ikke noe på nett som var det jeg lette etter så jeg måtte spørre chatgpt om det.

Jeg ville helst ikke bruke KI, men koden jeg fikk var enkel nok til å forstå og virket brukbar,
så nå har jeg noe jeg kan bruke til en annen gang hvis jeg trenger noe lignende.
```
------------------------------------------------------------------------

## 11. Kildeliste

```markdown
-   w3schools\
-   Tidligere oppgaver (Hovedsakelig til koden og mysql CREATE kommandoer)
```

### Laget av
```markdown
- Rebecca

```
