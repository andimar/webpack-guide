Webpack

La definizione più utile che ho trovato su webpack è:

Webpack è ciò che è noto come "module bundler". 

Prende moduli JavaScript, comprende le loro dipendenze e li concatena nel modo più efficiente possibile. 
In uscita restituisce un singolo file JS.

Tutto qui. Cose come RequireJS lo fanno da anni. 

In più Con Webpack, i moduli non sono limitati ai file JavaScript. 

Usando *Loaders*, Webpack capisce che un modulo JavaScript può richiedere un file CSS e che il file CSS potrebbe richiedere un'immagine. 
Le risorse emesse conterranno solo esattamente ciò che è necessario con il  "minimo sforzo".


Sviluppiamo un primo esempio:

installiamo webpack con 

npm install webpack -g


se lanciamo 

webpack

vediamo che il bundler cercherà la cartella ./src

è una convenzione! Creiamola. Anzi creiamo un progetto npm

npm init -y

poi installiamo i pacchetti base (webpack e webpack-cli)

npm install webpack webpack-cli --save-dev

e inizializziamo  il nostro progetto proprio come un progetto webpack

webpack init

che ci chiede di installare un nuovo pacchetto init. 
Infine creiamo una semplice struttura nella cartella del nostro progetto

esercizio
 |- package.json
 |- index.html
 |- /src
   |- main.js
	 
in pratica possiamo aggiungere il file index.html nella root e un file main.js nella cartella src, già che ci siamo inseriamo anche un altro file, un modulo per il nostro bundle e lo chiamiamo ./src/hello.js, che prende in ingresso un nome e un elemento e aggiunge un saluto nel testo dell'elemento:

// hello.js
module.exports = function (name, element) { element.textContent = 'Hello' + name + '!'; };

Quindi in main.js possiamo utilizzare il nostro modulo:

// main.js
var sayHello = require ('./hello'); 
sayHello('Guybrush', document.querySelector ('h2'));

Già ci sentiamo dei supereroi del bundle. ma cosa manca?

da riga di comando basterà scrivere 
webpack ./src/main.js

sarà generata automaticamente una cartella dist con il nostro bundle main.js

includiamo il nostro bundle in index.html

<!-- index.html -->
<!doctype html>
<html>
<body>
    <h2></h2>
    <script src="dist/main.js"></script>
</body>
</html>








