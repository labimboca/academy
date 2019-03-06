![alt text](https://uploaddeimagens.com.br/images/001/892/384/original/Labinboca_banner.jpg?1549978263)


# Labimboca's Academy

Sistema de teste para treinar os novos estagiários do LabTIC
  
  ## O que será o sistema?
  Você irá desenvolver, com a ajuda do tio Osvaldo, lembre-se disso, só o <b>Osvaldo</b> pode te ajudar, mais ninguém no lab é tão capacitado quanto este exímio ser humano(?).
  O desafio consiste em construir uma aplicação web em <s>typescript</s> Javascripto aprendendo a mexer com algumas tecnologias que são utilizadas nos nossos sistemas do Lab.
  
  ###### [AVENTUREIROS](https://youtu.be/o2RY6MP_jsU?t=10)
  
  #### Ao concluir o desafio você estará capacitado a:
  
  - [ ] Desenvolver app's
  - [x] <b><s>Xingar a mãe do Osvaldo</s></b>
  - [x] MongoDB
  - [x] Configurar um Server
  - [ ] Utilizar a <s>belíssima</s> Base de projetos
  - [x] Requisições HTTP
  - [x] VueJS
  - [x] Ter Mais Conhecimento que o Pedro
  - [ ] Sobreviver na Palhoça
  - [x] [surviv.io](http://surviv.io/)
  - [x] [abrir esse link](https://www.youtube.com/watch?v=xGgwGXjraCg)
  - [x] jogar DBZ
 
  #### Antes de concluir o desafio, ou qualquer coisa da sua vida você estará capacitado a:
  - [x] Ter Mais Conhecimento que o Pedro
 
 ##### Documentação de apoio
 Aqui estão as suas [documentações](https://drive.google.com/drive/folders/1rwoTRKnkKnHqaYHwxQ51ON82uzRy-QVO) necessárias que auxiliam na realização do projeto.
 
 
  ## Sumário
  
  * [Backend](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#iniciando-o-backend)
  * [Sistema](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#o-sistema)
  * [Model](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#model)
  * [Rotas](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#rotas)
  * [Testando Requisições](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#testando-as-requisi%C3%A7%C3%B5es)
  * [Frontend](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#iniciando-o-frontend)
  * [Componentes](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#criando-os-componentes)
  * [Rotas](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#adicionando-as-rotas-no-index)
  * [Dicas](https://github.com/lucaslovato/labimbocaAcademy/blob/master/README.md#dica-do-dia)

  
  # Configuração do Ambiente:
  
  Instale os principais programas
    
  + [Webstorm](https://www.jetbrains.com/webstorm/)
  + [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) e [Tortoise](https://tortoisegit.org/)
  + [MongDB](https://docs.mongodb.com/manual/administration/install-community/) e [roboMongo](https://robomongo.org/)
  + [NVM](https://github.com/creationix/nvm)
  + [Postman](https://www.getpostman.com/)
  + [VueJS](https://vuejs.org) e [Vue-CLI](https://cli.vuejs.org/)
  
  
  ## Iniciando Projeto:
  Criar uma pasta com o nome do desafio, também criar no bitbucket o repositório do projeto e um gitignore, após isso abir a pasta no Webstorm e então no terminal digitar o comando
            
    vue init webpack onomequevocequiserprosistemapqeunaomeimporto 
    
  Configurar o webpack... Esse comando baixará um template básico de vue que será a base do front do nosso projeto<br>
  Pra que serve o vue init webpack? [documentação](https://www.npmjs.com/package/vue-cli)
  
  Digite no terminal
  
    npm install
    
  Depois de entender o vue init webpack vamos testar se está tudo em ordem.
  Entre na pasta do projeto e digite no terminal
  
    npm run dev
    
  Abra o endereço http:localhost:8080 e veja o template rodando.
  
  Se não rodar chame o Bruno pra te ajudar, ele é um dos melhores na explicação e clareza na fala, também pode perguntar o motivo de ele apanhar tanto pro Breza no dbz.
  
  
  Agora você deve instalar as dependências que irá utilizar no projeto.
   
    npm install --save express body-parser mongoose nodemon ts-node morgan serve-favicon bluebird axios
    
   Leia sobre [express](https://expressjs.com/pt-br/) e [mongoose](https://mongoosejs.com/), são tecnologias que vão te ajudar a entender alguma coisa. Com isso você poderá contar para alguém que aprendeu alguma coisa no estágio. Lembre-se de sempre que surgir alguma dúvida pergunte <s>para qualquer um do lab</s> <b>para o Osvaldo!</b>
  

   
  # Iniciando o Backend!
  
   Agora vamos criar uma pasta chamada bin e nela um arquivo chamado www na raiz da pasta do projeto Vue.js
   
    mkdir bin
    touch bin/www
   
   Abra e edite o arquivo www com as seguintes linhas de código. Aqui nesse arquivo que a magia ta acontecendo!
 
 ```javascript 
    #!/usr/bin/env node

    /**
     * Module dependencies.
     */

    let app = require('../app');
    let debug = require('debug')('mean-app:server');
    let http = require('http');

    /**
     * Get port from environment and store in Express.
     */

    let port = normalizePort(process.env.PORT || '3000');
    app.set('port', port);

    /**
     * Create HTTP server.
     */

    let server = http.createServer(app);

    /**
     * Listen on provided port, on all network interfaces.
     */

    server.listen(port);
    server.on('error', onError);
    server.on('listening', onListening);

    /**
     * Normalize a port into a number, string, or false.
     */

    function normalizePort(val) {
      let port = parseInt(val, 10);

      if (isNaN(port)) {
        // named pipe
        return val;
      }

      if (port >= 0) {
        // port number
        return port;
      }

      return false;
    }

    /**
     * Event listener for HTTP server "error" event.
     */

    function onError(error) {
      if (error.syscall !== 'listen') {
        throw error;
      }

      let bind = typeof port === 'string'
        ? 'Pipe ' + port
        : 'Port ' + port;

      // handle specific listen errors with friendly messages
      switch (error.code) {
        case 'EACCES':
          console.error(bind + ' requires elevated privileges');
          process.exit(1);
          break;
        case 'EADDRINUSE':
          console.error(bind + ' is already in use');
          process.exit(1);
          break;
        default:
          throw error;
      }
    }

    /**
     * Event listener for HTTP server "listening" event.
     */

    function onListening() {
      let addr = server.address();
      let bind = typeof addr === 'string'
        ? 'pipe ' + addr
        : 'port ' + addr.port;
      debug('Listening on ' + bind);
    }
   ```
    
  Editar o arquivo package.json para que a parte de script fique assim:

```
    "scripts": {
      "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
      "start": "npm run build && node ./bin/www",
      "unit": "cross-env BABEL_ENV=test karma start test/unit/karma.conf.js --single-run",
      "e2e": "node test/e2e/runner.js",
      "test": "npm run unit && npm run e2e",
      "build": "node build/build.js"
     }
 ```
     
   Agora vamos criar o arquivo principal chamado app.js
   
    touch app.js
   
   Vamos editar esse arquivo adicionando as seguintes linhas de código:

```javascript   
    let express = require('express');
    let path = require('path');
    let favicon = require('serve-favicon');
    let logger = require('morgan');
    let bodyParser = require('body-parser');

    let pokemon = require('./routes/pokemon');
    let app = express();

    app.use(logger('dev'));
    app.use(bodyParser.json());
    app.use(bodyParser.urlencoded({'extended':'false'}));
    app.use(express.static(path.join(__dirname, 'dist')));
    app.use('/pokemons', express.static(path.join(__dirname, 'dist')));
    app.use('/pokemon', pokemon);

    // catch 404 and forward to error handler
    app.use(function(req, res, next) {
      let err = new Error('Not Found');
      err.status = 404;
      next(err);
    });

    // error handler
    app.use(function(err, req, res, next) {
      // set locals, only providing error in development
      res.locals.message = err.message;
      res.locals.error = req.app.get('env') === 'development' ? err : {};

      // render the error page
      res.status(err.status || 500);
      res.render('error');
    });
    
    app.set('view engine', 'html');
    
    module.exports = app;    
```

  O arquivo app terá a configuração do nosso sitema inteiro, e no server o express irá botar o ambiente 'no ar'. Procure sobre
  'use' no use procure bodyParser.json e bodyParser.urlencoded, 'listen' do express
  
  Agora a nossa rota principal será criada com o comando
  
    mkdir routes
    touch routes/pokemon.js
   
   ## O Sistema
    
 O que pokémon?? sim meu caro, você irá fazer uma pokédex com os mais diferentes animais desse mundinho fantástico, e fica a dica se você por o <b>Osvaldo</b> como um pokémon do tipo BUG você ganha 10 pontos no projeto!
   Dentro do arquivo pokemon.js nós iremos fazer nossa primeira requisição http, sim aquela que vamos contar pros amigos com orgulho, então bora digitar o código dentro do arqui[v](https://github.com/labimboca/academy#um-agradecimento-dos-estagi%C3%A1ros-do-lab-e)o
   
```javascript  
    let express = require('express');
    let router = express.Router();

    /* GET home page. */
    router.get('/', function(req, res, next) {
      res.send('Express PokeRESTful API TEST');
    });

    module.exports = router;
 ```
 
  Agora é possível testar nosso projeta1 com o comando
      
      npm start
      
   Vá lá na url http://localhost:3000 que está o projeto rodando e passe o path /pokemon no final para ver a mensagem que      está sendo enviada 'Express PokeRESTful API TEST'. ISSO AI MEU CARO PARABÉNS!!!<br>
   
   
   Continuando essa caralha que eu já to cansado...<br>
   Vamos agora começar a mexer com banco de dados, aqui no lab utilizamos o mongodb que você já era pra ter instalado no pc, se não instalou volta saporra pro começo e faz o passo a passo direito.
   No arquivo app.js que é o principal da nossa aplicação vamos adicionar a seguinte linha de código
   
```javascript
    let mongoose = require('mongoose');
    mongoose.Promise = require('bluebird');
    mongoose.connect('mongodb://localhost/pokedexDB', { useMongoClient: true, promiseLibrary: require('bluebird') })
    .then(() =>  console.log('connection succesful'))
    .catch((err) => console.error(err));
```
   
   Agora veja se quando o server for inciado novamente a mensagem de 'connection succesful' foi exibida no console.<br>
   Se houver algum erro de problema na conexão é provável que o mongo não esteja rodando, então digite:
   
      sudo service mongod start
   
   Deu boa? bora continuar, agora vamos criar o model, o que é ? o model é basicamente a estrutura dos dados que vamos armazenar no banco, no nosso caso vai ser tudo que queremos de cada pokemon.
      
      mkdir models
      touch models/PokemonModel.js
 
  ### Model
  
  No arquivo que vamos editar agora será posto tudo de dado que precisamos para que o pokémon fique perfeitamente catalogado no nosso banco, ou seja, precisamos dos atributos, veja ele nas suas documentações!
   
   * Name - String
   * Order - Number
   * Type - [String]
   * Evolution - ObjectId - Referencia outro pokémon!
   * Weakness- [String]
   
 E como fazer? se vira bro [mongodb](https://docs.mongodb.com/manual/core/data-modeling-introduction/)
 Qualquer dúvida que tiver sobre essa parte pode perguntar sem medo qualquer coisa relacionada ao projeto ou qualquer coisa para o Osvaldo, ele está a disposição para tirar dúvidas full-time, ps: se você leu até aqui pergunte para o Osvaldo sobre a Márcia, grande mulher por sinal...

 HEHE brinks, vou te ajudar a criar o model. No arquivo pokemonModel.js vamos começar
 
 ```javascript
 
     let mongoose = require('mongoose');
     
     const Schema = mongoose.Schema;
     
     const PokemonSchema = new Schema({
     
     });
     module.exports = mongoose.model('pokemon', PokemonSchema);
 
 ```
  
  Como eu sou um belo parça vou te passar um exemplo de um model antigo que eu fiz, pra te ajudar como base, lembre-se que esse é pra outra coisa completamente diferente, mas tem umas dicas aí de como fazer pra sua aplicação, prestenção bro!
  
```javascript

    const CategoriesSchema = new Schema({
      name: {
        type: Schema.Types.String,
        required: 'Name is required'
      },
      childrenIds: {
        type: [{
                type: Schema.Types.ObjectId,
                ref: "category",
            }],
      }
    });

```  

  Quando terminar chame o Osvaldo para ele corrigir, fique tranquilo que se você errar você está demitido instantaneamente, mas sem pressão, <b>glhf</b>.
 
  
  ### Rotas
  
 Para que as nossas rotas peguem os dados do banco de dados e consigam criar, ler, atualizar ou deletar pokemons vamos adicionar no routes/pokemon.js essas duas linas:
 
 ```javascript
    let mongoose = require('mongoose');
    let Pokemon = require('../models/PokemonModel');
```
    
 A dica prévia aqui é olhar o nosso GET exemplo que já temos nesse arquivo e perceber que com Pokemon.<b>AlgumaFuncaoDoMongoose()</b> conseguiremos mexer no Banco.   
 
 Agora precisamos dar um passo importante nas Requisições HTTP, preciso que você faça pra mim 5, cinco, cinque, five, cinq, fünf, пять, 五, REQUISIÇÕES REST, lembre-se de que no nosso arquivo pokemon.js na pasta routes temos um exemplo de GET.
 Pode fazer naquele arquivo mesmo então vamos lá, lembre-se de seguir o diagrama de caso de uso e marcar o que está fazendo, o que já fez e por aí vai.
  
  * GET ALL POKEMON - dica procure o .find() no mongoose e envie a resposta como res.json(pokemon)
  * GET POKEMON BY ID - dica a rota pode ser a mesma do get anterior, porém dessa vez use /:id, pegue esse id com req.params, e procure o .findById() no mongoose e envie a resposta como res.json(pokemon)
  * ADD NEW POKEMON - Método POST - dica procure o .create() no mongoose, os dados são enviados em req.body, e envie a resposta como res.json(newPokemon)
  * UPDATE POKEMON - Método PUT - também envolve o '/:id' - dica procure o .findByIdAndUpdate() no mongoose e envie a resposta como res.json(pokemons)
  * DELETE POKEMON - Método DELETE - mais uma vez precisa do '/:id' - - dica procure o .findByIdAndRemove() no mongoose e envie a resposta como res.json(pokemons)
  
  Repara que quando o método é diferente ele pode ter 'a mesma rota' manjou? localhost:8080/pokemon pode servir para várias requisições.
  
  ### Testando as Requisições
  
  Feito isso, bora testar as funcionalidades no postman, teoricamente ele é intuitivo, mas vamos explicar como fazer saporra acontecer, lembrando que para testar o servidor deve estar rodando (npm start).<br>
  
 ##### O que é o postman?
 Basicamente é uma ferramente que testa as nossas requisicoes http restful, ou seja, web api’s, também conseguimos ver o que estamos mandando de dado de volta, então bora lá, da pra ver (e ta escrito) o lugar que você precisa botar a request e do lado esquerdo disso tem o ‘tipo’ da requisição que irá ser testada, no caso do nosso sitema temos GET, POST, PUT, DELETE, então botaremos ali o http://127.0.0.1:3000/pokemon então primeiro de tudo vamos começar com o post para popular o banco, os dados vao em body e x-www-form-urlencoded voce precisa mandar o que é obrigatório lá do model, a dica aqui é que se for um array voce manda a mesma key em diferentes linhas e cada value um valor do que você quer postar. 
 
Como explicação, quando você envia os dados no body da requisição o backend recebe um objeto e então mandamos esse objeto pro banco na função create e o mongodb faz a mágica! Depois de fazer esse POST teste o GET e veja se está voltando certinho o objeto que acabou de ser cri[a](https://github.com/labimboca/academy#um-agradecimento-dos-estagi%C3%A1ros-do-lab-e)do, caso de um erro tente entender esse erro e criar o pokemon novo do jeito certo, uma dica se estiver sem criatividade é o site https://pokedex.org la tem os dados que o banco precisa.<br>

  # Iniciando o frontend

  Depois de testar isso tudo nós acabamos o backend, ou seja, todas as funcionalidades do nosso sistema estão mais lindas que o sorriso do breza, e olha que não é fácil isso não.

Agora uma nova vida, você irá começar a parte visual do sistema, que trabalham os caras mais feios do lab, são estes Oliver, Bruno e Pedro. Aqui no Labimboca’s Academy usamos o VueJS, você já deveria ter lido sobre, se não leu essa é uma boa hora pra aprender o básico.

Vale lembrar que toda a parte do frontend do nosso pokesistema fica dentro da pasta src!
      
      npm install vuetify --save
  
  ## Criando os componentes
  
  Primeiramente bom dia, segundamente vamos criar os componentes necessários para a nossa aplicação, itão dentro da pasta componente você digita esse comando magnífico, da-lhe:
  
    touch src/components/EXEMPLODECOMPONENTE1.vue
    
  Aqui você poderia adicionar outros componentes caso precise de 'mais telas', ou por exemplo algo que pode ser reutilizado, alguns exemplos do vue são tabelas, menus de navegação, enfim componentes que podem ser reutilizados pra poupar código.
  
  ## Criando as rotas
  
  Quais componentes vamos precisar pra nossa aplicação de pokedex? a minha sugestão é que da pra fazer tudo com um componente só. Mas se você quiser pode fazer mais de um para aprender sobre mudança de página(vueRouter) ou se ta afim mesmo. Criado(s) o(s) componente(s) vamos para as rotas do sistema, aqui é a parte que faz ‘ir de uma página à outra’. No arquivo src/router/index.js você precisa importar o(s) componente(s) recem criado(s) dessa maneira aqui:

```javascript
      import Vue from 'vue'
      import Router from 'vue-router'
      import COMPONENTE1 from '@/components/EXEMPLODECOMPONENTE1'
```

### Adicionando as rotas no index

e então adicionar ao router cada componente ou página...

```javascript
    export default new Router({
      routes: [
        {
          path: '/',
          name: 'EXEMPLODECOMPONENTE1',
          component: EXEMPLODECOMPONENTE1
        },
      ]
    })
```

Aqui nós botamos as rotas de todas as páginas que serão utilizadas, como nosso caso é o mais simples de todos eu sugeri tudo em uma pagina só, mas se você foi teimoso e fez mais eu não irei te ajudar daqui pra frente. Com a ajuda do [vuetify](https://vuetifyjs.com/pt-BR) inclusive é <s>full</s> está sendo traduzida para PT-BR pra auxiliar na sua falta de habilidade em inglês.

### Atualizando o src/main.js

Nosso arquivo src/main.js deve ficar assim

```javascript
    import Vue from 'vue'
    import Vuetify from 'vuetify'
    import App from './App'
    import router from './router'
    import 'vuetify/dist/vuetify.min.css'

    Vue.use(Vuetify);
    Vue.config.devtools = true;
    /* eslint-disable no-new */
    new Vue({
      el: '#app',
      router,
      components: {App},
      template: '<App/>'
    });
```
    
## Dica do dia
Uma dica para ter hot reload é -> fazer o node rodar o nosso arquivo bin/www.js lá em cima do webstorm no canto direito tem um botão 'add configurations' da um + node.js seleciona em working directory a pasta do aquivo e em JavaScript file seleciona o bin/www pronto da um apply ok sei la mais o que e aperta o debug ali, se rodar e aparecer aquele nosso console.log("connection succesful") quer dizer que o bagulho ta funcionando, e daí no terminal você manda um 

    npm run dev
 
 Que é o modo do desenvolvedor e todas as vezes que você der um ctrl+s na IDE ele atualiza a página, mágica não?!

### Modificando o index.html para funcionar o vuetify
E o index.html na raíz do projeto vamos adicionar essas linhas dentro do <head></head>

    <link href='https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900|Material+Icons'
          rel="stylesheet">
    <link href="./node_modules/vuetify/dist/vuetify.min.css" rel="stylesheet">
    
A minha sugestão é que você vá agora lá no site do vuetify procure nos componentes por data tables e <b>MyCRUD</b> vai descendo e acha, daí tenta entender o que ta rolando ali e copia a porra toda, tanto a parte vue quanto script no nosso aquirvo denominado src/components/'seilaquecaralhovoceescreveupronomedoarquivo'.vue depois de entender o bagulho, olha e testa e ve se ta igual o do site, se não tiver chame o Osvaldo.

## Dica 2 - Estrutura VueJS
  
```javascript
      data: () => ({
          dialog: false,
          headers: [
            {
              text: 'Name',
              align: 'center',
              value: 'name'
            },
          ],
          pokemon: [],
```

## Dica 3 - Primeira Requisição

  Exemplo de requisição, e o created() quando a página for criada ele ja vai fazer o que ta ali na hora.
  
  As outras requisições você deve fazer dentro de methods como eventos de click por exemplo, e asim vai! Boa sorte.
  
  Aproveite o máximo da estrutura mycrud que puxamos lá do vuetify.
  
```javascript
      created() {
      axios.get(`http://localhost:3000/pokemon`)
        .then(response => {
          this.pokemon = response.data
        })
        .catch(e => {
          this.errors.push(e)
        })
    },
```

Depois que você conseguir fazer o crud aparecer e funcionar na tela PARABÉNS VOCÊ CONCLUIU ESSA <s>MERDA</s> MARAVILHA QUE <s>COPIAMOS DE UM TUTORIAL GRINGO</s> CRIAMOS, dê um feedback positivo, negativo, ou fala o que quiser, não vai mudar nada na nossa vida mesmo!

Acredite você ou não, antigamente o treinamento era 10x pior. Vlw Flw!!!!

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

### Um agradecimento dos estagiáros do Lab e...

*pau no cu do osvaldo*
