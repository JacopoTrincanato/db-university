## CONSEGNA

Modellare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## TABLES
-Dipartimenti
-Corsi di Laurea
-Corsi
-Insegnanti
-appelli d'Esame
-Studenti
-?Voti

## DIPARTIMENTI
-id | BIGINT - AUTOINCREMENT - PK (UNIQUE - NOTNULL)
-name | VARCHAR(30) - NOTNULL
-location | VARCHAR(20) - NOTNULL
-description | TEXT(500) - NULL
-foundation_year | YEAR - NULL

## CORSI DI LAUREA
-id | BIGINT - AUTOINCREMENT - PK (UNIQUE - NOTNULL)
-dipartimenti_id | BIGINT - AUTOINCREMENT - FK (UNIQUE - NOTNULL)
-name | VARCHAR(20) - NOTNULL
-description | TEXT(500) - NULL

## CORSI
-id | BIGINT - AUTOINCREMENT - PK (UNIQUE - NOTNULL)
-corsi_di_laurea_id | BIGINT - AUTOINCREMENT - FK (UNIQUE - NOTNULL)
-insegnanti_id | BIGINT - AUTOINCREMENT - FK (UNIQUE - NOTNULL)
-name | VARCHAR(20) - NOTNULL

## INSEGNANTI
-id | BIGINT - AUTOINCREMENT - PK (UNIQUE - NOTNULL)
-name | VARCHAR(15) - NOTNULL
-lastname | VARCHAR(30) - NOTNULL
-email | VARCHAR(30) - NULL

## appelli d'Esame
## Studenti
## Voti