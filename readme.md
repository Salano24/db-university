- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.

dipartimenti
- id PK AI UN NN 
- nome VARCHAR(60) NN
- descrizione TEXT NULL

studente
- id PK AI UN NN 
- nome VARCHAR(20) NN
- cognome VARCHAR(20) NN
- email VARCHAR(30) NULL
- numero VARCHAR(15) NULL
- matricola VARCHAR(10) NULL
- corso_laurea_id FK BIGINT 

corsi
- id PK AI UN NN 
- ore_lezione SMALLINT NN
- docente_id FK BIGINT NULL
- aula VARCHAR(5) NULL
- nome VARCHAR(30) NN
- programma TEXT NN
- modalità_frequenza VARCHAR(20) NULL 
 
corsi_di_laurea
- id PK AI UN NN 
- corso_id FK BIGINT
- programma TEXT NN
- durata VARCHAR(10) NULL
- data_inizio DATE NN
- sede VARCHAR(20) NN
- dipartimento_id FK BIGINT
- lingua CHAR(2) NN

insegnanti
- id PK AI UN NN 
- nome VARCHAR(20) NN
- cognome VARCHAR(20) NN
- corso_id FK BIGINT

appelli
- id PK AI UN NN 
- corso_id FK BIGINT
- data DATE NN
- nome VARCHAR(30) NN
- aula VARCHAR(5) NN
- tipologia VARCHAR(20) NULL

appelli_studente(PIVOT)
- voto DECIMAL(3, 1) NULL
- appello_status TINYINT NULL 
- appello_id FK
- studente_id FK

corsi_insegnanti(PIVOT)
- insegnanti_id FK
- corso_id FK


RELAZIONI
 OneToMany => dipartimento & corsi_di_laurea
 OneToMany => corso_di_laurea & corsi
 ManyToMany => corsi & insegnanti(pivot)
 OneToMany => corso & studente
 OneToMany => corso & appelli
 ManyToMany => studente & appelli(pivot)
 


 


