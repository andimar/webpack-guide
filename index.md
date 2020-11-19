# WebPack primi vagiti

Il modo migliore di capire una cosa è cercare di spiegarla, o di immaginare di farlo. Ho cercato alcune fonti per **capire Webpack da zero**  e ho trovato una **definizione** che mi piace e la riporto un po' rimaneggiata.

> Webpack è ciò che è noto come **"module bundler"**. La sua responsabilità? Comporre  pacchetti. 

 - INPUT:  **moduli JavaScript**, comprende le loro dipendenze e li concatena nel modo più efficiente possibile. 
 
- OUTPUT:  **un singolo file JS**.

Tutto qui. Certo ci sono altri oggetti che lo fanno, ma webpack ***può prendere qualunque cosa e considerarla un modulo JS*** da impacchettare . 

Usando ***Loaders***, Webpack capisce che un modulo JavaScript può richiedere un file CSS e che il file CSS potrebbe richiedere un'immagine. 
Le risorse emesse conterranno solo esattamente ciò che è necessario con il  "minimo sforzo". 

## Primo esempio per capire

Per sviluppare un primo esempio apriamo la console e iniziamo installando webpack con: 

    $ npm install webpack -g

se lanciamo 

    $ webpack

vediamo che il bundler cercherà qualcosa la cartella `./src`
&Egrave; una convenzione! Come sempre possiamo creare un progetto e una struttura convenzionale di cartella. 

Anzitutto quindi  creiamo un progetto npm

    $ npm init -y

poi installiamo i pacchetti base (`webpack` e `webpack-cli`)

    $ npm install webpack webpack-cli --save-dev
    
Infine creiamo una semplice struttura nella cartella del nostro progetto

    esercizio
     |- package.json
     |- index.html
     |- /src
       |- main.js
	 
In pratica possiamo aggiungere il file `index.html` nella root e un file `main.js` nella cartella `src`, già che ci siamo inseriamo anche un altro file, un modulo per il nostro bundle e lo chiamiamo `./src/hello.js`, che prende in ingresso un nome e un elemento e aggiunge un saluto nel testo dell'elemento:

    // hello.js
    module.exports = function (name, element) {
	    element.textContent = 'Hello ' + name + '!';
	};

Quindi in `main.js` possiamo utilizzare il nostro modulo:

    // main.js
    var sayHello = require ('./hello'); 
    sayHello('Guybrush', document.querySelector ('h2'));

Già ci sentiamo dei supereroi del bundle. ma cosa manca?
**Lanciamo webpack!**  Da riga di comando basterà scrivere 

    $ webpack ./src/main.js

Sarà generata automaticamente una cartella `dist` con il nostro bundle `main.js`

Non ci resta che includere il nostro bundle in index.html

    <!-- index.html -->
    <!doctype html>
    <html>
    <body>
        <h2></h2>
        <script src="dist/main.js"></script>
    </body>
    </html>










