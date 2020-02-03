# Lightstreamer - Race Telemetry Demo - HTML Client

<!-- START DESCRIPTION lightstreamer-example-racetelemetry-client-javascript -->

This project includes a simple web client front-end example for the [Lightstreamer - Race Telemetry Demo - Java Adapter](https://github.com/Lightstreamer/Lightstreamer-example-RaceTelemetry-adapter-java).

## Live Demo
[![screenshot](screen_telemetry_large.png)](http://demos.lightstreamer.com/WebTelemetryDemo)<br>
### [![](http://demos.lightstreamer.com/site/img/play.png) View live demo](http://demos.lightstreamer.com/WebTelemetryDemo)

## Details

The *Web-Telemetry Demo* uses the <b>JavaScript Client API for Lightstreamer</b> to show how Lightstreamer can be used to send real-time telemetry data through the Web.<br>
In this demo, the data is generated by a random feed simulator of the telemetry metrics of a racing car such as Lap Time, Distance, Speed, Engine RPM, Gear, and Laps. The data is displayed in tabular form using two tables, one for the current lap and the other to recap the history of the laps. In addition, two real-time streaming charts are shown, one for speed and one for engine RPM.<br>
Actual feed adapters were created to deliver real data.<br>

The demo includes the following client-side functionalities:
* A [Subscription](https://lightstreamer.com/api/ls-web-client/latest/Subscription.html) containing 1 item, subscribed to in <b>MERGE</b> mode, with some of the metrics pertaining to the car, feeding a [StaticGrid](https://lightstreamer.com/api/ls-web-client/latest/StaticGrid.html).
* A [Subscription](https://lightstreamer.com/api/ls-web-client/latest/Subscription.html) containing 1 item, subscribed to in <b>DISTINCT</b> mode, with the data for each lap feeding a [DynaGrid](https://lightstreamer.com/api/ls-web-client/latest/DynaGrid.html).
* A [Subscription](https://lightstreamer.com/api/ls-web-client/latest/Subscription.html) containing 1 item (the same of the first Subscription but at a lower frequency), subscribed to in <b>MERGE</b> mode feeding two [Chart](https://lightstreamer.com/api/ls-web-client/latest/Chart.html)s, used to plot the speed and the engine RPM.

<!-- END DESCRIPTION lightstreamer-example-racetelemetry-client-javascript -->

## Install

If you want to install a version of this demo pointing to your local Lightstreamer Server, follow these steps:

* Note that, as prerequisite, the [Lightstreamer - Race Telemetry Demo - Java Adapter](https://github.com/Lightstreamer/Lightstreamer-example-RaceTelemetry-adapter-java)  has to be deployed on your local Lightstreamer Server instance. Please check out that project and follow the installation instructions provided with it.
* Launch Lightstreamer Server.
* Get the `lightstreamer.min.js` file from [npm](https://www.npmjs.com/package/lightstreamer-client-web) or [unpkg](https://unpkg.com/lightstreamer-client-web/lightstreamer.min.js) and put it in the `src/js` folder of the demo.
  Alternatively, you can generate a customized lightstreamer.min.js library containing only the classes you actually use;
  see the build instructions on the [GitHub page](https://github.com/Lightstreamer/Lightstreamer-lib-client-javascript#building).
  In that case, be sure to include the LightstreamerClient, Subscription, DynaGrid, StaticGrid, Chart, SimpleChartListener, ConnectionSharing, and StatusWidget modules.
* Get the `require.js file` from [requirejs.org](http://requirejs.org/docs/download.html) and put it in the `src/js` folder of the demo.

You can deploy this demo to use the Lightstreamer server as Web server or in any external Web Server you are running. 
If you choose the former case, please create the folders `<LS_HOME>/pages/demos/RaceTelemetryDemo` then copy here the contents of the `/src` folder of this project.<br>
The client demo configuration assumes that Lightstreamer Server, Lightstreamer Adapters, and this client are launched on the local machine. If you need to target a different Lightstreamer server, please search this line:
```js
var lsClient = new LightstreamerClient(protocolToUse+"//localhost:8080","F1Telemetry");
```
in `js/lsClient.js` file and change it accordingly. For example, if you want to target the adapter deployed in our server, you should substitute with this:
```js
var lsClient = new LightstreamerClient(protocolToUse+"//push.lightstreamer.com","F1Telemetry");
```
<br>
The demo is now ready to be launched.

## See Also

### Lightstreamer Adapters Needed by This Demo Client

<!-- START RELATED_ENTRIES -->
* [Lightstreamer - Race Telemetry Demo - Java SE  Adapter](https://github.com/Lightstreamer/Lightstreamer-example-RaceTelemetry-adapter-java)
* [Lightstreamer - Reusable Metadata Adapters - Java Adapter](https://github.com/Lightstreamer/Lightstreamer-example-ReusableMetadata-adapter-java)

<!-- END RELATED_ENTRIES -->

### Related Projects

* [Lightstreamer - Stock-List Demos - HTML Clients](https://github.com/Lightstreamer/Lightstreamer-example-StockList-client-javascript)

## Lightstreamer Compatibility Notes

* Compatible with Lightstreamer JavaScript Client library version 6.0 or newer (installation instructions for version 8.0 or newer).
