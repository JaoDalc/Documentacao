# Entendendo a ORM

Antes de entendermos o que é uma ORM, temos primeiro que entender os conceitos _SOLID_.

## Explicando o SOLID

SOLID é um acrônimo que descreve:

- [Single-Responsability Principle](#s---single-responsability-principle)
- [Open-Closed Principle](#o---open-closed-principle)
- [Liskov Substituition Principle](#l---liskov-substituition-principle)
- [Interface Segregation Principle](#i---interface-segregation-principle)
- [Dependency Inversion Principle](#d---dependency-inversion-principle)

Iremos ver cada um destes separados para depois entender como eles se completam e como eles se relacionam com a ORM.

### S - Single-Responsability Principle

Este primeiro princípio nos diz que cada classe, função, entendidade ou qualquer outra coisa, deve ter uma única responsabilidade, i.e., não faça alguma aplicação fazer várias funções. O exemplo utilizado pelo próprio SOLID é um robô que possui várias funções, o que funciona, mas é errado podendo-se criar um robô para cada uma das tarefas. No nosso caso, várias funções ou várias entidades.

### Quais as vantagens?

### Reaproveitamento de Código

Usando o primeiro princípio, temos a grande vantagem de não precisar ficar escrevendo o mesmo código várias vezes. Quando fazemos uma função, desejamos usar ela várias vezes durante o código, entretanto, usando uma função com mais de uma responsabilidade, perdemos a oportunidade de usar ela com coisas semelhantes mas que é excludente de uma das partes de sua função com várias responsabilidades. Esse conceito segue a mesma linha da letra [D - Dependency Inversion Principle](#d---dependency-inversion-principle).

### Refatoração

Refatorar nada mais é do que mudar o código, fatorar (dividir) o código em partes e ir modificando ele. Seja por problemas, por uma nova solução, uma nova requisição do cliente.

Isso pode ser feito ainda mais facilmente quando um código é "enxuto" e não possui milhares de responsabilidades. Este valor é condizente tanto com o [Open-Closed Principal](#o---open-closed-principle) quanto com o [Interface Segregation Principle](#i---interface-segregation-principle).

### Resolvendo BUGS

Com o S, temos uma forma ainda mais fácil de resolver bugs. Imagine que um código foi feito e faça várias funções, havendo um bug, seu código não irá parar por completo! Na realidade, dependendo da importância da parte, irá, mas só uma estará com problemas. Será mais fácil de:

1. Lembrar o que faz o código.
2. Pensar na solução.

Algo extremamente necessário em qualquer ambiente de trabalho.

Pensando em um exemplo, tomemos um código que possua a `Parte A` e a `Parte B`, ambas as partes podem ser escritas como `Parte AB`. Agora digamos que a `Parte A` do seu projeto está com problemas e terá que ser refeita. O que é mais fácil? Fazer apenas a `Parte A` e integrar ela com a `Parte B` usando o [Interface Segregation Principal](#i---interface-segregation-principle), ou refazer a `Parte AB` inteira e ter que achar uam solução que funcione as duas coisas? Talvez seja necessário mudar de linguagem, ou integrar com outra linguagem. Talvez seja necessário fazer de uma forma completamente diferente que não tenha nem mesmo como integrar com a outra, mas a outra ainda é necessária.

Por isso, faça logo do começo da forma mais separar possível, para evitar essas situações. Agora, vamos para o O.

### O - Open-Closed Principle

Vamos para o segundo dos princípios. Temos agora um princípio que fala isso: Classes, entidades e funções devem estar abertas para extensões, mas fechadas para modificações. O que isso significa?

Digamos que há uma classe feita para fazer X coisa. Essa coisa pode ser modificada durante o código para fazer outras coisas, Y e Z, por exemplo, entretanto, o princípio critica isso e diz que deve-se somente adicionar Y e Z, e não modificar X para fazer Y e depois fazer Z. Como assim?

Uma coisa não deve ser alterada para fazer outra, podemos, dentro de um código, fazer duas coisas, como autenticar e enviar, mas não podemos ter uma mesma parte para fazer as duas.

### Facilidade de Entender o Código

Além de facilitar a compreensão do código, já deixo outra vantagem desta letra que é a resolução de bugs, a qual está no mesmo sentido que isso.

Viu o que eu fiz ali em cima? Sim, neste último parágrafo, eu adicion uma nova informação sem alterar em nada a primeira, isso é o Open-Closed Principle. É natural pensarmos que um código fazer mais coisas é simples, entretanto, separar bem o código e fazer com que ele tenha uma base sólida para funcionar bem, é muito melhor. Não usar desse princípio tem como outra opção

### Mas... O que isso tem a ver com a ORM?

A ORM, em via de regra, usa códigos genéricos como "salvar", "inserir", etc, etc. Sabendo disso, podemos fazer com que a base da ORM, a base do código, se mantenha igual, ou seja, o que retornamos ser sempre a mesma coisa, isso é facilitado com o OCP, o qual diz que devemos sempre estender sem modificar, ou seja, podemos pegar vários valores de um banco de dados em uma mesma classe, entretanto, sem modificar o getter (quem irá pegar os dados), para evitar que hajam milhares de condições e problemas no código.

### L - Liskov Substituition Principle

Um conceito complexo mas fácil de entender para quem já tem um certo nível de compreensão de códigos é o LSP, ou Liskov Substituion Principle.

Se você já trabalhou com heranças, pode se confundir um pouco com esse conceito, pois aqui ele está para lhe fazer repensar o que você acha que sabe sobre heranças.

[//]: # (Sobre esta parte, não sei extamente se o que estou escrevendo aqui esta correto, mas será escrito e depois vejo se não confudi tudo)

O jeito correto de se fazer uma relação de heranças seria, utilizando de um exemplo esdrúxulo, o filho herda um terreno de seu pai e faz um apartamento. Outro filho transforma em um hospital, entretanto, o terreno é o mesmo. Agora, pressuponha que outro filho deseje construir um helicóptero, ele não precisará de um terreno. Assim, no código, é possível que vários filhos precisem de uma coisa X, mas se outros vários filhos tiverem que excluir essa parte ou lutar contra algo vindo do pai,  você deve se perguntar se vale mesmo a pena ter essa herança.

### I - Interface Segregation Principle

O I é uma das partes mais bobas de toda a documentação aqui presente, seu vir-a-ser é bem básico e seu conceito de fácil compreensão, entretanto, ainda é uma parte essencial e que pode não ser óbvia para todos os desenvolvedores em um primeiro momento.

O I, basicamente, é "não faça coisas juntas". Se você irá fazer uma tela de cadastro você não precisa fazer com que ela e o login seja no mesmo local, e isso é extremamente importante pois se um falhar, o outro ainda pode funcionar, neste caso, o login poderia continuar funcionando, todo o site poderia continuar funcionando, mas ainda não haver cadastro. Como isso se ligaria, então? Através de uma interface, vide o nome da seção.

### D - Dependency Inversion Principle

Uma coisa não deve depender de outra. Vamos pensar por exemplo em pregar. Você precisa de um martelo, correto? Agora, o que é mais fácil e prático, usar um robô que martele ou usar um robô já existente no projeto + uma ferramenta martelo? Também é possível utilizar outras ferramentas caso o martelo não esteja funcionando, é possível modificar a ferramenta sem necessariamente mudar o executor.

Isso é algo que é primordial pois uma ferramenta deve ser passível de uso por várias partes do código e de forma independente. Além disso, um robô deve fazer um trabalho com várias ferramentas, nem só de martelo vive o homem, então, para respeitarmos a letra [O (Open-Closed Principle)](#o---open-closed-principle) temos de fazer isso ser independente e sem modificar nada. Veja como os princípios se encaixam perfeitamente.

## O que é a ORM?

Agora que entendemos os conceitos básicos, vamos ir avançando! O que significa a sigla ORM? _Object Relational Mapping_ ou _Mapeamento Objeto-Relacional_. Uma ORM muda de linguagem para linguagem e, até mesmo dentro de uma, existem várias possibilidades. As duas ORM's utilizadas pelo `Website` são o Eloquent e o Doctrine . As ORM's seguem mais ou menos o CRUD: Create, Read, Update e Remove. Entretanto, as ORM's podem ser responsáveis por Conexões e Query's, entre outros diversos usos. A função da Orm é, também, abstratir inteiramente a base de dados. O que isso significa? Veja este comando:

``` sql
    SELECT * FROM users WHERE email = 'test@test.com';
```

Com a ORM, ao invés de ser escrito dessa forma "crua", ele será abstraído e será escrito assim:

``` js
var orm = require('generic-orm-libarry');var user = orm("users").where({ email: 'test@test.com' });
```

A linguagem, inclusive, pode ser alterada, acima, temos ela em JavaScript, entretanto, ela pode literalmente ser qualquer outra compatível com a ORM instalada.

Outro ponto importante das ORM's é que você pode, seguindo o princípio [I (Interface Segregation Principle)](#i---interface-segregation-principle), utilizar a mesma interface para database's diferentes e ambientes diferentes. Isto está de acordo com o [Single Responsability-Principle](#s---single-responsability-principle) que diz que a ORM deve fazer apenas uma tarefa, sim, de fato, ela o faz, ela faz a integração do código com os bancos de dados, puxar, selecionar, inserir, tudo está dentro da responsabilidade dela, mas, segue também o segundo princípio o [O (Open-Closed Principle)](#o---open-closed-principle) que fala que podemos extender sem modificar. Exatamente isso é feito pela ORM.
