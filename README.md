# VueJS-Router

Todos temos determinada dificuldade ao iniciar os estudos de uma nova linguagem, seja ela Orientada a Objetos, Eventos e etc. Mas sempre que iniciamos o estudo de uma nova linguagem (ou quase sempre), temos motivos particulares.
Quando comecei a estudar Jquery em 2011, queria desenvolver sistemas em Real Time, então tentei aprender apenas Ajax (sem muito sucesso), como eu estava focando em aprender apenas aquilo, aprender Jquery em si se tornou uma tarefa dificil. Porem foi ai que descobri que não se trata de ser dificil ou facil, se trata de como aprendemos (ou como as pessoas ensinam).<br>
<b>Agradecimentos ao nosso mestre SUISSA \o/</b><br>
Então vamos colocar a mão na massa.<br>
Para iniciarmos, é bom lembrar que iremos trabalhar com Vue.cli, então para isso, iremos precisar do NodeJS instalado, é possivel baixar em https://nodejs.org/en/ .<br>
Apos isso, iremos instalar o vue.cli pelo NPM. Abra seu Terminal (ou CMD) e digite o seguinte comando:<br><br>
<code>npm install --g vue-cli</code><br>
OBS: utilizamos o --g para instalar o vue-cli globalmente.<br>
Agora iremos iniciar (criar) nosso projeto, escolhendo com qual tema gostariamos de iniciar (com <code>npm vue list</code> você pode ver quais temas estão disponiveis).<br>
Vamos começar utilizando o tema webpack-simple, então iremos executar o seguinte comando <code>vue init webpack-simple nome-da-pasta-do-seu-projeto</code>. Apos isso precisamos entrar dentro da pasta <code>cd nome-da-pasta-do-seu-projeto</code> e instalar as dependencias com <code>npm install</code>.<br>
Pronto! Agora é só testar :D <code>npm run dev</code><br><br>
Com isso pronto, já temos nosso projeto pronto para trabalharmos com router. Os arquivos que iremos trabalhar serão <code>main.js</code>, <code>App.vue</code> e mais dois arquivos que iremos criar.<br><br>
Vamos começar criando os dois arquivos na pasta <code>src</code>, o primeiro arquivo irá se chamar <code>Users.vue</code> e o segundo <code>Home.vue</code><br><br>
Ao abrir o <code>main.js</code> você ira ver algo mais ou menos assim:<br>

        import Vue from 'vue'
        import App from './App.vue'
        new Vue({
          el: '#app',
          render: h => h(App)
        })
E o <code>App.vue</code> assim:
```
         <template>
  <div id="app">
    <img src="./assets/logo.png">
    {{ msg }}
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hello World'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

````

Agora vamos adicionar textos as paginas que criamos, na <code>Home.vue</code><br>

        <template>
          <h1>Eu sou Home!</h1>
        </template
E basicamente a mesma coisa no <code>Users.vue

        <template>
          <h1>Eu sou Users!</h1>
        </template

Feito isso já temos toda nossa estrutura funcionando, agora basta instalarmos o vue-router utilizando <code>npm install vue-router</code>, e iremos modificar o <code>main.js</code>

        import Vue from 'vue'
        import VueRouter from 'vue-router'
        import App from './App.vue'
        // Paginas
        import Users from './Users.vue'
        import Home from './Home.vue'

        Vue.use(VueRouter)

        const routes = [
                { path: '/users', component: Users },
                { path: '/', component: Home }
        ];

        const router = new VueRouter({
                routes,
                mode: 'history'
        });

        new Vue({
          el: '#app',
          router,
          render: h => h(App)
        })


Simples :D
