# API-digitalisation-des-donnees-de-la-FTF

notre projet consiste a cree un API REST pour la gestion des statistiques des joueurs de l equipe nationnale de football

PRE-REQUIS

 -  savoir installer node js
 - savoir installer nvm Node Version Manager
 -savoir installer npm Node Package Manager 
 -savoir utiliser le framework Express

 INSTALLATION

 -cliquez sur le lien (https://nodejs.org/en/download/) choisir la bonne version node adapter a votre machine telecharger et intaller
 aller dans terminal taper (node --version)pour etre sur de l avoir installer et connaitre la version

 -installer npm : taper la commande (npm install download) pour installer npm (npm --version)pour connaitre la version


 DEMARAGE

 -creer votre dossier sur le bureau ,l ouvrir dans le terminal,(npm init) pour demarer l installation du package ,suivre les etapes en appuiyant (ENTER) a chaque fois
 -installation du framework EXPRESS:(npm install express body-parser morgan)
-creer un fichier index.js dans lequel on copie tout le code entre les guillaumets:
<
const express = require('express');
const bodyParser = require('body-parser');
const logger = require('morgan');
const path = require('path');
const app = express();

const PORT = process.env.PORT || 3000;
const NODE_ENV = process.env.NODE_ENV || 'development';

app.set('port', PORT);
app.set('env', NODE_ENV);

app.use(logger('tiny'));
app.use(bodyParser.json());

app.use('/', require(path.join(__dirname, 'routes')));

app.use((req, res, next) => {
  const err = new Error(`${req.method} ${req.url} Not Found`);
  err.status = 404;
  next(err);
});

app.use((err, req, res, next) => {
  console.error(err);
  res.status(err.status || 500);
  res.json({
    error: {
      message: err.message,
    },
  });
});

app.listen(PORT, () => {
  console.log(
    `Express Server started on Port ${app.get(
      'port'
    )} | Environment : ${app.get('env')}`
  );
});
}
>
-creer un dossier appeler ROUTES
-creer dans le dossier un fichier STATS.JSON
-un autre appelle STATS.JS
-ajouter le script entre les parentheses au fichier packages.json
 ("scripts": {
  "start": "node index.js"
},)
-executer la commande (npm start) dans le dossier
-on nous envera un message
(Express Server started on Port 3000 | Environment : development
)
-l API est pret a etre tester avec POSTMAN ou heberger sur HEROKU




