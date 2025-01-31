:css: style.css

.. title:: Octoprint Integration

----

:data-x: r2400

.. image:: images/octoprint.png
   :width: 300px

Octoprint Integration
=====================

Der Druckserver im Home Assistant

Markus Pöschl

----

.. image:: images/tldr.jpg

Agenda
------

* Was ist Octoprint?
* Was kann die Integration in Home Assistant?

----

.. image:: images/dieter.jpg

Octoprint
---------

* Druckserver zur Steuerung von 3D Druckern
* Linux/Windows/Mac
* entwickelt seit 2012 von Gina Häußge (@fossel)
* Open-Source Software mit Donation

https://octoprint.org

----

.. image:: images/dieter.jpg

Octoprint Aufbau
----------------

* Oftmals auf Raspberry Pi installiert (OctoPi)
* Verbindung zum Drucker via USB
* Befehle über eine serielle Schnittstelle

----

.. image:: images/octoprint-default.png

Octoprint Standardfunktionen
----------------------------

* Monitoring und Steuerung beliebiger Drucker
* Weboberfläche
* Webcam Monitoring
* Dateien hochladen (Host + SD Karte)
* Grundlegende Zeitrafferaufnahmen
* Plugin-Mechanismus

----

.. image:: images/octoprint-custom.png

Octoprint Plugins
-----------------

* Responsive Design/Theme
* Filament Manager
* Druckteil History
* System Monitor
* Firmware Backup
* ...

----

Home Assistant Konfiguration (yaml)
-----------------------------------

* Nur über Yaml konfigurierbar

.. code-block:: yaml

  octoprint:
    host: '!secret octopi_host'
    api_key: '!secret octoprint_api_key'
    name: Hypercube Evolution
    bed: true
    number_of_tools: 1
    sensors:
      monitored_conditions:
        - 'Current State'
        - 'Job Percentage'
        - 'Time Remaining'
        - 'Temperatures'

  camera:
    - platform: mjpeg
      name: Hypercube Evolution Cam
      still_image_url: !secret octoprint_snapshot_url
      mjpeg_url: !secret octoprint_webcam_url

----

.. image:: images/integration-sensoren.png

Home Assistant Integration
--------------------------

* Monitoring von Temperaturen
* Monitoring Druckerzustand
* Druckfortschritt
* Weitere binäre Sensoren möglich

----

.. image:: https://img.memecdn.com/useless-invention_o_152430.webp
   :width: 400px

Fazit
-----

* Grundsätzliches Monitoring
* Webcam Stream

Zukunftsmusik
-------------

* Konfiguration über die Oberfläche
* Mehr Druckjob Informationen
* Drucker auch steuern
