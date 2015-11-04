---
layout: post
title:  "Autenticação com Tokens em uma aplicação AngularJS"
date:   2016-05-23
<!-- image: assets/img/posts/hello-world.jpg -->
keywords: angular, jwt, auth, js
resumo: >
  Neste artigo vamos ver como desenvolver um exeplo de autenticação utilizando AngularJS Json Web Token.
---
Primeiramente vamos a pergunta que não quer calar: **você usa tokens?**

Então todo mundo já utilizou token algumas vezes na vida. Como? Sabe aqueles arquivos marotos que ficam em nossos navegadores chamados **[cookies](https://en.wikipedia.org/wiki/HTTP_cookie)**? Então, a cada vez que utilizamos sessão do servidor, a aplicação grava um número composto da sessão e expiração em um cookie. Sim, você usa token, talvez apenas não se deu conta disso.

Tokens são uma forma de se identificar com a aplicação, nada mais que isso.

Num mundo virtual cada token representa uma sessão/identificação. Um token pode conter N informações como nível de acesso, data de expiração e outras coisas não muito recomendadas como ID do usuário normalmente encriptado com 128 bits (128-bit [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)).

Quando falamos de tokens, temos que ter uma maneira simples de criar um padrão de tokens inteligentes, e toda essa magia por traz disso é composta por algumas especificações do Json Object Signing and Encryption (JOSE) que é um conjunto de definições dos padrões para a criação de tokens inteligentes ([RFC 7519](https://tools.ietf.org/html/rfc7519)).

JOSE divide a ordem lógica de criação e composição de tokens em 5 padrões: JWT, JWA, JWS, JWK e JWE.

## JWT
Json Web Token (JWT) é um padrão ([RFC 7165](https://tools.ietf.org/html/rfc7165)) que define como transmitir de forma segura objetos JSON compactos entre aplicações. Neste artigo vamos nos focar nele.

Para criarmos um JWT, precisamos entender que ele é composto por 3 elementos:

#### Headers
**Headers** são objetos JSON que normalmente definem duas partes: O **tipo do token** (typ) que é **JWT**, e o **algorítimo (alg) de encriptação** que será utilizado, como HMAC SHA256 ou RSA;

Exemplo:
{% highlight json %}
{
  "alg": "HS256",
  "typ": "JWT"
}
{% endhighlight %}

#### Payload (Claims)
**Payloads** são objetos JSON que contem os chamados **claims**, que pode definição são os atributos sobre a entidade tratada (normalmente o usuário). Existem 3 tipos de claims em payloads:

- Reserved claims: São atributos não obrigatórios (mas recomendados) que podem ser um conjunto de informações úteis e interoperáveis normalmente utilizados por protocolos de segurança em várias APIs. *Ex: **iss**(issuer), **exp**(expiration), **sub**(subject), etc.*
- Public claims: São atributos que definem o uso do JWT e informações úteis para a aplicação.
- Private claims: São atributos definidos especialmente para compartilhar informações entre aplicações

Exemplo:
{% highlight json %}
{
  "iss": "https://api.github.com",
  "exp": 1300819380,
  "user": "rafaell-lycan",
  "admin": true
}
{% endhighlight %}

#### Signature
Onde a magia acontece, é a terceira e ultima parte do nosso JWT feita a partir do hash (Base64Url) do header e do payload e uma **chave** definida em nossa aplicação e assinar isso.

Vamos a um exemplo utilizando o algoritimo HMAC SHA256:
{% highlight javascript %}
var encodedString = base64UrlEncode(header) + "." + base64UrlEncode(payload);

HMACSHA256(encodedString, 'secret');
{% endhighlight %}

Isso ira gerar um token com essa estrutura:
{% highlight bash %}
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJodHRwczovL2FwaS5naXRodWIuY29tIiwiZXhwIjoxMzAwODE5MzgwLCJ1c2VyIjoicmFmYWVsbC1seWNhbiIsImFkbWluIjp0cnVlLCJpYXQiOjE0NjQxOTQzNTh9.CcXOdvwL1baDNzhEjds9u59oHVrqG97hj9oVdZMzpaI
{% endhighlight %}

Perceba que é uma string dividida em **3 partes** separados por `.`, sendo elas os respectivos hashs dos headers, payload e signature.

Atualmente o [Auth0](https://auth0.com/) é o melhor lugar para tirar informações sobre como criar e testar seus tokens. Você também pode utilizar o [JWT Debugger](https://jwt.io/) para verificar se a assinatura é válida.

**Tudo muito lindo e legal, mas como isso funciona na prática?**

Imagine que sua Aplicação possui 2 clientes: SPA e Mobile. Nós utilizaremos o JWT para **autenticar** o usuário a acessar certas partes da nossa aplicação, mas para isso ele precisa logar em nosso sistema que retornar um JWT a ser armazenado na aplicação (LocalStorage/SQLite) ao invés de utilizar o modo tradicional através de cookies e sessão.

Sempre que for necessário acessar recursos protegidos, o cliente deve enviar o JWT através do **Authorization** na header utilizando a flag **Bearer**.

{% highlight json %}
Authorization: Bearer <token>
{% endhighlight %}

Este é um exemplo de autenticação **stateless**, que é uma forma de proteger rotas onde uma vez que o usuário o JWT definido, ele pode acessar recursos protegidos. Uma boa ideia é colocar alguns dados no payload que irão reduzir o acesso ao DB sem necessidade. Essa também é uma forma de permitir serviços comunicarem-se entre si.

![Comunicação via JWT](https://cdn.auth0.com/content/jwt/jwt-diagram.png)

## Angular App
No lado cliente, nossa aplicação Angular precisa enviar dados de autorização para nossa API no cabeçalho a cada requisição HTTP.

Essa é uma alteração comum em uma aplicação MEAN Stack, pois como disse anteriormente cookies não são a melhor maneira de criarmos e utilizarmos tokens.

#### Estrutura do Projeto

#### Autentication Service

#### HTTP Interceptor
