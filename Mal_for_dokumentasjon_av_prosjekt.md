# Flask-prosjekt -- Dokumentasjon

## 1. Forside

**Drone Database:**\
**Rebecca:**\
**2IMI:**\
**11/2025:**

**Kort beskrivelse av prosjektet:**\

```markdown
Databasen holder 2 forskjellige tabeller. En tabell for "worker drones" som inneholder navn og status og en tabell for "disassembly drones". "Disassembly drones" har i tilegg også et tilfeldig serienummer hver. (Blir også gitt til nye "disassembly drones" som blir lagt til.)

Det er mulig å slette droner, legge til droner og redigere de via "view profile" knappen.
De får også en automatisk ID som ikke endrer seg. 

```
------------------------------------------------------------------------

## 2. Systembeskrivelse

**Formål med applikasjonen:**\
```markdown
## Denne databasen er basert på en scene fra en "indie" animasjonsserie (uavhengig animasjon) på youtube som heter MURDER DRONES. Jeg har tatt litt kreativ frihet ved å adaptere en database som kan vise kompetansen min med databaser i mariadb, bruk av python, flask og style.css.
```

**Brukerflyt:**\
*Beskriv hvordan brukeren bruker løsningen -- fra startside til lagring
av data.*

**Teknologier brukt:**

-   Python / Flask\
-   MariaDB\
-   HTML / CSS / JS\
-   (...wip...) 

------------------------------------------------------------------------

## 3. Server-, infrastruktur- og nettverksoppsett

### Servermiljø

*Ubuntu VM, fysisk server.*

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

------------------------------------------------------------------------

## 4. Prosjektstyring -- GitHub Projects (Kanban)

-   To Do / In Progress / Done\
-   Issues\
-   Skjermbilde (valgfritt)

Refleksjon: Hvordan hjalp Kanban arbeidet?

------------------------------------------------------------------------

## 5. Databasebeskrivelse

**Databasenavn:**

**Tabeller:**\
\| Tabell \| Felt \| Datatype \| Beskrivelse \|
\|--------\|-------\|-----------\|--------------\| \| customers \| id \|
INT \| Primærnøkkel \| \| customers \| name \| VARCHAR(255) \| Navn \|
\| customers \| address \| VARCHAR(255) \| Adresse \|

**SQL-eksempel:**

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
     ├── Prosjekt_db.docx
     └── .env

Databasestrøm:

    HTML → Flask → MariaDB → Flask → HTML-tabell

------------------------------------------------------------------------

## 7. Kodeforklaring

Forklar ruter og funksjoner (kort).

------------------------------------------------------------------------

## 8. Sikkerhet og pålitelighet

-   .env\
-   Miljøvariabler\
-   Parameteriserte spørringer\
-   Validering\
-   Feilhåndtering

------------------------------------------------------------------------

## 9. Feilsøking og testing

-   Typiske feil\ (skrivefeil, brukte /main som var en innebygd kommando)
-   Hvordan du løste dem\ (dobbeltsjekking av alt)
-   Testmetoder (Test filer! - html css for raskere/live oppdatering)

------------------------------------------------------------------------

## 10. Konklusjon og refleksjon

-   Hva lærte du?\ (Ikke gi den navn main, groove border...databaser ig)
-   Hva fungerte bra?\ (html og css)
-   Hva ville du gjort annerledes?\ (Gitt bedre navn på html fil)
-   Hva var utfordrende? (Ikke vite hva feilene var, og lage kode for random serial number)

------------------------------------------------------------------------

## 11. Kildeliste

-   w3schools\
- 
