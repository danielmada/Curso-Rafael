---
layout: post
title:  "Explorando Angular 1.5: Lifecycle"
date:   2016-06-13
tags: angular
keywords: angular 1.5, angular js, angular lifecycle, lifecycle hooks, ciclo de vida angular
resumo: >
  Components, Components, Components!... Entenda o component method que foi introduzido no Angular 1.5, Lifecycle Hooks e como isso pode mudar o jogo.
---
Nesse ano tivemos inumeras coisas boas acontecendo no meio tecnológico, [Angular 2](https://angular.io/) e [Ionic 2](http://ionicframework.com/docs/v2/) em versões Beta, [React v15](https://facebook.github.io/react/blog/2016/04/07/react-v15.html), [React-Router 2.0](https://github.com/reactjs/react-router), [Firebase](https://firebase.google.com/) com diversas features legais [mostradas no Google I/O](https://www.youtube.com/watch?v=tb2GZ3Bh4p8) e claro as novidades do [Angular 1.5](https://docs.angularjs.org/api).

Mas vamos ao que interessa e o porque eu estou escrevendo este artigo?

Eu poderia estar escrevendo sobre Angular 2, Firebase ou até mesmo sobre o ecosistema React, mas decidi falar de uma coisa que descobri a alguns dias atrás e me deu coragem para refatorar um antigo projeto de um cliente.

Os frameworks atuais mudaram a forma de pensar em web apps através de componentes. O Angular 1.5 mudou para melhor, e por mais que você esteja vendo coisas sobre Angular 2, Vue, React, etc... vale a pena conferir o porque ele está muito melhor que antes.

Novas features foram adicionadas, coisas sem sentido retiradas, algumas melhorias na performance e convenções vindas do Angular 2 de brinde que fizeram ser um grande release. Bem, se você ainda não viu nada [sobre Angular](/tags/#angular), talvez seja a hora de começar da maneira certa.

## Lifecycle Hooks
Primeiramente eu gostaria de mencionar que Lifecycle Hooks ou Lifecycle Methods não são algo novo, já vimos isso no post [Começando com React](/2015/comecando-com-react/), e também isso apareceu primeiro na versão alpha do Angular 2 e eles são bem menos inspirados nos **lifecycle callbacks** do [Custom Elements](http://webcomponents.org/articles/introduction-to-custom-elements/#lifecycle-callbacks) como anteriormente. Eles não tem apenas o nome e particularidades diferentes, na verdade eles são algo mais.

Um Angular 2 component possui métodos de controle do lifecycle tais como `ngOnInit()`, `ngOnDestroy()`, `ngOnChanges()` e muitos outros que estão [presentes na documentação oficial](https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html).

Focando agora na versão 1.x, se pensarmos que as futuras versões estão caminhando facilidade de migração de versão com o menor conflito possível alguns métodos do lifecycle foram encorporados na ultima versão. Vamos dar uma olhada em cada um deles:

**Lifecycle hooks foram introduzidos na versão 1.5.3**.

#### `$onInit()`

http://blog.thoughtram.io/angularjs/2016/03/29/exploring-angular-1.5-lifecycle-hooks.html
https://toddmotto.com/angular-1-5-lifecycle-hooks