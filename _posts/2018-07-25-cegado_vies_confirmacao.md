---
layout: post
title: "Não seja cegado pelo Viés da Confirmação"
ref: blinded_confirmation_bias
date: 2018-07-25
categories: vies_congnitivo
lang: pt
---

Sabe quando você (acha que) sabe solucionar um bug, mas de algum modo você passa ~~horas~~ muito tempo nele? Só para perceber que você esteve errado o tempo todo e que a solução era outra?

Bom, você pode agradecer ao <a href="https://pt.wikipedia.org/wiki/Vi%C3%A9s_de_confirma%C3%A7%C3%A3o">Viés da Confirmação</a>.

### É uma armadilha, Bino!

Eu estou criando um <a href="https://github.com/SilvaAriel/presente">CRUD do Nodejs com TDD</a> só para fins de aprendizagem. E eu cheguei no teste de banco de dados. 

O teste cria um dado falso, salva ele usando o Mongoose e roda o teste usando esse dado criado. Depois de todo os testes, a coleção (onde todos os dados estão) é apagada automaticamente.

Eu consegui fazer tudo acima, menos a parte de apagar a coleção. De algum modo o dado falso criado no início do teste estava sendo apagado antes do final do teste.

Mocha (um framework de teste) tem um hook chamado "after()". E ele faz basicamente o que diz: ele roda depois de todos os testes. Mas de alguma maneira, a coleção estava sendo apagada antes do final. Então eu pensei "Eu provavelmente não sei como o hook do Mocha funciona".

Por isso, eu fui direito a <a href="https://mochajs.org/#hooks">documentação do hook</a>, mas não me ajudou muito. Não me entenda mal, a documentação é ótima, mas eu não achei muito sobre o "after()". Ela só dizia o óbvio: ele roda depois de todos os testes.

Eu comecei a pensar que o Mocha estava com um bug. Sabe como que é né? As chances do framework estar errado é maior do que nós estarmos. (Todos já pensamos isso antes, certo?)

Depois de mais de uma hora (eu cronometei) tentando solucionar isso, eu estava cansado. Eu não sei como, mas eu comecei a pensar que talvez o problema não estava no hook, mas na função do Mongoose.

Eu achei aquela função numa <a href="https://stackoverflow.com/questions/10081452/how-to-drop-a-database-with-mongoose">pergunta no StackOverflow</a> e eu lembrei que haviam duas maneiras de apagar a coleção.
Então eu adaptei a segunda ao meu código e funcionou! Simples assim. Meus testes estavam rodando lisinhos sem nenhum erro.

### Conclusão

Eu cheguei a uma conclusão: eu sou muito burro! Não, tô de zoa. A resposta não é tão fácil assim.

### O que aconteceu?

Eu fui cegado pelo Viés da Confirmação.

Eu estava tão certo que o problema era o "after()" que eu fiquei míope. Eu não conseguia ver nada além do problema. E quanto mais eu pesquisava (sem achar nada) mais eu me fechava para outras respostas.

Agora está tudo claro. O problema era que a função era assíncrona:
```javascript
//classes é o nome da coleção
mongoose.connection.collections["classes"].drop((error)=>{
    if(error){
        console.log(`Drop collection error: ${error}`)
    }
})
```

É óbvio que o banco de dados estava sendo apagado antes do teste acabar! E eu sabia que Mongoose retornava Promises! Mas, reitero, eu estava tão focado em solucionar o que eu achava ser  o problema que esqueci disso.
Eu até pensei que o problema era do Mocha.

<span style="color: gray">Desculpa Mocha, vocês são demais!</span>

**Quando estamos cegados pelo Viés da Confirmação, a culpa é sempre do outro. Nunca nossa.**

Se essa história soa muito familiar pra você, você não está sozinho. Eu acho que todos nós programadores enfrentamos esse problema frequentemente. Então, para nos ajudar a não cair nessa armadilha de novo, eu pensei em 4 passos para seguirmos enquanto debugamos.

### Prevenindo o Viés da Confirmação

Os passos são:
1. Desmonte a função.
2. Escolha 2 partes dela que você acha que pode estar causando o problema.
3. Prepare um cronômetro com contagem regressiva para procurar a solução.
4. Procure.

# Explicando
1. Desmonte a lógica do código para ficar mais fácil de entender.
2. Essa parte é a mais importante para previnir o Viés da Confirmação. Você está tentando solucionar um bug e provavelmente já pensou numa solução. Para previnir que você fique preso nisso para sempre, você escolherá outra possível solução para tentar também.
3. Esse complementa o último ponto. Bote o cronômetro em contagem regressiva para evitar procurar eternamente pela solução que você acha que solucionará o problema. Pode ser um <a href="https://pt.wikipedia.org/wiki/T%C3%A9cnica_pomodoro">pomodoro</a>.
4. Vá procurar!