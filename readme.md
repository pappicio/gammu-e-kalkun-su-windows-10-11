Installare xampp su pc windows 11, (serve xampp con PHP 8.2.12)

scaricare kalkun e gammu

(kalkun versione: 0.8.3.2_forPHP8.2.12 - https://sourceforge.net/projects/kalkun/files/v0.8.3.2/Kalkun_v0.8.3.2_forPHP8.2.12.zip/download )

gammu ultima versione per windows

(gammu per windows versione 1.42 windows 64 bit - https://dl.cihar.com/gammu/releases/windows/Gammu-1.42.0-Windows-64bit.exe)

dopo aver installato xampp importare la kartella kslkun in c:\xampp\htdocs\kalkun

(effettuare alcune configurazioni sul config kalkun, pee accettare database mariadb - mySQL)

c:\xampp\htdocs\kalkun\application\database.php

$db['kalkun_mysql'] = array(
  'dsn' => '',
  'hostname' => '127.0.0.1',

 'username' => 'username del database con diritti ROOT',

 'password' => 'password dell'utente database',

 'database' => 'database creato, di solito "kalkun"',

 'dbdriver' => 'mysqli',

 'dbprefix' => '',

 'pconnect' => FALSE,

 'db_debug' => (ENVIRONMENT !== 'production'),

 'cache_on' => FALSE,

 'cachedir' => '',

 'char_set' => 'utf8mb4',

 'dbcollat' => 'utf8mb4_general_ci',

 'swap_pre' => '',

 'encrypt' => FALSE,

 'compress' => FALSE,

 'stricton' => FALSE,

 'failover' => array(),

 'save_queries' => TRUE

);

abilitare su php.ini: ;extension=intl (togliendo il ;), riavviare xampp diciamo.

disabilitare "core" (come da foto allegata) da "sicurezza di windiws/condivisione memoria", e riavviare il pc. (questo serve per installare i drivers modem con mobile partner)

https://www.huaweicalculator.com/download-mobile-partner-23-015-02-01-910/

installare Mobile_Partner_23.015.11.01.983 (che trovi in "tutto il necessario")

(riavviare il pc?!?!?!)

andare su localhost/phpmyadmin

creare un nuovo utente "root" dal nome che volete

dare tutti i permessi, password "xxxxxxxxx"

creare una password per utente root di MySQL.

creare nuovo database: kalkun

modificare il db mysql.sql (Gammu-1.42.0-Windows-64bit\share\doc\gammu\examples\sql) cosi:

da:

 ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP,

a:

 ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,

e da

 MultiPart enum('false','true') default 'false',

a:

 MultiPart varchar(6) NOT NULL DEFAULT '0',

(un avolo di bug, che nn fa inviare i messaggi multipart da kalkun, molto grave, ma cosi si risolve!!!)

sotto la voce:

 Signal integer NOT NULL DEFAULT -1,

aggiungere una voce simile:

 Signao integer NOT NULL DEFAULT -1,

(altro problema, mysql nn accetta dati con nome "Signal" e noi ne creiamo un'altra con nome Signao, poi vi spoego perche!)

salvare.

e importare il db di gammu con phpmyadmin

installare: Visual-C-Runtimes-All-in-One-Jul-2025

https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/

poi installare ODBC, scrivere con WIN+R "odbcad32.exe", eseguirlo,

seconda tab, DNS di sistema, creare 1 nuovo con "aggiungi", scegliere:

MySQL ODBC (9.3 o 8.0 a seconda di cosa installiamo, io ho la 9.3)

data source name: ODBCkalkun

description: ODBCkalkun

TCP/IP Server: localhost (porta 3306)

user: utente creato con permessi ROOT su phpmyadmin

password: xxxxxxxx

database: kalkun

avanzate, scegliere utf8mb4

test connection… OK… Fatto.

da web andare su localhost/kalkun e seguire le istruzioni, caricare il db (gia modificato)

e tutto dovrebbe essere verde, rinominare il file install in: install___ e login con

kalkun/kalkun

e iniziare a inviare sms

per gammu, verificare porta COM modem e modificare sia gammurc che smsdrc

e anche il file reg con PID E UID (particolari della com visrtuale dalla lista hardware id)

aggiungere il reg al registro e via!

per testare comunicazione con modem:

cd\

cd gammu

gammu -c C:\gammu\gammurc identify

per avviare il daemon da riga di comando (poi sia xampp che gammu)

gammu-smsd -c C:\gammu\smsdrc

e kalkun invia e riceve sms

possiamo rieseguire xampp come amministratore e installare i servizi per MySQL e apache ()

(il tastino alla sinistra sei 2 applicativi cosi installiamo i servizi e via!!!)

per verificare il servizio:

sc query GammuSMSD

Oppure apri services.msc e cerca "GammuSMSD"

e dovrebbe andare tutto bene!!!!!

per accedere alla pagina di kalkun come admin:

admin/Infosystem10

BONUS:

per poter eseguire gammu-smsd.exe con MySQL (OBDC), essendo Signal un comando interno a MySQL, ma anche una tabella gammu

per indicare il valore del segnale GSM, bisogna patchare l'eseguibile "gammu-smsd.exe" con un hex editor:

aprirlo quindi (quando nn è in esecuzione, ovviamente!) con un hex editor (neo hex editor), portarsi all'offset: 000F7CE0 e li vedrete "Signal", cambiatelo in Signao

cosi gammu cerchera di creare e aggiornare la chiave "Signao" e nn piu signal, che interrompe esecuzione

dell' exe per incompatibilità con mySQL engine.

fatto cio, salvate, eseguite e appost! ora sto usando ultima versione di GAMMU 64 bit e kalkun su xampp ultima versione

per PHP 8.2.12 e tutto funziona alla perfezione, e su WINDOWS!!!!!! che non è poco!!!!!!

BONUS2:

per risolvere il problema del mancato invio su multipart, usare questo trick sul database (database nella cartella gammu gia mdificato ad oc!!!!!)

e in gammu_:model nell'invio multipart, gia fixato anche nel codice php!!!

ALTER TABLE outbox

MODIFY MultiPart VARCHAR(6) NOT NULL DEFAULT '0';

(con adminer sul db, volendo!!!)

anche su kalkun tocca fsre delle modifiche:

nel file: C:\xampp\htdocs\kalkun\application\controllers\Kalkun.php

cambiare:

da:

 $response['signal'] = intval($this->Kalkun_model->get_gammu_info('phone_signal')->row('Signal'));

a:

 $response['signal'] = intval($this->Kalkun_model->get_gammu_info('phone_signal')->row('Signao'));

(per accedere alla voce del db modificato che viene riempito da gammu-smsd.exe patchatiìo!)

nel file: C:\xampp\htdocs\kalkun\application\models\Kalkun_model.php

da:

 $this->db->select('Signal');

a:

 $this->db->select('Signao');

ora, per inviare multipart con 1 e 0 amziche true e false (il famoso bug per cui gammu nn invia sms multipart, dopo li invierà!!!!!)

nel file: C:\xampp\htdocs\kalkun\application\models\gateway\Gammu_model.php

sotto:

  'RelativeValidity' => $tmp_data['validity'],

aggiunfere:

  'MultiPart'   => 0, // default sempre 0

e

sotto la linea:

  $data['UDH'] = $tmp_data['UDH'] . sprintf('%02X', $tmp_data['part']) . '01';

aggiungere:

  $data['MultiPart'] = 1; //////'true';

ok, finito, ora avete:

gammu-smsd.exe patchato per comunicare il segnale GSM in modo che ODBC o cmq MySQL lo accettano (Signao, al posto di Signal)

mysql.sql, aggiornato per accettare in modo corretto la voce multipart e la voce "Signao" che fa si che gammu-smsd.exe non crashi perhce nn trova tabella (Signao) giusta

kalkun modificato per accettare la ovce signao e mostrarla come segnale GSM, multipart da inviare foxato.

avviate il tutto e vedrete che tutto funzionerà allagrande!
