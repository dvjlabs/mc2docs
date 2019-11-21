=============
Installazione
=============

.. tip::
    Prima di procedere, assicuriamoci che il sistema operativo sia aggiornatissimo e pronto per le operazioni.
    Procediamo con un bel:
    
    .. code-block:: bash

        $ sudo apt update
        $ sudo apt upgrade
    
    In caso di reale aggiornamento, sempre per la maggior sicurezza, procediamo ad un riavvio.

    
Per installare Mycroft sul Raspberry, procediamo con i seguenti comandi nel terminale:

.. code-block:: bash

    $ cd
    $ git clone https://github.com/MycroftAI/mycroft-core.git
    $ cd mycroft-core
    $ bash dev_setup.sh

L'operazione "collettiva" che si va ad eseguire con il comando *dev_setup.sh* installa tutte le dipendenze del Raspberry, configura il sistema e prepara Mycroft
all'esecuzione.

Ci vengono all'inizio proposte una serie di domande sull'installazione. Potete rispondere Sì a tutte, **tranne che a quelle sull'aggiornamento automatico e sulla compilazione di Mimic**: se abilitiamo l'aggiornamento automatico, ogni giovedì perdiamo 10 minuti. Se compiliamo Mimic, l'installazione durerà quasi 2 ore; senza Mimic ce la caviamo in 20 minuti...

.. note::
    Da quello che vedo, nel Raspberry è già installato di default il software **git** che viene utilizzato per scaricare il codice Mycroft.
    Nel caso il secondo comando fallisca per l'assenza di git, basta sistemare il tutto con un bel
    
    .. code-block:: bash

        $ sudo apt install git

L'installazione è tutta qui :)

