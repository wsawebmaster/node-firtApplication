# Primeira Aplicação NodeJS utilizando Express e Nodemon

`npm init -y` - Inicia npm no projeto

`npm install --save express` - Instala o framework Express e suas dependências

Crie o arquivo `index_puro.js`

    const http = require('http');

    const hostname = '127.0.0.1';
    const port = 3000;


    const server = http.createServer((req, res) => {
      res.statusCode = 200;
      res.setHeader('Content-Type', 'text/plain');
      res.end('Servidor NodeJS ON');
    })

    server.listen(port,hostname, () => {
      console.log('Servidor Rodando');
    });

Crie o arquivo `index_express.js`

    const express = require('express');
    const app = express();
    const path = require('path');
    const router = express.Router();

    router.get('/', function(req, res) {
      res.sendFile(path.join(__dirname+'/index.html'));
    });

    router.get("/sobre", function (req, res) {
      res.sendFile(path.join(__dirname + "/sobre.html"));
    });



    app.use('/',router);

    app.listen(process.env.port || 3000);

    console.log("Servidor NodeJS ON")

No exemplo acima temos uma rota principal e outra sobre, crie também os arquivos `index.html` e `sobre.html`

Para visualizar a aplicação em execução execute o comando `node index_express.js` e acesse a url `http://localhost:3000/`


`npm install -g nodemon` Instala o Nodemon de forma global

`nodemon index_express` para iniciar servidor usando nodemon
