# Procurando Partes do Código

## Objetivo

Demonstrar a forma mais fácil de transitar pelos caminhos do código e dos arquivos do projeto oneticket.com.br
Há duas opções de o fazer, usando a URL ou pesquisando a página no próprio VS Code.

## Usando o VS Code

### Usando Atalhos

Muitos devs já sabem dessa opção, mas para transitar para um arquivo específico,    digamos o arquivo <kbd>Filme.php</kbd>, você pode utilizar o comando <kbd>ctrl + P</kbd> e digitando o nome do arquivo.

Haverão vários arquivos, entretanto, se você sabe onde procurar o arquivo, se já tem mais experiência com o código, essa é uma forma rápida e prática de fazer transições rápidas entre partes do código.

<a id = "header"></a>

### Usando o <kbd>ctrl</kbd>

Outra opção dentro do VS Code é utilizar a extensão _PHP Intelephense_ e apertar <kbd>ctrl</kbd> e clicar em alguma função, _Composer_, entre outros e ele lhe leverá diretamente a onde aquele foi criado.

Sabendo utilizar isso de forma correta, pode-se ter uma grande facilidade de transitar entre telas que estão relacionadas entre si e não necessariamente são sobre a mesma coisa.


## Encontrando Tela do Website

A forma mais garantida, entretanto, mais chata de se procurar uma parte do código é pela URl. Tomemos por exemplo a URL: [https://oneticket.com.br/eventos/detalhes/](https://oneticket.com.br/eventos/detalhes/). Temos um _evento_ e dentro dele uma subpasta _detalhes_, correto?

Entre em `src`, depois em `Presentation` (onde estarão quase todas as telas e API's) e, sendo a aplicação o site da [One Ticket](oneticket.com.br), entre em `Website` e procure o arquivo `routes.php`.

### Procurando o Correto

Agora, dentro do arquivo <kbd>**routes.php**</kbd> encontrado na `Presentation` (e é importante essa definições de onde é encontrado pois haverão mais arquivos com o mesmo nome, então decore onde está esse arquivo para não se perder), procure a primeira parte de sua URL, no exemplo, procuraremos a parte que fala de **Eventos**. Achar-se-á o seguinte código:

```php
$app->group('/eventos', function () use ($app) {
    include __DIR__ . '/Areas/Eventos/routes.php';
});
```

Vamos destrinchar isso agora.

Veja que o */eventos* é a principal parte e está sendo posta dentro do group. O app então inclui esse arquivo no `__DIR__` que significa que será inserto o arquivo seguinte no mesmo diretório que o arquivo atual está, sendo o arquivo atual o <kbd>**routes.php**</kbd> e ele estando dentro da *Presentation*, o novo arquivo incluso será adicionado em *Presentation*. Também é válido notar que, após o `__DIR__` temos o <kbd>'/Areas/'</kbd>, o qual será uma pasta criada, neste caso, dentro do `__DIR__` atual e, da mesma forma, dentro dele será criado outra pasta **Eventos** e depois será criado o arquivo em si, denominado, novamente, <kbd>**routes.php**</kbd>.

Perfeito! Agora temos o arquivo desejado. Para procurar arquivos que combinam com este, pode-se usar o comando [ctrl](#header).
