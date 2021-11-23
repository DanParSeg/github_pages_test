
<!-- <!DOCTYPE html> -->
<html lang="es" dir="ltr">
  <head>
    <title>8 INPUTS - 8 OUTPUTS</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="icon" href="media/favicon.ico" type="image/ico"/>
    <link rel="shortcut icon" href="media/favicon.ico" type="image/x-icon"/>

    <!-- Hojas de estilo de los diferentes componentes -->
    <link rel="stylesheet" href="css/w3.css">
    <link rel="stylesheet" href="css/led.css">
    <link rel="stylesheet" href="css/switch.css">
    <link rel="stylesheet" href="css/pushbutton.css">
    <link rel="stylesheet" href="css/label-on-off.css">

    <!-- Código de los componentes -->
    <script src="js/SerialPanel.js"></script>
    <script src="js/led.js"></script>
    <script src="js/switch.js"></script>
    <script src="js/pushbutton.js"></script>
    <script src="panel.js" defer> </script>
  </head>

  <body>

    <!--  RECURSO: Audio del click del switch -->
    <audio id="click" src="media/click.mp3">
    </audio>

    <!-- Mensaje de error que se muestra si el navegador
         no tiene web-serial
     -->
    <div class="w3-panel w3-red w3-round-xlarge w3-border w3-margin-left w3-margin-right" id="msg_serial">
      <h3>Warning!</h3>
      <p>Este navegador NO soporta <b>Web Serial</b></p>
      <p>Asegúrate que estás usando
      Chrome/Chromium 78 o superior
        y que está habilitado el flag
      <code>#enable-experimental-web-platform-features</code> en
      <code>chrome://flags</code></p>
      <p>Para habilitarlo en Chrome/Chromium copia esta URL en una nueva pestaña:
      <a href="chrome://flags/#enable-experimental-web-platform-features">chrome://flags/#enable-experimental-web-platform-features</a>
      y pincha en ENABLE</p>
    </div>

    <!-- Panel de control LOVE -->
    <div class="w3-card-4 w3-margin w3-round-large">

      <header class="w3-container w3-grey w3-text-white">
        <h5>LOVE Controls</h5>
      </header>

      <!-- Botones de gestion del panel -->
      <div class="w3-container">
          <p>
          <button class="w3-button w3-pale-green w3-round-large" type="button" id="butSerial" disabled>🔌Connect</button>
          <button class="w3-button w3-yellow w3-round-large " id="butReset" disabled>↪ Reset</button>
          <button class="w3-bar-item w3-button w3-yellow w3-round-large " id="butSync" disabled>⤵ Sync</button>
          </p>
      </div>
    </div>

   <!-- ENTRADAS del circuito -->
   <div class="w3-card-4 w3-margin w3-round-large">
     <header class="w3-container w3-blue w3-text-white">
       <h5><b>INPUTS</b></h5>
     </header>

      <!-- Switches -->
      <div class="w3-container">
        <div class="w3-row">

          <!-- Grupo: Datos -->
          <div class="w3-col w3-center" style="width:280px">
            <p class="w3-margin-top w3-text-blue" style="margin:0px">Switches</p>
            <div class="w3-container">
              <div class="w3-row">

                <!-- Label on/off -->
                <div class="w3-col w3-center" style="width:30px">
                  <p class="w3-margin-top" style="margin:0px">&nbsp</p>
                  <div class="Label-on-off"></div>
                </div>

                <!-- First switch -->
                <div class="w3-col w3-center" style="width:54px">
                  <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                  <div class="Switch switch_disabled" id="swa"></div>
                </div>

                <!-- Second switch -->
                <div class="w3-col w3-center" style="width:54px">
                  <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                  <div class="Switch switch_disabled" id="swb"></div>
                </div>

                <!-- Third switch -->
                <div class="w3-col w3-center" style="width:54px">
                  <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                  <div class="Switch switch_disabled" id="swc"></div>
                </div>

                <!-- Fourth switch -->
                <div class="w3-col w3-center" style="width:54px">
                  <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                  <div class="Switch switch_disabled" id="swd"></div>
                </div>

              </div>
            </div>
          </div>

          <!-- Grupo: Pulsadores -->
          <div class="w3-col w3-center" style="width:220px">
            <p class="w3-margin-top w3-text-blue" style="margin:0px">Pushbuttons</p>

            <!-- First pushbuton -->
            <div class="w3-col w3-center" style="width:54px">
              <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
              <div class="Pushbutton pushbutton_disabled" id="pbe"></div>
            </div>

            <!-- Second pushbuton -->
            <div class="w3-col w3-center" style="width:54px">
              <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
              <div class="Pushbutton pushbutton_disabled" id="pbf"></div>
            </div>

            <!-- Third pushbuton -->
            <div class="w3-col w3-center" style="width:54px">
              <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
              <div class="Pushbutton pushbutton_disabled" id="pbg"></div>
            </div>

            <!-- Forth pushbuton -->
            <div class="w3-col w3-center" style="width:54px">
              <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
              <div class="Pushbutton pushbutton_disabled" id="pbh"></div>
            </div>

          </div>

          <div class="w3-rest"></div>
        </div>
       </div>

   </div>

   <!-- SALIDAS del circuito -->
   <div class="w3-card-4 w3-margin w3-round-large">
     <header class="w3-container w3-green w3-text-white">
       <h5><b>OUTPUTS</b></h5>
     </header>

    <!-- LEDs -->
     <div class="w3-container">
       <div class="w3-row">

        <!-- Grupo: Leds -->
        <div class="w3-col w3-center" style="width:480px">
          <p class="w3-margin-top w3-text-green" style="margin:0px">LEDs</p>
          <div class="w3-container">
            <div class="w3-row">
              hola
            </div>


            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="leda"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledb"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledc"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledd"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="lede"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledf"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledg"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledh"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledi"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledj"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledk"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledl"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledm"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledn"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledo"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledp"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledq"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledr"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="leds"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledt"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledu"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledv"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledw"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledx"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledA"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledB"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledC"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledD"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledE"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledF"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledG"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledH"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledI"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledJ"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledK"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledL"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledM"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledN"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledO"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledP"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledQ"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledR"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledS"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledT"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledU"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledV"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledW"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledX"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led0"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led1"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led2"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led3"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led4"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led5"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led6"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led7"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led8"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led9"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledy"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledz"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledY"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="ledZ"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led!"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led#"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led$"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led%"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led&"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led("></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led)"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led*"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led+"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led,"></div>
              </div>
            </div>

            <div class="w3-row">

              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led-"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led."></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led/"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led:"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led;"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led<"></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led="></div>
              </div>
              <div class="w3-col w3-center" style="width:54px">
                <p class="w3-margin-top" style="margin:0px"><b>-</b></p>
                <div class="Led led_disabled" id="led>"></div>
              </div>
            </div>

          </div>
        </div>

         <div class="w3-rest"></div>
       </div>
      </div>
   </div>
   
   <!-- Parte inferior: Enlaces (TODO: enlazar mis cosas)-->
   <div class="w3-container w3-margin-top">
    <a class="w3-btn w3-sand" href="https://github.com/DanParSeg/github_pages_test" target="_blank">Github</a>
    <a class="w3-btn w3-sand" href="https://github.com/DanParSeg/github_pages_test" target="_blank">DOC</a>
   </div>
  </body>
</html>
