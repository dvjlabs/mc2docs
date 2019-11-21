======
OpenCV
======

Liberamente ispirandomi a Wikipedia, posso dirvi che OpenCV (acronimo in lingua inglese di Open Source Computer Vision Library) 
è una libreria software multipiattaforma nell'ambito della visione artificiale in tempo reale.

È una libreria software libera originariamente sviluppato da Intel e poi presa in carico dalla comunità opensource. Il linguaggio di programmazione principalmente utilizzato per sviluppare con questa libreria è il C++, ma è possibile interfacciarsi ad essa anche attraverso il C, il Python e Java.


Installazione su RPI3 (Raspbian Buster)
=======================================

L'installazione della libreria su Raspbian Buster è notevolmente semplificata dalla presenza di alcuni pacchetti precompilati 
nei repository. 

L'installazione descritta di seguito è relativo alla versione 3.4.x nonostante sia già disponibile, anche su 
Raspbian, la versione 4.1.x. Purtroppo nei nostri test di laboratorio abbiamo avuto qualche problemino con essa...

Procedete come di seguito. Ricordate inoltre che qualsiasi operazione di installazione del sistema inizia con l'aggiornamento dello stesso...

.. code-block:: bash

    $ sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
    $ sudo apt install libxvidcore-dev libx264-dev
    $ sudo apt install libjpeg-dev libtiff5-dev libjasper-dev libpng-dev
    $ sudo apt install libhdf5-dev libhdf5-serial-dev libhdf5-103
    $ sudo apt install libatlas-base-dev gfortran
    $ sudo apt install libfontconfig1-dev libcairo2-dev
    $ sudo apt install libgdk-pixbuf2.0-dev libpango1.0-dev
    $ sudo apt install libgtk2.0-dev libgtk-3-dev
    $ sudo apt install libqtgui4 libqtwebkit4 libqt4-test python3-pyqt5
    $ sudo apt install python3-dev

Poi, finalmente...

.. code-block:: bash
    
    $ sudo pip3 install opencv-contrib-python==3.4.3.18


TEST
====

.. $ LD_PRELOAD=/usr/lib/arm-linux-gnueabihf/libatomic.so.1 python3

Al termine dell'installazione si può procedere con il primo test di funzionamento, che verifica semplicemente se l'installazione è andata a buon fine.
Il test prova semplicemente a caricare il modulo ``cv2`` all'interno dell'interprete ``python3``.

.. code-block:: bash
    
    $ python3
    Python 3.7.3 (default, Apr  3 2019, 05:39:12) 
    [GCC 8.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import cv2
    >>>
