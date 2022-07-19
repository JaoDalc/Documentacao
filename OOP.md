### O que é a Programação Orientada a Objetos?

A POO (Programação Orientada a Objetos) veio para resolver problemas que a PP (Programação Procedimental) tinha. Para ver em que forma se diferenciam, clique
 [aqui](#procedimental). Porém, o conceito em si da orientação a objetos é vasta e pode ser trazida para vários conceitos, seja ele empresarial ou familiar.
 Parte importante de ter uma empresa, é saber reutilizar, saber como manter-se relevante durante anos é uma prática difícil e que deve sempre ser uma das prioridades.
 
 Porém como fazer isso sendo que coisas novas podem demorar anos para serem feitas? Utilizando a orientação a objetos. 
 
 Criando formas de reutilizar partes de uma aplicação, produto ou método de criação. Imagine que tenhamos 6 sites/aplicativos diferentes, porém, todos eles possuem o mesmo 
 checkout, uma forma de pagar pelo serviço realizado. Essa forma pode ser reaproveitada. Mesmo que diversos fatores mudem, seja o produto, os nomes que serão usados, os usuários, 
 forma de pagamento, tipo de impressão, etc; tudo isso pode ser feito de uma forma dinâmica e que possibilite que não precise ser criado o mesmo tipo de checkout em diversas aplicações.
 
 Assim também podemos pensar em funções. Funções ainda são muito mais utilizadas que partes completas de uma aplicação. Formas de salvar dados no banco de dados ou formas de extrair informações,
 tudo pode ser feito seguindo os conceitos de orientação a objetos. Claro, por vezes, é necessário copiar uma função quase perfeitamente igual outra pela praticidade e pelos prazos dados que são 
 curtos demais para realmente parar e reorganizar várias partes para seguir um padrão, porém, seguindo os conceitos mostrados mais a frente, é possível criar novas funções que todos possam usar. 
 Gerando facilidade, velocidade, e o mais importante, organização.

 Caso o exemplo de uma aplicação seja ruim, pensemos neste mesmo arquivo. Diversas partes dele poderiam ser utilizadas novamente em várias e várias partes que não 
 são principais. Podemos chamar o tópico [Abstração](#abstracao), ou o [Qual sua diferença para a Programação Procedimental?](#procendimental) sem precisar reescrever partes do arquivo
 para se adaptar a necessidade, apenas adicionando certas palavras (código) para tratar das informações referenciadas. Apenas neste exemplo, podemos ver
 a Abstração, você não precisa ler todo o tópico (função) para entender o que ele faz, herança, pois a mesma coisa pode ser usada várias vezes e, polimorfismo
 pois o papel feito pela referencia muda de acordo com a chamada da mesma.
 
 Vejamos especificamente os conceitos para ter maior entendimento deles.
  
  ---
  
#### Encapsulamento

O encapsulamento é uma forma de segurança para os atributos da classe e que permite com que alguns atributos sejam (ou não) modificados de formas diferentes.
Para certas informações, você não quer que qualquer um modifique, de qualquer jeito, o objeto. Coisas mais estruturais e que realmente podem causar problema não devem ser modificadas de qualquer forma.

Outra coisa que o encapsulamento proporciona é a localidade de variáveis. Deixando as variáveis ali dentro, ela pode ser alterada, modificada, excluída, e permanecerá lá, mesmo que haja um `return()`, 
é escolha da aplicação receber e usar esse resultado. Além disso, essa camada é importante para gerar verificações dos dados. Imagine que salvaremos dados no banco de dados a partir de um objeto.
Esse objeto deve possuir um valor int, dois valores string e um array. Esse objeto vai ser instanciado em diversos locais da aplicação, para garantirmos que ele sempre terá os valores que o banco 
necessita para não dar um erro absurdo, podemos transformar os atributos em privados e fazer com que apenas um método, que faz diversas verificações, criar, ou não, o objeto e devolver um erro. Até mesmo colocar um status `no modifier` pode existir.

---

<a id="abstracao"></a>

#### Abstração 

Abstrair uma parte do código é transformar essa parte do código em algo mais... abstrato. Assim como na língua portuguesa, 
abstrair significa `observar (um ou mais elementos de um todo), avaliando características e propriedades em separado.`, essa descrição pode muito bem definir o que 
é abstrair coisas do código. É literalmente pegar essas coisas, de preferência mais complexas ou com uma funcionalidade que pode ser utilizada por vários locais e
colocar toda essa complexidade lá e passar apenas o resultado dessa coisa tão maluca.

---

#### Herança

A herança é o principal conceito (se é possível o ter) da POO. Esse conceito é o que irá fazer com que haja impacto direto no número de linhas e onde que as coisas
de fato acontecem. Além de a herança permitir uma maior legibilidade do código, levando em consideração que ler uma linha chamando uma função que faz x, é mais fácil que entender
o que aquelas várias linhas fazem dentro de um código enorme. A possibilidade de reutilizar o código é saudável em diversos níveis, não impede a especialização de funções,
levando em consideração o princípio de [Abstração](#abstracao) e além disso, permite com que existam maiores soluções de problema. Vide o fato de que várias pessoas estariam usando a mesma frase.

---

#### Polimorfismo

Polimorfismo não é necessariamente um conceito da POO, mas a POO que usa o polimorfismo tão bem que tornou-se intrinseco o uso desse conceito a própria orientação a objtos.
Este conceito nada mais é que utilizar o mesmo objeto de formas diferentes. Em uma situação com Interfaces é necessário trabalhar com diferentes requisições. Onde um 
atributo define qual forma que a função tomará e/ou como ela agirá baseado no tipo de requisição. 

---

<a id="Procedimental"></a>

### Qual sua diferença para a Programação Procedimental?

A grande diferença entre a POO e a PP é o fato de a PP precisar alterar diversas funções pela falta de uma forma de centralizar as funções. Imaginemos esse código:

```php
  public function removeObjeto(
  int $id, 
  int $codigoObjeto, 
  string $variavelAleatoria1, 
  EntityAleatoria $variavelAleatoria2
  ) {
        $this->repository->remove($id, $codigoObjeto, $variavelAleatoria1, $variavelAleatoria2);
  }
```

Essa função pode ser reaproveitada? Imagine um código onde Objeto pode ser tanto chave de fenda como coxinha. Sim, pode ser reaproveitado. 
Claramente o exemplo é esdrúxulo, porém coisas que compartilham características, não só podem como, devem utilizar as funções para a mesma tarefa. 

A comparação com a `removeObjeto` é prejudicada por uma questão de limitação do quanto sabemos sobre a aplicação que utilizaria ela. Porém imaginemos uma biblioteca como o
Eloquent, a mesma função de salvar é utilizada sempre, do mesmo local de um mesmo arquivo. Isso é orientação a objetos. Em uma forma procedural, seria feito de uma forma 
a qual seria possível que cada vez que precisasse ser salva uma parte do código em um banco de dados, partes do salvar do Eloquent seriam utilizadas em cada uma das vezes. 

Assim, não só reduzimos o número de modificações a serem feitas, o número de linhas de código, mas, também, concentrando as coisas em um único lugar, podemos ter maior segurança ao utilizar
uma função. Imagine ter que refazer a mesma função vinte, trinta, até quarenta vezes. A possibilidade de uma delas dar errado é grande. As vezes esse lugar não é tão utilizado, mas imagine
que um recém contratado da empresa, ou alguém que desconhece o fato dessa função não funcionar, copia isso para outra parte. O efeito cascata pode ser grande e devastador.
Realizando uma POO, podemos confiar que, se todos os locais usam e todos os locais funcionam, algo passado pela nova chamada à função é o que está errado. 

Outra grande vantagem da POO é a não necessidade de passarmos o tanto de variáveis como é passado na função `removeObjeto`. Veja o exemplo, lá são passados: id, codigo do objeto, e duas variaveis
aleatórias para nosso exemplo. Em uma aplicação real, dezenas de variáveis poderiam ser passadas, mas, para que fazer isso quando podemos tratar dessas variáveis como propriedades? Podemos fazer algo como:
```php
class Remocao {

  /*
   * @var int
   *
   */
  public $id; 
 
  /*
   * @var int
   *
   */
  public $codigoObjeto; 
  
  /*
   * @var string
   *
   */
  public $varRandom1; 
  
   /*
    * @var EntityAleatoria
    *
    */
  public $varRandom2; 
  
  public function construct() {
  $id = (valor do id, deve ser iteravel), 
  $codigoObjeto = (valor do codigo, deve ser iteravel), 
  $variavelAleatoria1 = 'string', 
  $variavelAleatoria2 = $objeto,
  }
  
  public function removeObjeto() {
        $this->repository->removeid, $codigoObjeto, $variavelAleatoria1, $variavelAleatoria2);
  }
}
```

Claro que outras camadas teriam que ser adicionadas para que esse exemplo realmente se tornasse um código real, porém, muda muito, especialmente por envolver 
o código com uma outra camada de segurança utilizando valores como `protected` ou `private` no lugar do `public`, podendo ser chamado apenas dentro da função ou
com métodos especificos para a chamada. Quanto maior a complexidade, maior o código, dentro do `construct()` talvez todas as variáveis tenham de ser chamadas, porém,
elas são chamadas de dentro do próprio arquivo e são declaradas apenas uma vez. Fazendo com que variáveis que seriam chamadas multiplas vezes se criem em um arquivo só e possam ser 
reutilizadas, uma grande harmonia de objetos. 

