=================
Personalizzazioni
=================



mycroft.conf
============

La configurazione di Mycroft è memorizzata nel file **mycroft.conf**. In realtà i file di configurazione sono 4 e vengono applicati a cascata.

I livelli di configurazione sono:

#. **DEFAULT**: sono le impostazioni predefinite. Si trovano nella cartella mycroft-core, percorso ``mycroft/configuration/mycroft.conf``

#. **REMOTE**: sono le impostazioni scaricate dal sito home.mycroft.ai o comunque dall'installazione con sui si é fatto il pairing.

#. **SYSTEM**: sono le impostazioni del dispositivo; si trovano nel file ``/etc/mycroft/mycroft.conf``

#. **USER**: sono le impostazioni dell'utente locale (l'utente pi su Raspberry) e si trovano nel file ``$HOME/.mycroft/mycroft.conf``


Come vedete sono praticamente 4 file mycroft.conf. Come funziona dunque? Come dicevo le impostazioni vengono applicate a cascata a partire dal primo file.

Proviamo a spiegare con un esempio: tra le impostazioni di DEFAULT troviamo il fuso orario "America\New York" che viene dunque inizialmente applicato.
Sul sito home.mycroft.ai non vengono impostate informazioni sul fuso orario, in modo tale che rimangono attive le impostazioni di default. A livello di sistema
viene impostato il fuso orario "Italy\Rome" che sovrascrive quello precedente, collocando correttamente il dispositivo. Se ci fossero nuove impostazioni nel 
file utente, queste andrebbero a sovrascrivere quelle impostate precedentemente.

Sostanzialmente se si ha a che fare con un Raspberry, le impostazioni da controllare (per rendere le cose più facili) sono solo 2: quelle sul sito **home.mycroft.ai**
e quelle nel file utente, ricordandosi che le ultime vincono su tutte! Il file di sistema è meglio non utilizzarlo, in modo da non rendere più complicate le impostazioni.

Il file ``mycroft.conf`` è un file JSON standard (https://it.wikipedia.org/wiki/JavaScript_Object_Notation). Il consiglio principale è quello di cercare di
mantenerlo il più breve possibile, in modo tale che sia più facile controllare le impostazioni.

Vi lascio un file di esempio con le impostazioni che può servire di impostare:

.. code-block:: json

    {
        // Language used for speech-to-text and text-to-speech.
        // NOTE: DO NOT CHANGE THIS!!
        "lang": "en-us",

        // Measurement units, either 'metric' or 'english'
        // Override: REMOTE
        "system_unit": "metric",

        // Time format, either 'half' (e.g. "11:37 pm") or 'full' (e.g. "23:37")
        // Override: REMOTE
        "time_format": "full",

        // Date format, either 'MDY' (e.g. "11-29-1978") or 'DMY' (e.g. "29-11-1978")
        // Override: REMOTE
        "date_format": "DMY",

        // Play a beep when system begins to listen?
        "confirm_listening": true,

        // Location where the system resides
        // Override: REMOTE
        "location": {
            "city": {
                "code": "Jesi",
                "name": "Jesi",
                "state": {
                    "code": "TM",
                    "name": "The Marches",
                    "country": {
                        "code": "IT",
                        "name": "Italy"
                    }
                }
            },
            // DA SISTEMARE
            "coordinate": {
                "latitude": 38.971669,
                "longitude": -95.23525
            },
            "timezone": {
                "code": "America/Chicago",
                "name": "Central Standard Time",
                "dstOffset": 3600000,
                "offset": -21600000
            }
        },

        // Speech to Text parameters
        // Override: REMOTE
        "stt": {
            // Engine.  Options: "mycroft", "google", "google_cloud", "wit", "ibm", "kaldi", "bing",
            //                   "houndify", "deepspeech_server", "govivace", "mycroft_deepspeech"
            "module": "mycroft"
        },

        // Text to Speech parameters
        // Override: REMOTE
        "tts": {
            // Engine.  Options: "mimic", "mimic2", "google", "marytts", "fatts", "espeak", "spdsay", "watson", "bing", "responsive_voice"
            "module": "mimic2",
        },

    }


A proposito... per testare "Mimic2", dall'interfaccia WEB, selezionare "American Male"!



Italianizzare Mycroft
=====================

Questa cosa che proviamo qui è altamente sperimentale e non siamo per niente sicuri che funzionerà... è una delle cose belle di questo corso :)

Per utilizzare Mycroft in un'altra lingua, cioè in Italiano, dobbiamo andare a modificare 6 impostazioni:

#. **le impostazioni del linguaggio** nel file mycroft.conf

#. la **Wake Word** per renderla adatta al proprio linguaggio

#. il motore **STT** (Speech To Text), scegliendone uno che supporti il proprio linguaggio

#. il motore **TTS** (Text To Speech), come sopra

#. le **Skills** che devono supportare il nuovo linguaggio

#. il supporto della lingua scelta nel modulo **Lingua Franca**


La cosa un pò più complicata è quella di personalizzare la wake word in maniera generica. L'attuale documentazione di fornisce questi
suggerimenti: https://mycroft-ai.gitbook.io/docs/using-mycroft-ai/customizations/mycroft-conf#changing-your-wake-word

Per quanto riguarda Skills e Lingua Franca, tutto dipende dal fatto che la lingua che desideriamo sia stata implementata oppure no. Per questi due aspetti,
nel caso dell'italiano, la risposta è sì!!

Le impostazioni del linguaggio e i motori STT e TTS possono essere modificati tramite il file di configurazione. Lascio qui sotto un esempio:


.. code-block:: json

    {
        "lang": "it-it",
        "stt": {
            "module": "mycroft",
            "mycroft": {
                "lang": "it-it"
            }
        },
        "tts": {
            "module": "google",
            "google": {
                "lang": "it"
            }
        }
    }

