 
<p class="has-line-data" data-line-start="0" data-line-end="1">Installare xampp su pc windows 11, (serve xampp con PHP 8.2.12)</p>
<p class="has-line-data" data-line-start="2" data-line-end="3">scaricare kalkun e gammu</p>
<p class="has-line-data" data-line-start="4" data-line-end="5">(kalkun versione: 0.8.3.2_forPHP8.2.12 - <a href="https://sourceforge.net/projects/kalkun/files/v0.8.3.2/Kalkun_v0.8.3.2_forPHP8.2.12.zip/download">https://sourceforge.net/projects/kalkun/files/v0.8.3.2/Kalkun_v0.8.3.2_forPHP8.2.12.zip/download</a> )</p>
<p class="has-line-data" data-line-start="6" data-line-end="7">gammu ultima versione per windows</p>
<p class="has-line-data" data-line-start="8" data-line-end="9">(gammu per windows versione 1.42 windows 64 bit - <a href="https://dl.cihar.com/gammu/releases/windows/Gammu-1.42.0-Windows-64bit.exe">https://dl.cihar.com/gammu/releases/windows/Gammu-1.42.0-Windows-64bit.exe</a>)</p>
<p class="has-line-data" data-line-start="11" data-line-end="12">dopo aver installato xampp importare la kartella kslkun in c:\xampp\htdocs\kalkun</p>
<p class="has-line-data" data-line-start="13" data-line-end="14">(effettuare alcune configurazioni sul config kalkun, pee accettare database mariadb - mySQL)</p>
<p class="has-line-data" data-line-start="15" data-line-end="37">c:\xampp\htdocs\kalkun\application\database.php<br>
$db[‘kalkun_mysql’] = array(<br>
‘dsn’   =&gt; ‘’,<br>
‘hostname’ =&gt; ‘127.0.0.1’,<br>
‘username’ =&gt; ‘username del database con diritti ROOT’,<br>
‘password’ =&gt; ‘password dell’utente database’,<br>
‘database’ =&gt; ‘database creato, di solito “kalkun”’,<br>
‘dbdriver’ =&gt; ‘mysqli’,<br>
‘dbprefix’ =&gt; ‘’,<br>
‘pconnect’ =&gt; FALSE,<br>
‘db_debug’ =&gt; (ENVIRONMENT !== ‘production’),<br>
‘cache_on’ =&gt; FALSE,<br>
‘cachedir’ =&gt; ‘’,<br>
‘char_set’ =&gt; ‘utf8mb4’,<br>
‘dbcollat’ =&gt; ‘utf8mb4_general_ci’,<br>
‘swap_pre’ =&gt; ‘’,<br>
‘encrypt’ =&gt; FALSE,<br>
‘compress’ =&gt; FALSE,<br>
‘stricton’ =&gt; FALSE,<br>
‘failover’ =&gt; array(),<br>
‘save_queries’ =&gt; TRUE<br>
);</p>
<p class="has-line-data" data-line-start="38" data-line-end="39">abilitare su php.ini: ;extension=intl (togliendo il ;), riavviare xampp diciamo.</p>
<p class="has-line-data" data-line-start="40" data-line-end="41">disabilitare “core” (come da foto allegata) da “sicurezza di windiws/condivisione memoria”, e riavviare il pc. (questo serve per installare i drivers modem con mobile partner)</p>
<p class="has-line-data" data-line-start="42" data-line-end="43"><a href="https://www.huaweicalculator.com/download-mobile-partner-23-015-02-01-910/">https://www.huaweicalculator.com/download-mobile-partner-23-015-02-01-910/</a></p>
<p class="has-line-data" data-line-start="44" data-line-end="45">installare Mobile_Partner_23.015.11.01.983  (che trovi in “tutto il necessario”)</p>
<p class="has-line-data" data-line-start="46" data-line-end="47">(riavviare il pc?!?!?!)</p>
<p class="has-line-data" data-line-start="48" data-line-end="49">andare su localhost/phpmyadmin</p>
<p class="has-line-data" data-line-start="50" data-line-end="51">creare un nuovo utente “root” dal nome che volete</p>
<p class="has-line-data" data-line-start="52" data-line-end="53">dare tutti i permessi, password “xxxxxxxxx”</p>
<p class="has-line-data" data-line-start="54" data-line-end="55">creare una password per utente root di MySQL.</p>
<p class="has-line-data" data-line-start="56" data-line-end="66">creare nuovo database: kalkun<br>
modificare il db mysql.sql (Gammu-1.42.0-Windows-64bit\share\doc\gammu\examples\sql) cosi:<br>
da:<br>
ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP,<br>
a:<br>
ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,<br>
e da<br>
MultiPart enum(‘false’,‘true’) default ‘false’,<br>
a:<br>
MultiPart varchar(6) NOT NULL DEFAULT ‘0’,</p>
<p class="has-line-data" data-line-start="67" data-line-end="68">(un avolo di bug, che nn fa inviare i messaggi multipart da kalkun, molto grave, ma cosi si risolve!!!)</p>
<p class="has-line-data" data-line-start="69" data-line-end="74">sotto la voce:<br>
Signal integer NOT NULL DEFAULT -1,<br>
aggiungere una voce simile:<br>
Signao integer NOT NULL DEFAULT -1,<br>
(altro problema, mysql nn accetta dati con nome “Signal” e noi ne creiamo un’altra con nome Signao, poi vi spoego perche!)</p>
<p class="has-line-data" data-line-start="75" data-line-end="76">salvare.</p>
<p class="has-line-data" data-line-start="77" data-line-end="78">e importare il db di gammu con phpmyadmin</p>
<p class="has-line-data" data-line-start="81" data-line-end="83">installare: Visual-C-Runtimes-All-in-One-Jul-2025<br>
<a href="https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/">https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/</a></p>
<p class="has-line-data" data-line-start="84" data-line-end="85">poi installare ODBC, scrivere con WIN+R “odbcad32.exe”, eseguirlo,</p>
<p class="has-line-data" data-line-start="86" data-line-end="87">seconda tab, DNS di sistema, creare 1 nuovo con “aggiungi”, scegliere:</p>
<p class="has-line-data" data-line-start="88" data-line-end="89">MySQL ODBC (9.3 o 8.0 a seconda di cosa installiamo, io ho la 9.3)</p>
<p class="has-line-data" data-line-start="90" data-line-end="93">data source name: ODBCkalkun<br>
description:      ODBCkalkun<br>
TCP/IP Server:    localhost (porta 3306)</p>
<p class="has-line-data" data-line-start="94" data-line-end="97">user:     utente creato con permessi ROOT su phpmyadmin<br>
password: xxxxxxxx<br>
database: kalkun</p>
<p class="has-line-data" data-line-start="98" data-line-end="99">avanzate, scegliere utf8mb4</p>
<p class="has-line-data" data-line-start="101" data-line-end="102">test connection… OK… Fatto.</p>
<p class="has-line-data" data-line-start="104" data-line-end="106">da web andare su localhost/kalkun e seguire le istruzioni, caricare il db (gia modificato)<br>
e tutto dovrebbe essere verde, rinominare il file install in: install___ e login con</p>
<p class="has-line-data" data-line-start="107" data-line-end="108">kalkun/kalkun</p>
<p class="has-line-data" data-line-start="109" data-line-end="110">e iniziare a inviare sms</p>
<p class="has-line-data" data-line-start="111" data-line-end="114">per gammu, verificare porta COM modem e modificare sia gammurc che smsdrc<br>
e anche il file reg con PID E UID (particolari della com visrtuale dalla lista hardware id)<br>
aggiungere il reg al registro e via!</p>
<p class="has-line-data" data-line-start="115" data-line-end="116">per testare comunicazione con modem:</p>
<p class="has-line-data" data-line-start="117" data-line-end="118">cd\</p>
<p class="has-line-data" data-line-start="119" data-line-end="120">cd gammu</p>
<p class="has-line-data" data-line-start="121" data-line-end="122">gammu -c C:\gammu\gammurc identify</p>
<p class="has-line-data" data-line-start="124" data-line-end="125">per avviare il daemon da riga di comando (poi sia xampp che gammu)</p>
<p class="has-line-data" data-line-start="126" data-line-end="127">gammu-smsd -c C:\gammu\smsdrc</p>
<p class="has-line-data" data-line-start="128" data-line-end="129">e kalkun invia e riceve sms</p>
<p class="has-line-data" data-line-start="130" data-line-end="132">possiamo rieseguire xampp come amministratore e installare i servizi per MySQL e apache ()<br>
(il tastino alla sinistra sei 2 applicativi cosi installiamo i servizi e via!!!)</p>
<p class="has-line-data" data-line-start="135" data-line-end="138">per verificare il servizio:<br>
sc query GammuSMSD<br>
Oppure apri services.msc e cerca “GammuSMSD”</p>
<p class="has-line-data" data-line-start="139" data-line-end="140">e dovrebbe andare tutto bene!!!</p>
<p class="has-line-data" data-line-start="141" data-line-end="143">per accedere alla pagina di kalkun come admin:<br>
kalkun/kalkun</p>
<p class="has-line-data" data-line-start="144" data-line-end="152">BONUS:<br>
per poter eseguire gammu-smsd.exe con MySQL (OBDC), essendo Signal un comando interno a MySQL, ma anche una tabella gammu<br>
per indicare il valore del segnale GSM, bisogna patchare l’eseguibile “gammu-smsd.exe” con un hex editor:<br>
aprirlo quindi (quando nn è in esecuzione, ovviamente!) con un hex editor (neo hex editor), portarsi all’offset: 000F7CE0 e li vedrete “Signal”, cambiatelo in Signao<br>
cosi gammu cerchera di creare e aggiornare la chiave “Signao” e nn piu signal, che interrompe esecuzione<br>
dell’ exe per incompatibilità con mySQL engine.<br>
fatto cio, salvate, eseguite e appost! ora sto usando ultima versione di GAMMU 64 bit e kalkun su xampp ultima versione<br>
per PHP 8.2.12 e tutto funziona alla perfezione, e su WINDOWS!!! che non è poco!!!</p>
<p class="has-line-data" data-line-start="153" data-line-end="156">BONUS2:<br>
per risolvere il problema del mancato invio su multipart, usare questo trick sul database (database nella cartella gammu gia mdificato ad oc!!!)<br>
e in gammu_:model nell’invio multipart, gia fixato anche nel codice php!!!</p>
<p class="has-line-data" data-line-start="157" data-line-end="159">ALTER TABLE outbox<br>
MODIFY MultiPart VARCHAR(6) NOT NULL DEFAULT ‘0’;</p>
<p class="has-line-data" data-line-start="160" data-line-end="161">(con adminer sul db, volendo!!!)</p>
<p class="has-line-data" data-line-start="162" data-line-end="175">anche su kalkun tocca fsre delle modifiche:<br>
nel file: C:\xampp\htdocs\kalkun\application\controllers\Kalkun.php<br>
cambiare:<br>
da:<br>
$response[‘signal’] = intval($this-&gt;Kalkun_model-&gt;get_gammu_info(‘phone_signal’)-&gt;row(‘Signal’));<br>
a:<br>
$response[‘signal’] = intval($this-&gt;Kalkun_model-&gt;get_gammu_info(‘phone_signal’)-&gt;row(‘Signao’));<br>
(per accedere alla voce del db modificato che viene riempito da gammu-smsd.exe patchatiìo!)<br>
nel file: C:\xampp\htdocs\kalkun\application\models\Kalkun_model.php<br>
da:<br>
$this-&gt;db-&gt;select(‘Signal’);<br>
a:<br>
$this-&gt;db-&gt;select(‘Signao’);</p>
<p class="has-line-data" data-line-start="177" data-line-end="181">ora, per inviare multipart con 1 e 0 amziche true e false (il famoso bug per cui gammu nn invia sms multipart, dopo li invierà!!!)<br>
nel file: C:\xampp\htdocs\kalkun\application\models\gateway\Gammu_model.php<br>
sotto:<br>
‘RelativeValidity’ =&gt; $tmp_data[‘validity’],</p>
<p class="has-line-data" data-line-start="182" data-line-end="184">aggiunfere:<br>
‘MultiPart’        =&gt; 0, // default sempre 0</p>
<p class="has-line-data" data-line-start="185" data-line-end="190">e<br>
sotto la linea:<br>
$data[‘UDH’] = $tmp_data[‘UDH’] . sprintf(’%02X’, $tmp_data[‘part’]) . ‘01’;<br>
aggiungere:<br>
$data[‘MultiPart’] = 1; //////‘true’;</p>
<p class="has-line-data" data-line-start="191" data-line-end="195">ok, finito, ora avete:<br>
gammu-smsd.exe patchato per comunicare il segnale GSM in modo che ODBC o cmq MySQL lo accettano (Signao, al posto di Signal)<br>
mysql.sql, aggiornato per accettare in modo corretto la voce multipart e la voce “Signao” che fa si che gammu-smsd.exe non crashi perhce nn trova tabella (Signao) giusta<br>
kalkun modificato per accettare la ovce signao e mostrarla come segnale GSM, multipart da inviare foxato.</p>
<p class="has-line-data" data-line-start="196" data-line-end="197">avviate il tutto e vedrete che tutto funzionerà alla grande!</p>

</body></html>
