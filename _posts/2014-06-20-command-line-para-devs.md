---
layout: post
title:  "Command Line para Devs"
date:   2014-06-20
categories: outros
tags: lifestyle produtividade
image:
keywords:
resumo: >
  Saber utilizar o terminal em ambientes unix/linux é mais que um pré-requisito para nós desenvolvedores, ele provavelmente vai ser seu melhor amigo mas também pode ser seu pior inimigo se não souber utiliza-lo.
---
Ser um desenvolvedores, seja front/back end, mobile, WTV... trabalhando com projetos PHP, Ruby, Python, etc... que normalmente são hospedados em Linux, e saber linux facilita muito nossa vida, simplifica muita coisa em nosso dia-a-dia como automatizar tarefas, instalar dependencias, entre outras coisas.

Sou suspeito para falar sobre isso já que comecei a utilizar linux <del>(Conectiva 9/KDE)</del> em meu primeiro computador <del>(AMD k6-2 500Mhz/128MB/HDD 1GB)</del> porque Windows 2000 e XP ficavam lentos, mas vamos lá.

##Porque aprender a utilizar o Terminal?
Claro que alguns programas/IDE's são cheios de botões que facilitam as principais tarefas como o [SourceTree](https://www.sourcetreeapp.com/) que é um GUI para git, entre muitos outros softwares. Mas e se você tiver que ir além? Um [rebase](https://git-scm.com/book/en/v2/Git-Branching-Rebasing) talvez?

E quando a coisa complica e você precisa acessar o servidor, criar um VirtualHost no Apache, ou modificar o valor de uma variável de ambiente? Não tem jeito, você vai ter que usar o terminal para realizar a tarefa.

Outro motivo é que em projetos front end, você vai precisar atualizar/baixar as dependencias, rodar um task runner como [Grunt]({{site.url}}/2014/automacao-de-tarefas-com-grunt/), [Gulp]({{site.url}}/2014/gulp-chegou-para-ficar/), [Bower](http://bower.io/), etc.

Não se preocupe, tudo depende de como você usa e para que você usa. Se você precisa aprender ao menos o básico sobre Terminal(Command Line) você veio ao lugar certo.

##Command Line é seu melhor amigo
Sim, normalmente são aquelas letras brancas (ou verdes) em uma tela preta onde coisas misteriosas acontecem através de texto e comandos estranhos.

Primeiro vamos falar sobre o **bash**.

BASH (Bourne Again Shell) esta presente em distribuições Linux e também no OSX da Apple. Foi criado lá por 1989 e normalmente pode ser executado em `/bin/sh` e `/bin/bash`.

O meu bash por exemplo esta personalizado, mas em linhas gerais tenho algo mais ou menos assim em meu terminal:

{% highlight PowerShell %}
rafaell@rafaell-pc: ~/github/rafaell-lycan $
{% endhighlight %}

Em linhas gerais: **rafaell** é o meu usuário da maquina, **rafaell-pc** é o nome do meu computador e `~/github/rafaell-lycan` é a pasta onde estou. Vale resaltar que o simbolo `~` refere-se ao **diretório home** do usuário. O cursor `$` indica que não estou logado como **root**, ou seja eu não tenho permissão para fazer algumas coisas no sistema. Todos os exemplos a seguir não necessitam do cursor.

Alguns comandos básicos:
{% highlight PowerShell %}
$ whoami # Enter
rafaell
$ hostname # Enter
rafaell-pc
$ pwd # Enter
/Users/rafaell/github/rafaell-lycan
{% endhighlight %}

####Navegando entre diretórios
Você pode alternar entre diferentes diretórios através do comando `cd`

{% highlight PowerShell %}
cd nome_diretorio/sub_diretorio/outro_diretorio

cd ../diretorio_relativo/diretorio/sub_diretorio/outro_diretorio

cd /diretorio_raiz/outro_diretorio/sub_diretorio/ainda_outro_diretorio
{% endhighlight %}

####Listando arquivos e diretórios

####Copiando e movendo arquivos

####Deletando arquivos e diretórios

**Mas como eu sei quais opções um comando possui?**

####Procurando arquivos

##Comando Sudo

##Vamos falar sobre permissões

##Histórico, !! e !$

##Conclusão

Links:
http://code.tutsplus.com/tutorials/the-command-line-is-your-best-friend--net-30362
http://code.tutsplus.com/tutorials/7-simple-and-useful-command-line-tips--net-11608
http://code.tutsplus.com/articles/10-terminal-commands-that-will-boost-your-productivity--net-14105

http://promo.visie.com.br/curso-gratis-de-terminal-do-linux