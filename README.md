# :: mini-R :: a Wi-Fi controlled rover-robot based on ESP8266
**mini-R** è un _robot-rover_ controllato via Wi-Fi costruito attorno al kit [Adafruit Mini Robot Rover Chassis](https://www.adafruit.com/product/2939).
I codici completi per il controllo del robot e per l'interfaccia web sono disponibili nella [repository del progetto su GitHub](https://github.com/lucasguanci/esp8266/tree/main/esp8266-mini-r).

<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-08.jpg"/>
  <div class="caption">Il robot-rover mini-R.</div>
</figure>

Al centro del progetto si trova un [Adafruit ESP8266 Feather Huzzah]({{< ref "esp8266" >}}) impostato in [modalità soft-AP]({{< ref "esp8266/#soft-access-point-mode-ap-mode" >}}) e controllato tramite una web-app. Il driver dei motori è la scheda [Adafruit DC Motor + Stepper FeatherWing](https://www.adafruit.com/product/2927).

**mini-R** funziona senza collegamento a Internet: il robot crea la propria rete Wi-Fi attraverso la quale avviene il collegamento alla _web-app_ per controllarne i movimenti.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-09.png"/>
  <div class="caption">L'interfaccia per il controllo del robot-rover mini-R accessibile via browser all'indirizzo 192.168.4.1.</div>
</figure>

## Assemblaggio
### Motori e ruote
Per prima cosa vanno montati i due motori facendo attenzione a posizionarli verso l'interno dello chassis (vedi Figura.1). A questo punto avvitare le ruote posteriori ai montari e utilizzare quattro bulloni per posizionare la ruota centrale, avvitandoli dal basso (vedi Figura.1).
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-01.jpg"/>
  <div class="caption">Figura 1. Montare motori, ruote e ruota centrale.</div>
</figure>
### FeatherWing Doubler
Applicare due distanziatori in silicone sotto al _FeatherWing Doubler_ come in Figura.2.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-02.jpg"/>
  <div class="caption">Figura 2. FeatherWing Doubler.</div>
</figure>

Avvitare il FeatherWing Doubler allo chassis sfruttando un taglio diagonale esterno e un foro della base del robot, avvitando prima il bullone in alto a sinistra in Figura.3 facendolo scorrere verso il centro per facilitare l'avvitatura, poi quello in basso a destra posizionandolo nel foro predisposto (vedi Figura.3).
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-03.jpg"/>
  <div class="caption">Figura 3. Avvitare il FeatherWing Doubler allo chassis.</div>
</figure>
Visto dall'alto in posizione corretta il FeatherWing Doubler deve risultare posizionato come in Figura.4.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-04.jpg"/>
  <div class="caption">Figura 4. Il FeatherWing Doubler posizionato sullo chassis.</div>
</figure>
### ESP8266 e driver motori
Sul Feather doubler vanno posizionate le due schede, l'_Adafruit ESP8266 Feather Huzzah_ e l'_Adafruit DC Motor_, il primo sulla destra e il secondo sulla sinistra, come in Figura.5, facendo attenzione all'orientazione dei connettori.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-05.jpg"/>
  <div class="caption">Figura 5. ESP8266 Feather Huzzah e DC Motor + Stepper FeatherWing posizionati sul Feather doubler.</div>
</figure>
Connettere il portabatterie da quattro batterie stilo da 1.5V al driver dei motori facendo attenzione alla polarità (cavo rosso connesso al _+_ e cavo nero al _-_), vedi Figura.6.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-06.jpg"/>
  <div class="caption">Figura 6. Connettere il portabatterie al driver motori facendo attenzione alla polarità.</div>
</figure>
Connettere i motori al driver motori con attenzione alla polarità, il motore di sinistra va connesso ai connettori di sinistra e viceversa quello di destra.
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-07.jpg"/>
  <div class="caption">Figura 7. Connettere i motori al driver motori.</div>
</figure>
### Posizionare le batterie 
Avvitare i distanziali allo chassis e montare la piastra superiore come in Figura.8, fissare il portabatterie alla piastra con del nastro biadesivo e connettere la batteria al litio all'ESP8266
<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-08.jpg"/>
  <div class="caption">Figura 8. Il montaggio del robot-rover mini-R è completo.</div>
</figure>


## Controllare il robot-rover mini-R
Il rover ospita un server web che crea un'interfaccia per controllare i movimenti di **mini-R**.

<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-09.png"/>
  <div class="caption">L'interfaccia per il controllo del robot-rover mini-R accessibile via browser all'indirizzo 192.168.4.1.</div>
</figure>

La web-app è scritta in HTML5/CSSe si basa sulla [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API).
L'applicazione è scritta in _vanilla_-JavaScript in modo tale che il codice possa girare senza aver bisogno di librerie esterne che necessitino di connessione a Internet per essere scaricate: per controllare il robot basta collegarsi con un web browser all'indirizzo 192.168.4.1.
