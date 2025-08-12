 
<p class="has-line-data" data-line-start="0" data-line-end="1">Installare xampp su pc windows 11, (serve xampp con PHP 8.2.12)</p>
<p class="has-line-data" data-line-start="2" data-line-end="4">scaricare kalkun e gammu<br>
(kalkun versione: 0.8.3.2_forPHP8.2.12 - <a href="https://sourceforge.net/projects/kalkun/files/v0.8.3.2/Kalkun_v0.8.3.2_forPHP8.2.12.zip/download">https://sourceforge.net/projects/kalkun/files/v0.8.3.2/Kalkun_v0.8.3.2_forPHP8.2.12.zip/download</a> )</p>
<p class="has-line-data" data-line-start="5" data-line-end="6">gammu ultima versione per windows</p>
<p class="has-line-data" data-line-start="7" data-line-end="8">(gammu per windows versione 1.42 windows 64 bit - <a href="https://dl.cihar.com/gammu/releases/windows/Gammu-1.42.0-Windows-64bit.exe">https://dl.cihar.com/gammu/releases/windows/Gammu-1.42.0-Windows-64bit.exe</a>)</p>
<p class="has-line-data" data-line-start="10" data-line-end="11">dopo aver installato xampp importare la kartella kalkun in c:\xampp\htdocs\kalkun</p>
<p class="has-line-data" data-line-start="12" data-line-end="13">(effettuare alcune configurazioni sul config kalkun, pee accettare database mariadb - mySQL)</p>
<p class="has-line-data" data-line-start="14" data-line-end="36">c:\xampp\htdocs\kalkun\application\database.php<br>
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
<p class="has-line-data" data-line-start="37" data-line-end="38">abilitare su php.ini: ;extension=intl (togliendo il ;), riavviare xampp diciamo.</p>
<p class="has-line-data" data-line-start="39" data-line-end="40">disabilitare “core” da “sicurezza di windiws/condivisione memoria”, e riavviare il pc. (questo serve per installare i drivers modem con mobile partner)</p>
<p class="has-line-data" data-line-start="41" data-line-end="42"><a href="https://www.huaweicalculator.com/download-mobile-partner-23-015-02-01-910/">https://www.huaweicalculator.com/download-mobile-partner-23-015-02-01-910/</a></p>
<p class="has-line-data" data-line-start="43" data-line-end="44">installare Mobile_Partner_23.015.11.01.983  (che trovi in “tutto il necessario”)</p>
<p class="has-line-data" data-line-start="45" data-line-end="46">(riavviare il pc?!?!?!)</p>
<p class="has-line-data" data-line-start="47" data-line-end="48">andare su localhost/phpmyadmin</p>
<p class="has-line-data" data-line-start="49" data-line-end="50">creare un nuovo utente con permessi “root” dal nome che volete</p>
<p class="has-line-data" data-line-start="51" data-line-end="52">dare tutti i permessi, password “xxxxxxxxx”</p>
<p class="has-line-data" data-line-start="53" data-line-end="54">creare una password per utente root di MySQL.</p>
<p class="has-line-data" data-line-start="55" data-line-end="65">creare nuovo database: kalkun<br>
modificare il db mysql.sql (Gammu-1.42.0-Windows-64bit\share\doc\gammu\examples\sql) cosi:<br>
da:<br>
ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP,<br>
a:<br>
ReceivingDateTime timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,<br>
e da<br>
MultiPart enum(‘false’,‘true’) default ‘false’,<br>
a:<br>
MultiPart varchar(6) NOT NULL DEFAULT ‘0’,</p>
<p class="has-line-data" data-line-start="66" data-line-end="67">(un avolo di bug, che nn fa inviare i messaggi multipart da kalkun, molto grave, ma cosi si risolve!!!)</p>
<p class="has-line-data" data-line-start="68" data-line-end="73">sotto la voce:<br>
Signal integer NOT NULL DEFAULT -1,<br>
aggiungere una voce simile:<br>
Signao integer NOT NULL DEFAULT -1,<br>
(altro problema, mysql nn accetta dati con nome “Signal” e noi ne creiamo un’altra con nome Signao, poi vi spoego perche!)</p>
<p class="has-line-data" data-line-start="74" data-line-end="75">salvare.</p>
<p class="has-line-data" data-line-start="76" data-line-end="77">e importare il db di gammu con phpmyadmin</p>
<p class="has-line-data" data-line-start="80" data-line-end="82">installare: Visual-C-Runtimes-All-in-One-Jul-2025<br>
<a href="https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/">https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/</a></p>
<p class="has-line-data" data-line-start="83" data-line-end="84">poi installare ODBC, scrivere con WIN+R “odbcad32.exe”, eseguirlo,</p>
<p class="has-line-data" data-line-start="85" data-line-end="86">seconda tab, DNS di sistema, creare 1 nuovo con “aggiungi”, scegliere:</p>
<p class="has-line-data" data-line-start="87" data-line-end="88">MySQL ODBC (9.3 o 8.0 a seconda di cosa installiamo, io ho la 9.3)</p>
<p class="has-line-data" data-line-start="89" data-line-end="92">data source name: ODBCkalkun<br>
description:      ODBCkalkun<br>
TCP/IP Server:    localhost (porta 3306)</p>
<p class="has-line-data" data-line-start="93" data-line-end="96">user:     utente creato con permessi ROOT su phpmyadmin<br>
password: xxxxxxxx<br>
database: kalkun</p>
<p class="has-line-data" data-line-start="97" data-line-end="98">avanzate, scegliere utf8mb4</p>
<p class="has-line-data" data-line-start="100" data-line-end="101">test connection… OK… Fatto.</p>
<p class="has-line-data" data-line-start="103" data-line-end="105">da web andare su localhost/kalkun e seguire le istruzioni, caricare il db (gia modificato)<br>
e tutto dovrebbe essere verde, rinominare il file install in: install___ e login con</p>
<p class="has-line-data" data-line-start="106" data-line-end="107">kalkun/kalkun</p>
<p class="has-line-data" data-line-start="108" data-line-end="109">e iniziare a inviare sms</p>
<p class="has-line-data" data-line-start="110" data-line-end="113">per gammu, verificare porta COM modem e modificare sia gammurc che smsdrc<br>
e anche il file reg con PID E UID (particolari della com visrtuale dalla lista hardware id)<br>
aggiungere il reg al registro e via!</p>
<p class="has-line-data" data-line-start="114" data-line-end="116">nel file: gammurc file: inserire la giusta COMPORT<br>
esempio:</p>
<p class="has-line-data" data-line-start="117" data-line-end="120">[gammu]<br>
device = COM5<br>
connection = at115200</p>
<p class="has-line-data" data-line-start="121" data-line-end="122">salvare</p>
<p class="has-line-data" data-line-start="123" data-line-end="124">nel file smsdrc invece, per comunicazione con drive SQL ODBC:</p>
<p class="has-line-data" data-line-start="125" data-line-end="128">[gammu]<br>
device = COM5<br>
connection = at115200</p>
<p class="has-line-data" data-line-start="129" data-line-end="130">[smsd]</p>
<p class="has-line-data" data-line-start="131" data-line-end="133">CheckSecurity = false  ###nn manda warn se nn c’e PIN<br>
PIN =</p>
<p class="has-line-data" data-line-start="134" data-line-end="135">SMSC = +393770001016 ### Centro messaggi HO Mobule</p>
<p class="has-line-data" data-line-start="136" data-line-end="140">commtimeout = 10 ###30<br>
sendtimeout = 10 ###30<br>
MaxRetries  = 10<br>
DeliveryReport = log</p>
<p class="has-line-data" data-line-start="141" data-line-end="147">service = sql<br>
driver = odbc<br>
host = ODBCkalkun<br>
user = utente con permessi ROOT che abbiamo aggiunto in phpmyadmin<br>
password =password dell’ utente con permessi root cosi come da phpmyadmin<br>
database = kalkun ### il database che abbiamo creato sul db, sempre con phpmyadmin</p>
<p class="has-line-data" data-line-start="148" data-line-end="150">LogFile = smsd.log<br>
debuglevel = 2 ### da 0 (less) a 255 (full)</p>
<p class="has-line-data" data-line-start="151" data-line-end="152">RunOnReceive = C:\xampp\htdocs\kalkun\scripts\daemon.bat</p>
<p class="has-line-data" data-line-start="153" data-line-end="156">HangupCalls = 1<br>
RunOnIncomingCall = c:\gammu\call_autoreply.bat (lo script è mio, ma potete crearne uno voi per rispondere alle<br>
chiamate in arrivo, dopo aver riagganciato “HangupCalls = 1”)</p>
<h5 class="code-line" data-line-start=156 data-line-end=157 ><a id="FINE_FILE_156"></a>FINE FILE</h5>
<p class="has-line-data" data-line-start="157" data-line-end="158">salvate e via…</p>
<p class="has-line-data" data-line-start="159" data-line-end="160">ok salvate e ora…</p>
<p class="has-line-data" data-line-start="161" data-line-end="162">per testare comunicazione con modem:</p>
<p class="has-line-data" data-line-start="163" data-line-end="164">cd\</p>
<p class="has-line-data" data-line-start="165" data-line-end="166">cd gammu</p>
<p class="has-line-data" data-line-start="167" data-line-end="168">gammu -c C:\gammu\gammurc identify</p>
<p class="has-line-data" data-line-start="170" data-line-end="171">per avviare il daemon da riga di comando (poi sia xampp che gammu)</p>
<p class="has-line-data" data-line-start="172" data-line-end="173">gammu-smsd -c C:\gammu\smsdrc</p>
<p class="has-line-data" data-line-start="174" data-line-end="175">e kalkun invia e riceve sms</p>
<p class="has-line-data" data-line-start="176" data-line-end="178">possiamo rieseguire xampp come amministratore e installare i servizi per MySQL e apache ()<br>
(il tastino alla sinistra sei 2 applicativi cosi installiamo i servizi e via!!!)</p>
<p class="has-line-data" data-line-start="181" data-line-end="184">per verificare il servizio:<br>
sc query GammuSMSD<br>
Oppure apri services.msc e cerca “GammuSMSD”</p>
<p class="has-line-data" data-line-start="185" data-line-end="186">e dovrebbe andare tutto bene!!!</p>
<p class="has-line-data" data-line-start="187" data-line-end="189">per accedere alla pagina di kalkun come admin:<br>
kalkun/kalkun</p>
<p class="has-line-data" data-line-start="190" data-line-end="198">BONUS:<br>
per poter eseguire gammu-smsd.exe con MySQL (OBDC), essendo Signal un comando interno a MySQL, ma anche una tabella gammu<br>
per indicare il valore del segnale GSM, bisogna patchare l’eseguibile “gammu-smsd.exe” con un hex editor:<br>
aprirlo quindi (quando nn è in esecuzione, ovviamente!) con un hex editor (neo hex editor), portarsi all’offset: 000F7CE0 e li vedrete “Signal”, cambiatelo in Signao<br>
cosi gammu cerchera di creare e aggiornare la chiave “Signao” e nn piu signal, che interrompe esecuzione<br>
dell’ exe per incompatibilità con mySQL engine.<br>
fatto cio, salvate, eseguite e appost! ora sto usando ultima versione di GAMMU 64 bit e kalkun su xampp ultima versione<br>
per PHP 8.2.12 e tutto funziona alla perfezione, e su WINDOWS!!! che non è poco!!!</p>
<p class="has-line-data" data-line-start="199" data-line-end="202">BONUS2:<br>
per risolvere il problema del mancato invio su multipart, usare questo trick sul database (database nella cartella gammu gia mdificato ad oc!!!)<br>
e in gammu_:model nell’invio multipart, gia fixato anche nel codice php!!!</p>
<p class="has-line-data" data-line-start="203" data-line-end="205">ALTER TABLE outbox<br>
MODIFY MultiPart VARCHAR(6) NOT NULL DEFAULT ‘0’;</p>
<p class="has-line-data" data-line-start="206" data-line-end="207">(con adminer sul db, volendo!!!)</p>
<p class="has-line-data" data-line-start="208" data-line-end="221">anche su kalkun tocca fsre delle modifiche:<br>
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
<p class="has-line-data" data-line-start="223" data-line-end="227">ora, per inviare multipart con 1 e 0 anziche true e false (il famoso bug per cui gammu non invia sms multipart, dopo li invierà!!!)<br>
nel file: C:\xampp\htdocs\kalkun\application\models\gateway\Gammu_model.php<br>
sotto:<br>
‘RelativeValidity’ =&gt; $tmp_data[‘validity’],</p>
<p class="has-line-data" data-line-start="228" data-line-end="230">aggiunfere:<br>
‘MultiPart’        =&gt; 0, // default sempre 0</p>
<p class="has-line-data" data-line-start="231" data-line-end="236">e<br>
sotto la linea:<br>
$data[‘UDH’] = $tmp_data[‘UDH’] . sprintf(’%02X’, $tmp_data[‘part’]) . ‘01’;<br>
aggiungere:<br>
$data[‘MultiPart’] = 1; //////‘true’;</p>
<p class="has-line-data" data-line-start="237" data-line-end="241">ok, finito, ora avete:<br>
gammu-smsd.exe patchato per comunicare il segnale GSM in modo che ODBC o cmq MySQL lo accettano (Signao, al posto di Signal)<br>
mysql.sql, aggiornato per accettare in modo corretto la voce multipart e la voce “Signao” che fa si che gammu-smsd.exe non crashi perhce nn trova tabella (Signao) giusta<br>
kalkun modificato per accettare la ovce signao e mostrarla come segnale GSM, multipart da inviare foxato.</p>
<p class="has-line-data" data-line-start="242" data-line-end="243">avviate il tutto e vedrete che tutto funzionerà allagrande!</p>

</body></html>
