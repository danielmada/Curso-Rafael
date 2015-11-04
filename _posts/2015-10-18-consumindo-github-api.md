---
layout: post
title:  "Consumindo o Github API"
date:   2015-10-18
categories: javascript
tags: javascript angular
image:
keywords:
resumo: >
  Neste post trago tudo o que abordamos até agora sobre o fantástico mundo do AngularJS, contudo, vamos um pouco mais além, e também vamos aprender a utilizar ES6 com Browserify e Babelify com Gulp.

related:
  - title : $resource API
    url: https://docs.angularjs.org/api/ngResource/service/$resource
  - title : Ajax with $resource by Learn Angular.org
    url: http://learn-angular.org/#!/lessons/ajax-with-resource
---
Este não é mais um post de exemplo de como utilizar algo dentro do [AngularJS](https://angularjs.org/), na verdade este é um tutorial de como fazer um desafio passado a um outro desenvolvedor.

##Prefácio
Eis que estava tranquilo, simplesmente trabalhando, tentando convencer outras pessoas a utilizar Angular e fazendo algumas coisas que me veio a ideia de escrever sobre isso.

Este post é culpa de algumas pessoas, a primeira delas é o [@antenando](https://twitter.com/antenando) que me mostrou que configurar um builder complexo pode ser mais simples do que imaginava, e o [@viniciusllima](https://twitter.com/viniciusllima) que se propos a aprender Angular em 2 semanas e fazer este pequeno desafio.

Primeiramente quero apresentar a vocês o [Github Pulse](https://github.com/tadeuzagallo/GithubPulse). Um projeto do meu amigo [@tadeuzagallo](https://twitter.com/tadeuzagallo) utilizando [React.js](https://facebook.github.io/react/) para a criação das views e seus componentes.

###Indredientes:
O objetivo deste post é mostrar como fazer o mesmo APP *(clone)* utilizando:

- [Angular.js](https://angularjs.org/), para utilizarmos o que vimos até agora nos posts anteriores;
- [Browserify](http://browserify.org/), que nos permite utilizar transforms como o [Babelify](https://github.com/babel/babelify) e usar ES6 e Babel;
- E o [Gulp](http://gulpjs.com/), para juntar tudo e partir pro abraço.


##Mantendo o MVP simples:

O APP desenvolvido consiste basicamente em consumir o [Github API](https://developer.github.com/v3/) e obter informações sobre o usuário;

Vamos imaginar isso em 3 telas únicas em nosso sistema:

- Login: Onde temos um input que recebe o nome do usuário do Github;
- User: Que exibe as informações do usuário em sí;
- Following users: Que nada mais é do que a lista de usuários que o usuário segue;

##Configurando nosso Builder:
Primeiro de tudo, criamos nosso arquivo `package.json` e instalamos algumas dependencias:

{% highlight text %}
npm install --save-dev gulp gulp-browserify babelify gulp-plumber
{% endhighlight %}

Sobre as extensões o `gulp-browserify` é um wrapper para o gulp já utilizando o [vinyl-source-stream](https://www.npmjs.com/package/vinyl-source-stream) para fazer stream dos arquivos; `babelify` é o wrapper para o [Babel](https://babeljs.io/) que vai nos permitir escrever em ES6 sem problemas e o `gulp-plumber` tem a função de evitar/previnir error que possam acontecer durante o build e parar a execusão do script.

##$http Service
Vamos utilizar um simples código de exemplo:

{% highlight javascript %}
app.controller('MyController', ['$scope', '$http', function($scope, $http) {
  $scope.users;
  var baseUrl = '/api/users';

  $http.get(baseUrl).then(function(response) {
    $scope.users = response.data;
  }, function(err) {
    console.log(err);
  });
}]);
{% endhighlight %}