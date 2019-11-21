========
Utilizzo
========

Se avete ancora il terminale aperto sulla cartella *mycroft-core* potete dare subito un *ls* e ricontrollare tutti i file presenti.
Se non siete lì vi basta riaprire il terminale e digitare i seguenti comandi:

.. code-block:: bash

    $ cd
    $ cd mycroft-core
    $ ls
    
Dovreste vedere la seguente situazione:

.. code-block:: bash

    $ ls    
    bin doc mycroft scripts test coveralls.yml ACKNOWLEDGEMENTS.md CODE_OF_CONDUCT.md
    LICENSE.md MANIFEST.in README.md dev_setup.sh requirements.txt setup.py start-mycroft.sh
    stop-mycroft.sh test-requirements.txt venv-activate.sh

    

Se provate ad eseguire start-mycroft.sh senza parametri dovreste vedere la finestra seguente:

.. code-block:: bash

    $ ./start-mycroft.sh
    
    usage: start-mycroft.sh [command] [params]

    Services:
    all                      runs core services: bus, audio, skills, voice
    debug                    runs core services, then starts the CLI

    Services:
    audio                    the audio playback service
    bus                      the messagebus service
    skills                   the skill service
    voice                    voice capture service
    wifi                     wifi setup service
    enclosure                mark_1 enclosure service

    Tools:
    cli                      the Command Line Interface
    unittest                 run mycroft-core unit tests

    Utils:
    skill_container <skill>  container for running a single skill
    audiotest                attempt simple audio validation
    audioaccuracytest        more complex audio validation
    sdkdoc                   generate sdk documentation

    Examples:
    start-mycroft.sh all
    start-mycroft.sh cli
    start-mycroft.sh unittest


A noi praticamente ne servono solo tre:

$ ./start-mycroft.sh audiotest
    serve per verificare il funzionamento del servizio audio. Buono per la prima volta...
    Sostanzialmente è un test di registrazione della propria voce e di riascolto, per testare
    microfono e casse. Se funziona tutto si può andare avanti.

$ ./start-mycroft.sh debug
    Questa opzione esegue tutto quello che serve per Mycroft più lancia la console di debug per la
    verifica del funzionamento iniziale e interattivo (ovvero, durante utilizzo).
    Useremo sempre questa opzione finché non siamo sicuri al 100% che tutto sia ok e potremo lanciare 
    Mycroft *senza* interfaccia 

$ ./start-mycroft.sh all
    Come debug, ma senza l'interfaccia per il debug, in modo che possa essere utilizzato solo *dialogando*
    ma senza interagire fisicamente con il terminale
    

Per fermare tutto abbiamo bisogno del secondo script: **stop-mycroft.sh**. Questo script non presenta alcuna opzione particolare: 
controlla tutti i servizi Mycroft e li ferma nel giusto ordine. Richiede una decina di secondi per essere eseguito:

.. code-block:: bash

    $ ./stop-mycroft.sh


Pairing Mycroft
===============

Il Pairing è il processo di sincronizzazione dell'intelligenza artificiale appena installata con una interfaccia web, che le permette una interazione
con un sito esterno da cui caricare impostazioni, scaricare skills, etc...

.. note::
    L'applicazione web con cui si fa la sincronizzazione si chiama **selene** (https://github.com/MycroftAI/selene-backend), 
    ma la sua installazione e configurazione va al di là del nostro corso.
    Per i nostri scopi utilizzeremo l'installazione ufficiale di Mycroft, disponibile al sito https://home.mycroft.ai.

Per effettuare il pairing, procedere con l'esecuzione di Mycroft e dei suoi servizi con in più l'opzione di debug:

.. code-block:: bash

    $ ./start-mycroft.sh debug

Il caricamento iniziale è abbastanza oneroso in termini di tempo, soprattutto durante la primissima esecuzione dove vengono scaricate tutte le skills dal repository Mycroft. Dopo un pò Mycroft dovrebbe parlare o comunque scrivere qualcosa del tipo:

``I am connected to the internet and need to be paired. Your 6-digit Registration Code is X1Y2Z3``

Dove le 6 cifre che ho scritto sono state scelte a caso. Quelle 6 cifre che il vostro device avrà scritto
o pronunciato però... saranno fondamentali per registrare Mycroft online e terminare la prima configurazione.

Accedete al sito https://home.mycroft.ai, registratevi e selezionate "Add a device" dove inserirete le 6 cifre selezionate dalla vostra installazione di Mycroft.
A quel punto nel sito ci sono poche e semplici opzioni da scegliere, tramite le quali terminare la prima parte di configurazione.

L'unica cosa che raccomando è quella di selezionare l'opzione **American Male** come voce :)

Una volta fatto il **pairing** è possibile iniziare ad utilizzare le skills di base.



Skills di base
===============

Le skills predefinite installate con Mycroft sono quelle che ho elencato qui sotto. 

Dedicate una decina di minuti a testarle tutte per verificarne il funzionamento. Se ci sono problemi con la "comprensione" fra voi e Mycroft (ovviamente per colpa del microfono, non del vostro inglese) provate a digitare le domande nell'interfaccia di debug.

Le skills preinstallate su Mycroft sono:

Alarms
    Hey Mycroft, set an alarm for two hours Hey Mycroft, set an alarm for 3pm

Audio record
    Hey Mycroft, record

Configuration
    Hey Mycroft, configuration update

DuckDuckGo
    Hey Mycroft, what is Frankenstein? Hey Mycroft, who is Kathryn Johnson?

Hello World
    Hey Mycroft, how are you?

IP address
    Hey Mycroft, what is your IP address?

Jokes
    Hey Mycroft, tell me a joke!

Naptime
    Hey Mycroft, go to sleep

News from NPR
    Hey Mycroft, news
    
Pairing
    Hey Mycroft, pair my Device

Personal
    Hey Mycroft, what are you

Reminders
    Hey Mycroft, remind me to turn off the oven in 5 minutes

Support information
    Create a support ticket You're not working! Send me debug info

Version checker
    Hey Mycroft, check version

Volume
    Hey Mycroft, increase volume Hey Mycroft, decrease volume

Weather
    Hey Mycroft, what is the weather?

Wikipedia
    Hey Mycroft, tell me about artificial intelligence Hey Mycroft, tell me about Grace Hopper

