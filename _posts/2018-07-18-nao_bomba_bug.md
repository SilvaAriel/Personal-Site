---
layout: post
title: "Não use uma bomba contra um bug"
ref: nuke_the_bug
date: 2018-07-18
categories: bug
lang: pt
---

Nós todos já fizemos isso.

Quando encontramos um bug ~~inseto~~ de verdade nós não usamos grandes ferramentas para matá-lo. Nós usamos nossos pés ou um inseticida.
Mas as coisas são um pouco diferentes quando encontramos um bug no nosso código. Nós normalmente tentamos solucioná-lo sem pensar direito e acabamos usando uma arma nuclear. Pode até acabar com o bug mas irá criar uma bagunça maior ainda do que a anterior.
Nós temos que usar as ferramentas corretas para solucionar os bugs. Mas para fazer isso, nós temos que entendê-lo primeiro. Eu já bombardeei alguns bugs e eu entendo o dano que isso pode causar. Por isso que eu decidi seguir uma outra abordagem para solucionar ~~esmagar~~ esses bugs malditos.

Eu sigo os seguintes passos:
* Escrever o principal problema.
* Achar onde ele começou.
* Criar 3 hipóteses para solucioná-lo
* Tentar uma de cada vez.

### Explicação
**Escrever o principal problema**:
Nós nos perdemos tentando solucionar um problema mais do que gostaríamos de admitir. Talvez a gente comece a pesquisar a solução no Google, mas acabamos achando algo interessante e desviando a nossa atenção. Temos que manter em mente que nosso único objetivo é solucionar o bug atual. Deixe as outras coisas maneiras para depois.

**Achar onde ele começou**:
Onde o bug nasceu? Temos que achar onde nossos dados começaram a se comportar mal para entender o que exatamente deu de errado.

**Criar 3 hipóteses para solucionar o bug**:
O que você acha que provavelmente está causando o bug? Escreva 3 possíveis soluções que você acha que possa aplicar.
Por que 3? Pode ser qualquer número que você quiser, mas não somente 1. Por quê? Porque esses passos servem para nos manter focados. Se provarmos que a nossa única hipótese está errada talvez nós nos desviemos e voltemos a pesquisar no Google por toda eternidade!

**Tentar uma de cada vez**:
Então, depois disso tudo, nós podemos escolher uma hipótese que pensamos estar mais próxima da raiz do problema e começar a implementá-la.

Esses são os passos que eu uso para solucionar um bug. Você pode pegar essa lista e adaptá-la a sua vontade. Não é uma lista exaustiva, então eu estou a melhorando. Você pode fazer o mesmo.

Até mais!