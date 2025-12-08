# Flask-prosjekt -- Dokumentasjon

## 1. Forside

**Drone Database:**\
**Rebecca:**\
**2IMI:**\
**11/2025:**

!!!

**Kort beskrivelse av prosjektet:**\

```markdown
Databasen inneholder 2 forskjellige tabeller. En tabell for *worker drones* og en tabell for *disassembly drones*. Begge tabeller har ID, navn og status for hver drone. *Disassembly drones* har i tilegg også et tilfeldig serienummer hver.

Det er mulig å slette droner, legge til droner og redigere de via "view profile" knappen.
De får også en automatisk ID som ikke endrer seg. 

```
------------------------------------------------------------------------
!!!
## 2. Systembeskrivelse

**####Formål med applikasjonen:**\
```markdown
 **Denne databasen er basert på en scene fra en indie animasjonsserie (uavhengig animasjonsserie) på youtube som heter MURDER DRONES. Jeg har tatt litt kreativ frihet ved å ta utgangspunktet fra en database og lagt til flere krav som kan vise kompetansen min med databaser i mariadb, bruk av python, flask og css.**

  **Som sagt i beskrivelsen så er det mulig å legge til droner, rediegere de og slette de om ønsket. Det er en interaktiv database som gir brukeren mye frihet til å endre det de ønsker med dronene.**
```
!!!
**Brukerflyt:**

### Startside:

```markdown
(Se brukerveiledning for mer oversikt)

#### Worker Drones
Når programmet kjøres, åpnes det til html siden "/overview" der det vises overskriften som forklarer databasen, to tabeller ved siden av hverandre og to "legg til" knapper under hver tabell. Den første kolonnen til venstre er til *wokerdrones* og viser en tabell med ID, navn, status og muligheten til å slette dronen eller "view profile" som kan også være ne måte å redigere navn eller staus på.

#### Disassembly Drones
Den neste kolonnen inneholder en tabell som viser *disassembly drones*. Tabellen vist er helt lik *workerdrones*, med ID, navn, og status og muligheten til å redigere og/eller slette. *Disassembly drones* har en ekstra detalje som kan bli funnet ved å klikke på en *disassembly drone* profil, (via "View Profile" knappen). Under navnet på dronen vil det stå et tilfeldig serienummer for hver disassembly drone. Når man legger til flere *diassembly drones* vil koden automatisk gi de en streng med tall som består av 9 felt med 0,1, og èn X. (Dette er en referanse til serien der alle disassembly drones har en designert serienummer.)

### Delete (slett funksjon):
For alle droner er det en slett knapp ved siden av med navnet "Delete". hvis du ønsker å slette en drone vil det komme opp en pop-up-vindu som spør om du er helt sikker på valget ditt. Om du velger å slette dronen vil den automatisk oppdatere og slette dronen fra databasen permanent.

### View profile (redigering av droner):
Alle droner i databasen har en "view profile" knapp, den vil lede brukeren til en html side (edit_WD/DD.html), der brukeren har muligheten til å endre navn og status på dronen. Etter man har endret navn og/eller status kan man trykke på "Update Dissassembly/Worker drone" og da vil den oppdatere automatisk og lede brukeren tilbake til startsiden med den nye endringen(e). Det er ikke mulig å endre serienummeret til en *disassembly drone*



## Installasjon
1. **####Klon prosjektet:**
   git clone https://github.com/SD-Shar/Drone_database.git

2. **####Installer krav:**
   ```bash
   pip install flask
   pip install mysql.connector
   .env - med eget passord

```

**####Teknologier brukt:**

-   Python / Flask\
-   MariaDB\
-   HTML / CSS / JS\

------------------------------------------------------------------------


!??

## 3. Server-, infrastruktur- og nettverksoppsett

### Servermiljø
```markdown
*Ubuntu VM, fysisk server, Mariadb.*

### Nettverksoppsett

-   Nettverksdiagram
-   IP-adresser\
-   Porter\
-   Brannmurregler

Eksempel:

    Klient → Waitress → MariaDB

### Tjenestekonfigurasjon

-   systemctl / Supervisor\
-   Filrettigheter\
-   Miljøvariabler

```

------------------------------------------------------------------------
???

## 4. Prosjektstyring -- GitHub Projects (Kanban)
```markdown
-   To Do / In Progress / Done\
-   Issues\

Refleksjon: Hvordan hjalp Kanban arbeidet?
```

------------------------------------------------------------------------

!!!

## 5. Databasebeskrivelse

**####Databasenavn:**
```markdown
drone_db
```

**###Tabeller:**\

```markdown

workerD tabell:
+----+-------+------------+
| id | name  | status     |
+----+-------+------------+
|  1 | Doll  | infected   |
|  3 | Nori  | patched    |
|  4 | Uzi   | infected   |
|  6 | Thad  | N/A        |
|  7 | Alice | patched..? |
|  8 | null  | null       |
+----+-------+------------+

disassemblyD tabell:
+----+---------+--------+-----------+
| id | name    | status | serial    |
+----+---------+--------+-----------+
|  1 | N       | alive  | 0X0010010 |
|  2 | V       | alive  | X00100000 |
|  3 | J       | ???    | 00X111001 |
|  4 | S       | dead   | 01X101000 |
|  5 | R       | alive  | 000000000 |
|  9 | serieal | test 2 | 111111X01 |
| 10 | 1111    | 1212   | 011X01111 |
| 12 | W       | dead   | 1111X1000 |
+----+---------+--------+-----------+

```

!!!
**####SQL-eksempel:** 
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

!!!

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

!!!

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

```markdown
Den øverste app.route henter startsiden (overview.html), og get_connection(): henter database informasjonen. get_connection(): vil bli hentet igjen i de andre kodedelene.
```

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
```markdown
Først så henter denne app.route drone-informasjonen fra databasen. Den kaller på get_connection, definerer mycursor til mydb.cursor() , så gjør den mycursor.execute() og henter alt (SELECT * FROM) fra worker drones og disassembly drones. Så setter den opp som en liste med mycursor.fetchall() og return render_template til hoved-siden.
```


```markdown
```python
import random

def serialNumber():
    s = list(''.join(random.choice('01') for _ in range(9)))
    x_pos = random.randrange(9)
    s[x_pos]= 'X'
    return ''.join(s)
```
```markdown
Dette er koden brukt for å generere serienummer til disassembly drones.

s er listen av number, x_pos står for x position som velger random plass i listen,
så settes x_pos inn i s. Den bruker join(random.choice('01')) for _ in range (9) som skal velge et random tall, enten 0 eller 1, og printe ut det helt til den fyller range (9). Så setter den X i et random sted i stringen (random.randrange(9)). Den setter den ukjente x-verdien og definerer den som "X" og return printer/viser en sammendratt string av tilfeldige 0 og 1 tall, med en inblandet "X"

```


------------------------------------------------------------------------

## 8. Sikkerhet og pålitelighet

-   .env\
-   Miljøvariabler\
-   Parameteriserte spørringer\
-   Validering\
-   Feilhåndtering

------------------------------------------------------------------------
!!!
## 9. Feilsøking og testing

```markdown
**####Feil jeg møtte**
-   Typiske feil jeg fikk var skrivefeil eller forvirrende funksjonsnavn. Jeg hadde først brukt "/main" for "main page" som var en innebygd kommando. Dette gjorde at ting var litt forvirrende på starten, men etter jeg fikk fikset det så gikk det greit. Noe annet jeg hadde gjort galt på begynnelsen var at jeg ikke hadde seperert funksjonsnavnene til *disassembly drones* og *worker drones* og hadde bare brukt "def drones():" for begge. Noen småting var også ikke linket sammen p.g.a. skrivefeil på funksjoner og noen ganger id navn på html elementer.

**####Løsning**
-   Hvordan jeg løste det: Dobbelsjekking av alt!

**####Testmetoder:**
- Lagde test filer for å få en raskere/live oppdatering på css. Jeg lagde en seperat mappe og kopierte html sidene, i tilegg til css så jeg kunne gjøre små endringer i css uten å måtte kjøre koden via terminalen hver gang for å se endringene.

```

------------------------------------------------------------------------
!!!

## 10. Konklusjon og refleksjon
```markdown

**####Hva lærte jeg?**
- Jeg lærte at "main" var en innebygd back-end kommando som ikke er lurt å gi navn til index siden. 
Jeg lærte litt mer om databaser, hvordan automatisk oppdatering fungerer og hvordan Mariadb håndterer nye kolonner og tabeller. Jeg lærte også hvordan man kan lage en tilfeldig nummergenerator i python, med en extra variabel innblandet.

**####Hva fungerte bra?**
- Jeg vil si at prosjektet gikk ganske bra generelt, jeg ble ferdig relativt raskt og hadde god tid til å fikse småting som farger, style og utseende. Jeg ble fornøyd med hvordan det så ut og hvordan html og css samarbeidet. 

**####Hva ville du gjort annerledes?**
- Til neste gang ville jeg vært mer oppmerksom på navnene jeg gir funksjoner og filer, dobbeltsjekke alt, i tillegg til å ikke gi noen filnavn "main".

**####Hva var utfordrende?**
- Noe som var litt utfordrene var når jeg ikke visste hva som skapte feilene, dette fant jeg ut av eventuelt men det å måtte lese gjennom alt ble ganske slitsomt etterhvert. Det var også helt nytt for meg å lage en tilfeldig serienummer generator, og jeg fant ikke noe på nett som var det jeg lette etter så jeg måtte spørre chatgpt om det. Ville helst ikke bruke AI, men koden jeg fikk var enkel nok til å forstå og virket brukbar, så nå har jeg noe jeg kan bruke til en annen gang hvis jeg trenger noe lignende.
```
------------------------------------------------------------------------
!!!

```markdown
## 11. Kildeliste

-   w3schools\
-   Tidligere oppgaver (Hovedsakelig til koden og mysql CREATE kommandoer)

```

```markdown
### Laget av
- Rebecca

```