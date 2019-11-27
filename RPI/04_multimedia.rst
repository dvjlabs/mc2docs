==========
Multimedia
==========

Quello che si vuole intendere in questa sezione come *Multimedia* è la possibilità di utilizzare con 
il nostro Raspberry alcune periferiche che poi torneranno utili nell'utilizzo dell'Intelligenza Artificiale.

Queste periferiche nello specifico sono:

* Una Webcam USB (utile per il riconoscimento facciale)

* Un microfono (per parlare, nella nostra dotazione è integrato nella webcam)

* le casse audio (per ascoltare musica e...la AI che parla!!!)

Queste funzionalità multimediali si appoggiano su alcuni software che, per motivi di spazio, non sono compresi nell'installazione iniziale del Raspberry. Procediamo dunque ad un aggiornamento del sistema e ad
una installazione degli stessi. Dal terminale, digitiamo:

.. code-block:: bash

    $ sudo apt update
    $ sudo apt upgrade
    $ sudo apt install pulseaudio pavucontrol
    
Alla fine di questo procedimento occorre riavviare il sistema. Ecco il motivo per cui abbiamo pensato di procedere subito all'installazione del software :)


Webcam
======

.. warning:: 
    Per poter utilizzare la webcam (ovvero accedere al file della periferica che la rappresenta) bisogna far parte del gruppo **video**. L'utente *pi* è automaticamente parte di questo gruppo. Se vuoi verificare digita:

    .. code-block:: bash

        $ groups
        
    Verranno elencati i gruppi di cui l'utente corrente fa parte. Se per qualche motivo *video* non fosse fra questi, bisogna aggiungere il proprio utente al gruppo con il comando:
    
    .. code-block:: bash

        $ sudo usermod -a -G video NOMEUTENTE


Per poter utilizzare la webcam, basta collegarla al Raspberry e installare il software necessario al suo utilizzo:

.. code-block:: bash

    $ sudo apt install fswebcam

Questione di 1 minuto...

Per fare una prima prova e farsi una foto con la webcam, basta digitare:

.. code-block:: bash

    $ fswebcam prova.jpg
    
Sorridete, poi aprite il file manager, andate a guardare la foto e controllate il risultato :)

.. image:: images/fswebcam_image.jpg
    :alt: Foto scattata con fswebcam


Per modificare la risoluzione, si può agire con il parametro **-r**. Basta non esagerare. Ad esempio:

.. code-block:: bash

    $ fswebcam -r 800x600 prova2.jpg

Se non vi piace la barra sotto (il *banner*), basta eliminarlo con l'opzione *--no-banner*

.. code-block:: bash

    $ fswebcam -r 800x600 --no-banner prova3.jpg

Il risultato:

.. image:: images/fswebcam_image_no_banner.jpg
    :alt: Foto scattata con fswebcam
    
Più o meno tutto qui!


Casse audio
===========

Queste sono davvero semplici da provare! Collegate le casse al Raspberry (jack e USB per l'alimentazione)
e provate a sentire un video di Youtube!
Se non funziona, forse il problema è che la periferica collegata al jack non è stata riconosciuta.
Per assicurarci della cosa, proviamo con:

.. code-block:: bash

    $ sudo raspi-config
    
    Advanced Options ---> Audio ---> Jack

E questo è tutto!


Microfono integrato
===================

Una volta positivamente testate le casse, si potrà provare anche con il microfono: basterà registrare 
qualche secondo di conversazione e poi provare a riascoltarla!

Per fare ciò, procediamo con le utility installate tramite pulseaudio. Per registrare:

.. code-block:: bash

    $ parecord prova.wav
    
Dite una frase tipo "che bello questo corso!!!", aspettate un paio di secondi e poi premete la combinazione
di tasti **CTRL + C** per interrompere la registrazione.

Per riascoltare le nostre soavi parole, digitate un bel:

.. code-block:: bash

    $ paplay prova.wav

E anche questa è fatta!!!


