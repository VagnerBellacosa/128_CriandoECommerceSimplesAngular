# Implementando serviços com AngularJS

## Veja nesse artigo como usar todo o poder do AngularJS para criar serviços variados em suas aplicações web.

- O que é o AngularJS

O **AngularJS é um framework open-source de desenvolvimento front-end que possibilita o desenvolvimento de aplicações web**, com foco em simplificar tanto a codificação quanto o processo de teste. Além disso, é possível integrá-lo com bibliotecas famosas como o [Bootstrap](https://www.devmedia.com.br/curso/bootstrap-trabalhando-com-design-responsivo/407), D3.js e o Apache [Cordova](https://www.devmedia.com.br/guia/cordova/38321) (ou PhoneGap), ajudando a acelerar esse tipo de codificação como nunca antes tivemos.

O **AngularJS também permite aos desenvolvedores web fazer uso da linguagem de marcação HTML** para definir associações de dados, validações, além de *response handlers* para lidar com as ações do usuário em um formato declarativo que também contribui para essa mesma aceleração. Com tudo isso em conjunto, a maior consequência é, de longe, o crescimento e enriquecimento das aplicações cada vez mais ricas em funcionalidades e recursos.

### Atualidades do Angular

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZSJBCtMMMrs" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen="" style="outline: none; -webkit-tap-highlight-color: transparent; max-width: 100%; margin: auto; height: 455.062px; width: 809px;"></iframe>

Relacionado: [Curso de introdução ao Angular](https://www.devmedia.com.br/curso/o-que-e-angular/1918)

Saber como arquitetar apropriadamente suas aplicações **AngularJS há medida que elas crescem é algo tão importante quanto definir um bom modelo em um ciclo de vida** de um software para linguagens como Java, C# ou quaisquer outros modelos server side de hoje.

[Saiba maisSérie **Angular, API RESTful e Banco de Dados**](https://www.devmedia.com.br/angular/)

Neste artigo, trataremos de expor algumas formas de bem arquitetar e construir **serviços no AngularJS** que, por sua vez, endereçam as mais usadas e importantes camadas de uma aplicação desse tipo: autenticação, mensageria, logging, acesso a dados, além da camada de acesso às regras da lógica de negócio que é requisito obrigatório para qualquer aplicação que tenha um nível de complexidade moderado. Além disso, veremos também rapidamente como integrar serviços externos do próprio framework com bibliotecas de terceiros dentro de suas aplicações de tal forma que o **AngularJS possa tomar vantagem das mesmas com pouco esforço**, enquanto você analisa detalhadamente a forma como o framework realiza tais integrações.

### A necessidade de serviços

Em tempos onde muito se discute acerca do MVC no lado front-end, bem como das responsabilidades desse padrão no *client side*, inúmeras vertentes da comunidade de desenvolvimento front-end, muitas vezes em contraversão às que apoiam e suportam o lado back-end, dizem que a utilização de camadas que fornecem acesso direto a serviços é algo totalmente desnecessário e que foge às responsabilidades da mesma, devendo ser amparadas, portanto, pelas camadas que atuam no servidor da arquitetura. Para entender a contrapartida dessa discussão, é necessário que antes respondamos a algumas questões inerentes a tal dúvida: Por que serviços são realmente necessários no front-end? Como eles apoiam a sua aplicação? Quais são suas responsabilidades na aplicação de uma forma geral?

A primeira sentença a ser analisada diz que “os serviços são a base de tudo”. Isto é, eles fornecem funcionalidades de forma transversal, solicitam e manipulam dados, se integram com outros serviços externos, e incorporam lógica de negócio, tudo isso de uma forma tão simples quanto um objeto JSON possa parecer (que é inclusive o tipo de dado mais usado para representá-los).

Em alusão a uma situação um pouco mais lúdica, os serviços funcionam como a fundação de um prédio. Obviamente um prédio pode ser construído sem a necessidade de uma fundação, porém ele não irá durar tanto quanto duraria se a tivesse. Da mesma forma, sem serviços em uma aplicação, a mesma logo se tornará tão pesada que não se aguentará por muito tempo. A **Figura 1** nos mostra uma representação visual dos componentes do AngularJS e suas interações.

![Representação do modelo de componentes do AngularJS e interações](https://arquivo.devmedia.com.br/REVISTAS/front_end/imagens/edicao6/3/image001.jpg)**Figura 1.** Representação do modelo de componentes do AngularJS e interações.

Observe que, conforme discussões se abrangem, maior é a necessidade de entender como ambos os padrões (MVC + Serviços) interagem e se auto ajudam, quando em conjunto.

### A necessidade de boas práticas

Quando uma equipe de desenvolvimento se depara com um projeto novo, uma das primeiras e mais importantes ações é escolher um framework para facilitar a produtividade do projeto como um todo. Aliado a essa escolha, o arquiteto ou alguém com mais experiência terá o desafio de entender como o mesmo funciona e, mais importante que isso, como aplicar as boas práticas de programação a este framework.

As boas práticas são como guias que nos ajudam a entender o melhor jeito de usar aquele framework, assim como estruturar a sua aplicação de forma a deixá-la manutenível, testável e reusável.

O desenvolvimento utilizando módulos leva em consideração a unidade na aplicação como um todo. Isso quer dizer que cada componente deve ter sempre uma única e específica responsabilidade, caso contrário teremos uma discrepância na implementação e o modelo tenderá a se tornar cada vez mais complexo de manter.

### Desenhando serviços

Antes de iniciarmos a implementação de fato dos nossos serviços, é preciso que o leitor tenha em mente algumas regras essenciais para a criação correta dos mesmos. Vejamos:

· Antes de iniciar qualquer serviço, **tome um tempo pensando sobre ele**. Quais serão as suas funcionalidades (faça uma lista delas, no papel mesmo, se achar melhor)? Como criarei este(s) serviço(s) de modo que eu possa facilmente modificá-lo(s) no futuro, mantendo-o(s) sempre testável(eis) e manutenível(eis)?

· **Meça duas vezes, corte apenas uma**. Isso serve para te ensinar a não se apressar quando for criar serviços e/ou quaisquer implementações. Às vezes é melhor perder um bom tempo planejando direito o que você vai desenvolver, em vez de atropelar o desenvolvimento ágil e precisar refazer no futuro.

· **Foque no desenvolvedor**, e não em você mesmo. Isso quer dizer que, quando construir um serviço, pense em quem irá usá-lo. Muitas vezes esquecemos dessa premissa por não estarmos lidando com algo que será acessado diretamente por um usuário, pois tudo será abstraído pela “figura do desenvolvedor”. Coloque-se no lugar dele, e pergunte-se se, sendo você o desenvolvedor consumidor, você entenderia o serviço que criou e disponibilizou.

· Faça apenas **o que o nome do seu serviço manda fazer**. Essa prática já é muito comum entre codificadores para nomes de métodos, por exemplo. Se o seu método se chama *cadastrarCliente()*, adivinhe qual deve ser a única coisa que ele faz? O mesmo vale para os serviços.

· **Mantenha o mais usável possível**. Isso quer dizer que, se o seu serviço foi criado por alguma ferramenta de CRUD, por exemplo, que automaticamente gerou métodos de *add(), remover(), alterar() e pesquisar()*, mas no seu serviço só será usado o método de pesquisa, então remova os demais. Deixe-o simples e direto.

· **Documente a sua interface de serviço.** Isso será útil não só para outros desenvolvedores que venham a encarar o seu código no futuro, mas principalmente para você mesmo. Afinal, você não é obrigado a decorar tudo o que codifica. Existem inúmeras ferramentas que te ajudam nisso: JSDoc, YUIDoc, Ext Doc, ou algum plugin que a sua IDE disponibilize e que você se sinta à vontade para usar.

### Instalando o AngularJS

Para trabalhar com o **AngularJS a única coisa que você precisará fazer é importar o seu arquivo JavaScript** para o seu projeto, seja através do download direto ou do uso da interface CDN que o mesmo disponibilizará de forma gratuita e online. Para os objetivos deste artigo, faremos sempre uso da segunda opção pela simplicidade da mesma. Na seção **Links** deste artigo você encontrará a URL da página de download oficial do projeto, onde poderá encontrar todas as referências necessárias. Ademais, não será objeto deste instruir o leitor acerca de conceitos básicos do AngularJS, visto que isso fugiria ao foco que é apresentar como criar serviços com a tecnologia.

No momento de escrita deste artigo, a versão mais **recente do AngularJS era a 1.3.14**, mas o leitor poderá usar versões anteriores sem problemas.

As bases de uma aplicação feita sob os **pilares do AngularJS são: \**comportamento\** e \**interação\** em conjunto com a \**apresentação\****. De início, esse tipo de conceito pode ser confuso, especialmente se você estiver acostumado a lidar com outros frameworks onde tais pilares são distintos e funcionam de forma independente. Vejamos o exemplo representado na **Listagem 1**.

**Listagem 1**. Exemplo básico de uso do AngularJS.



```
<!doctype html>
<html ng-app>
  <head>
     <meta charset="utf-8">
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
  </head>
  <body>
    <div style='padding: 3%'>
      <input type="text" ng-model="meuNome" placeholder="Digite um nome aqui..." style='margin-bottom: 20px'>
      <h1>Olá, {{ meuNome }}!</h1>
    </div>
  </body>
</html>
```



Neste exemplo temos basicamente a importação do arquivo js sendo feita dentro da tag de cabeçalho HTML, e um campo de input de formulário seguido de um cabeçalho de texto h1 para exibição do resultado final. No mesmo exemplo, é possível ver a associação de dados bidirecionais sendo feita sem muito trabalho. Essa associação significa que se você mudar os dados exibidos no back-end da aplicação, tais mudanças surtirão efeito no lado front-end automaticamente, e vice-versa.

Perceba também que, no exemplo, temos três operadores incomuns para a HTML, a saber:

· **ng-app**, o mais importante atributo na nossa página, que será responsável por iniciar o processo do AngularJS;

· **ng-model=”meuNome”,** que se responsabilizará por interligar o campo de input ao elemento h1 de resultado, automaticamente, exibindo o valor que estiver em um respectivamente no outro;

· **{{meuNome}},** o mesmo que o item anterior, só que no processo inverso, de exibição.

A execução deste conteúdo no browser resultará em algo semelhante ao que temos na **Figura 2**.

**![Resultado da execução do exemplo AngularJS](https://arquivo.devmedia.com.br/REVISTAS/front_end/imagens/edicao6/3/image002.jpg)**



**Figura 2.** Resultado da execução do exemplo AngularJS.



Perceba que essa implementação é demasiadamente simples se comparada ao código necessário para criá-la em outras tecnologias, como JSP, JSF ou ASP.NET, por exemplo. O **item 1** marca a página quando iniciada, nada aconteceu ainda; enquanto o **item 2** demarca o final do teste, quando o usuário preenche o campo que tem sua respectiva label atualizada automaticamente. Para incutir quaisquer efeitos de estilo, os arquivos de CSS do Bootstrap ou de um framework de sua preferência podem ser usados.

### A necessidade de testes

O AngularJS foi totalmente projetado com o conceito de testabilidade em mente. Evidentemente, outro conceito, o de *Depency Injection* (ou Injeção de Dependências), anda de mãos dadas com ele. A injeção de dependências permite que você escreva códigos que sejam extremamente desacoplados dos serviços aos quais os mesmos dependem. Consequentemente, isso nos permite criar códigos que obedeçam à famosa **Lei de Demeter**, que constitui uma boa prática quando da escrita de códigos de teste. De uma forma geral, essa lei diz que cada unidade de código deve ter conhecimento limitado sobre as demais.

Em outras palavras, jamais chame objetos encadeados nos seus métodos sob pena de aumentar consideravelmente a complexidade do seu código, tornando-o também mais difícil de ser testado. Em vez disso, passe como parâmetros os objetos com os quais precisa interagir. Veja na **Listagem 2** um exemplo fiel da chamada encadeada de objetos.

**Listagem 2**. Exemplo de função com objetos encadeados.



```
$scope.getNome = function(autenticacao) {
    if (autenticacao && autenticacao.clienteAtual) {
       return autenticacao.clienteAtual.primeiroNome + ' ' +  autenticacao.clienteAtual.ultimoNome;
    }
    return '';
},
```



Observe que o código aceita um objeto chamado “autenticacao”, bem como a forma como ele certifica que ambos os objetos **autenticacao** e **clienteAtual** são válidos antes de acessar as propriedades do objeto clienteAtual para retornar o nome do cliente.

Testar o referido código com objetos mock é algo muito trabalhoso, neste exemplo. Você não somente terá de “mockar” todos os métodos chamados no objeto autenticacao, como também precisará fazer o mesmo para todos os métodos chamados no objeto clienteAtual, tornando o seu código muito maior do que ele necessita ser.

Por outro lado, se você seguir a mesma implementação, porém fazendo uso da Lei de Demeter, poderá simplificar o seu código consideravelmente. Vejamos na **Listagem 3** como atingir esse objetivo.

**Listagem 3**. Código simplificado pela Lei de Demeter.



```
$scope.getNome = function (cliente) {
     if (cliente) {
        return cliente.primeiroNome + ' ' + cliente.ultimoNome;
     }
     return '';
},
```



Agora, nosso código está apenas validando o objeto que invoca métodos no mesmo, ao contrário de verificar o objeto que deveria encapsulá-lo. Isso resultado em um código muito mais simplificado, uma vez que tivemos de mockar somente os métodos atrelados ao objeto **cliente**.

Um outro princípio muito importante para a testabilidade do seu código se caracteriza pelo uso das injeções de dependências: sempre passe todas as dependências requeridas para o seu serviço no momento de criação da função, e jamais use o serviço *$injector* para recuperar dependências, a menos que não haja outra maneira de injetar um serviço obrigatório. Apesar de ser permitido invocar uma instância de um serviço através desse operador, você nunca poderá testar tal código, isso porque você não poderá garantir que mockou todos os serviços que o seu código invocará.

Ao passar como parâmetros todas as dependências obrigatórias que o seu serviço irá precisar, você terá um *road map* de todos os que precisará mockar, além de ser possível então determinar facilmente quais métodos são chamados por quais serviços.

Dando continuidade, outro ponto para se ter em mente se refere a limitar seus métodos de construtores para somente receber atribuições de campos e definições de funções. Não efetue chamadas a serviços externos para inicializar dados. Em vez disso, adicione esse tipo de código dentro de métodos de inicialização e/ou configuração que devem ser chamados depois que a instância de seu serviço tiver sido criada. Isso porque ao fazer esse tipo de chamada explícita, você estará dificultando futuros testes e debugs, uma vez que os mesmos serviços externos podem apresentar falhas durante o teste, o que pode te confundir entre qual dos serviços está apresentando erro.

### Estruturando o serviço em código

Antes de começar a codificar o seu serviço, você precisa pensar em como não poluir o namespace global e somente expor métodos e propriedades que você pretenda usar para os consumidores quando eles interagirem com o seu serviço.

A razão para não poluir o namespace global é que precisamos proteger o código de eventuais colisões de nomenclaturas que podem ocorrer com outros scripts carregados na página, além de evitar que seu código sobrescreva algum outro código de script.

O jeito mais fácil de prevenir isso é criando um IIFE (*Immediately-Invoked Function Expression*, vide **BOX 1**) que você poderá usar para definir o seu módulo e serviço (**Listagem 4**).

**Listagem 4**. Exemplo básico de uso do IIFE.



```
(function () {
       'use strict';
       // definições de módulo aqui
       // definições de serviço aqui
  })();
```



Não somente pode este padrão ser usado para seus serviços, como também para todos os seus controladores e diretrizes. A única vez que é aconselhável não usar esse padrão é se você estiver usando uma ferramenta de construção que concatena seu código em um único arquivo e encapsula-o em uma *closure* (que ocorre quando temos uma função declarada dentro do corpo de outra função, e a função interior referencia variáveis locais da função exterior).

A próxima coisa a se pensar quando escrever o seu serviço é expor somente métodos e propriedades que você pretenda que os usuários de seu serviço tenham acesso. A maneira mais fácil de fazer isso é usando o padrão *Christian Heilmann's Revealing Module Pattern* para definir seu serviço (veja na seção **Links** uma referência para o site do padrão).

A vantagem de utilizar esse padrão é que você não tem que usar o nome do objeto principal para chamar métodos ou variáveis de acesso, além de ter a capacidade para expor apenas os métodos e variáveis para o mundo exterior que você sente que precisam estar acessíveis.



**BOX 1.** Immediately-Invoked Function Expression (IIFE)



O IIFE (Expressão de Função Imediatamente Invocada, em português literal) é um padrão de design JavaScript comum usado pela maioria das bibliotecas populares (jQuery, Backbone.js, Modernizr, etc.) para colocar todo o código da mesma em um escopo local. É apenas uma função anônima que é encapsulada dentro de um conjunto de parênteses e invocada imediatamente. Um IIFE padrão geralmente é implementado assim: *(function() { // Código }());*





O exemplo da **Listagem 5** define um serviço de mensageria para publicação/subscrição usando o Revealing Module Pattern. A função **messaging_service** cria uma closure onde definimos os vários métodos de serviço e quaisquer variáveis internas que precisamos para armazenar o estado do mesmo. Na parte inferior da definição da função, retornarmos um objeto que inclui apenas os métodos que queremos tornar visíveis para os consumidores do serviço.

**Listagem 5**. Exemplo de função para serviço de mensageria.



```
01 (function () {
02   'use strict';
03   // Define a fábrica no módulo.
04   // Injeta as dependências.
05   // Aponta para a função de definição da fábrica.
06   angular.module('brew-everywhere').factory('messaging_service', [messaging_service]);
07
08   function messaging_service() {
09
10   //#region Propriedades Internas
11   var cache = {};
12   //#endregion
13
14   //#region Métodos Internos
15   function publicar(topico, args) {
16     cache[topico] && angular.forEach(cache[topico],
17           function (callback) {
18           callback.apply(null, args || []);
19     });
20   }
21
22   function subscrever(topico, callback) {
23     if (!cache[topico]) {
24           cache[topico] = [];
25     }
26     cache[topico].push(callback);
27     return [topico, callback];
28   }
29
30   function dessubscrever(handle) {
31     var t = handle[0];
32     cache[t] && angular.forEach(cache[t], function (idx) {
33           if (this == handle[1]) {
34                  cache[t].splice(idx, 1);
35           }
36     });
37   }
38   //#endregion
39
40   // Define as funções e propriedades para revelar.
41   var servico = {
42     publicar: publicar,
43     subscrever: subscrever,
44     dessubscrever: dessubscrever
45   };
46
47   return servico;
48   }
49 })();
```



A listagem está auto comentada, porém vejamos algumas observações importantes:

· Na linha 2 vemos o modelo de implementação de serviços padrão que comentamos antes. Este deverá ser seguido sempre que um novo serviço necessitar ser criado.

· Na linha 6 é possível observar o uso da função **module()** do AngularJS, que se encarrega de injetar o módulo requerido para uso posterior. Na mesma linha estamos criando uma factory de mensagerias que será útil para fabricar novos objetos sempre que necessários.

· Os métodos de publicação (linha 15), subscrição (linha 22) e de-subscrição (linha 30) fazem uso do array **cache** que será útil para lidar com o salvamento de informações temporárias, otimizando o tempo de acesso às mesmas e aumentando, assim, a performance da aplicação.

· No final da implementação, a partir da linha 41, simplesmente adicionamos os novos métodos de serviço ao objeto que os guardará como referências: a variável **servico**, que será também retornada como resultado final.

### Configurando o serviço

O método **provider** dos módulos do AngularJS possibilita a criação de um serviço com configurações básicas de métodos que os consumidores possam invocar sem problemas (em um método **config**, por exemplo).

Através desse método, podemos definir um serviço de logging, por exemplo, de forma extremamente mais simples. Vejamos a **Listagem 6**.

**Listagem 6**. Exemplo de módulo para serviço de logging.



```
01 angular.module('MinhaApp', ['logging']).config(function(provedorLogging){
02     // Inicializa o serviço de logging
03     provedorLogging.init();
04     // Configura o nível do log
05     provedorLogging.setLogLevel(log4javascript.Level.ALL);
06     // Cria e Add um appender ao logger
07     var appender = new log4javascript.PopUpAppender();
08     provedorLogging.setAppender(appender);
09 });
```



Esse tipo de estrutura é muito semelhante à forma como configuramos logs em outros ambientes, tais como Java, .Net, etc. Até mesmo o uso dos objetos JavaScript em alusão aos que usamos na biblioteca Log4J do Java se equiparam, o mesmo para appenders, níveis de logs, etc.

No entanto, você não precisa sempre usar o método provider para permitir que os seus serviços sejam configurados. É possível usar ambos os métodos service e factory para definir o seu serviço e fornecer métodos de configuração que possam ser chamados diretamente do método de execução do módulo: **run**, que, por sua vez, executa após o bootstrap da sua aplicação. A única coisa que você precisa garantir é que seu serviço siga as práticas de projeto que discutimos anteriormente e não tente chamar quaisquer serviços externos assim que for instanciado.

Não importa como você cria seus serviços, ao fornecer funcionalidade para configurá-los, você faz com que os mesmos sejam mais flexíveis, mais fáceis de usar, além de reduzir a complexidade necessária para incluí-los em uma aplicação.

### Gerenciando preocupações cross-cuting

Um bom design em uma aplicação usa camadas para separar áreas de responsabilidade. Se bem feito, cada camada tem uma única responsabilidade e se interliga com as outras camadas usando uma interface bem definida.

As camadas mais populares que você vai ver incluídas em um aplicativo são: dados, lógica de negócios e interface do usuário. No entanto, existem serviços que atravessam todas as outras camadas; aqueles que lidam com preocupações *cross-cuting* (transversais), tais como mensageria, logs, validação de dados, *caching*, internacionalização e segurança.

Comunicar-se com os consumidores do seu serviço se torna muito importante quando você tem métodos que são de longa duração ou que façam chamadas assíncronas AJAX do front-end para um servidor. Obviamente, você não vai querer bloquear a execução do seu aplicativo enquanto o seu serviço está processando ou esperando uma chamada AJAX voltar. Logo, a melhor maneira de lidar com todos esses métodos é executando-os de forma assíncrona.

Existem várias saídas que você pode usar para lidar com tais métodos:

· Solicitar ao consumidor o fornecimento de uma função de retorno que o seu método de serviço irá executar após a conclusão;

· Devolver uma “promise (retorno promessa)” que garante que o seu método de serviço será executado após a conclusão;

· Ou usar um padrão de design de mensagens para notificar o consumidor uma vez que seu método de serviço estiver concluído.

Embora as **funções de callback** e as **promises** funcionem muito bem para notificar um único consumidor sempre que seu método de serviço tenha sido concluído, elas não funcionam direito quando você tem vários consumidores que precisam saber quando os métodos do seu serviço foram finalizados ou quando os dados geridos pelo mesmo foram atualizados.

Isso ocorre especialmente quando você tem várias views visíveis ao mesmo tempo e cada uma precisa ser notificada quando os dados do seu serviço mudam. Um bom exemplo é o carrinho de compras em um aplicativo de e-commerce. À medida que o usuário adiciona itens ao carrinho, o mesmo precisa atualizar a exibição dos conteúdos, juntamente com outros serviços que possam mostrar os custos de transporte, total de compras feitas, e assim por diante.

Para lidar com tais situações, você precisa usar um padrão de projeto *publish/subscribe* tanto para notificar consumidores quando métodos de longa duração completarem, quanto para notificar todas as views do seu aplicativo quando os dados do seu serviço mudarem.

Uma coisa que você deve sempre ter em mente quando da utilização de funções de cabllback para mensageria é que é possível diminuir o desempenho do aplicativo se seus manipuladores de callback publicarem outras mensagens como parte do seu processamento. Então, o melhor é usar o serviço *$timeout* para moldar o código que publica mensagens, uma vez que o manipulador de cabllbacks pode retornar o mais rápido possível e não afetar o desempenho.

O código demostrado pela **Listagem 7** representa a criação de um serviço de mensageria usado pelo aplicativo de exemplo.

**Listagem 7**. Exemplo de módulo para serviço de mensageria.



```
01 angular.module('brew-everywhere').factory('messaging', function () {
02     var cache = {};
03
04     var subscrever = function (topico, callback) {
05           if (!cache[topico]) {
06                  cache[topico] = [];
07           }
08           cache[topico].push(callback);
09           return [topico, callback];
10     };
11
12     var publicar = function (topico, args) {
13           cache[topico] && angular.forEach(cache[topico],
14           function (callback) {
15                  callback.apply(null, args || []);
16           });
17     };
18
19     var dessubscrever = function (handle) {
20           var t = handle[0];
21           if (cache[t]) {
22                  for(var x = 0; x < cache[t].length; x++) {
23                         if (cache[t][x] === handle[1]) {
24                                cache[t].splice(x, 1);
25                         }
26                  }
27           }
28     };
29
30     var service = {
31           publicar: publicar,
32           subscrever: subscrever,
33           dessubscrever: dessubscrever
34     };
35     return service;
36 });
```



Inicialmente, definimos uma variável interna chamada **cache** que será usada para armazenar todos os assinantes para cada uma das mensagens e para os seus métodos de callback. Dentre os três métodos definidos, temos:

· O método **subscrever** recebe uma string de nome topico e uma função de callback para invocar quando o mesmo for publicado. Em seguida, ele checa se o cache contém uma propriedade com o nome do tópico; se não existir, uma nova propriedade é adicionada ao objeto e uma matriz é criada e atribuída à mesma. Em seguida, a função de retorno é inserida na matriz. Finalmente, um identificador é retornado para que o assinante possa utilizar quando desejar cancelar a subscrição.

· O método **publicar** recebe a mesma string topico e um array de argumentos que pode ser passado para a callback que assina o tópico em questão. O método verifica se o objeto de cache contém uma propriedade com o nome do tópico. Se assim for, ele itera através de cada item na matriz e chama a função de callback com os argumentos passados.

· O método **dessubscrever** recebe o identificador retornado pelo método subscrever e remove a função de callback associada com o tópico. O método primeiro verifica se o objeto de cache contém uma propriedade com o nome do tópico, e em caso afirmativo, ele itera através de cada item da matriz até encontrar um callback que coincida com o callback contido no identificador e, então, remove-o da matriz.

Finalmente, o serviço retorna um objeto com apenas os métodos que queremos tornar públicos para os consumidores, seguindo o Revealing Module Pattern.

Para fazer uso desse mesmo serviço, o consumidor precisará incluir um outro serviço, o de *messaging*, como uma dependência e então subscrever a um ou mais tópicos que o mesmo tenha interesse em ser notificado sempre que novos eventos acontecerem. Para exemplificar essa situação, consideremos um controller simples (**Listagem 8**) que usa esse mesmo serviço de mensageria para autenticar um usuário e, assim, faz uso direto do serviço que acabamos de criar.

**Listagem 8**. Exemplo de módulo para serviço de autenticação.



```
01 angular.module('brew-everywhere').controller('LoginCtrl', function($scope, messaging, events){
02     //#region Modelos Internos
03     $scope.usuario = '';
04     $scope.senha = '';
05     $scope.usuarioAtual = {};
06     $scope.usuarioAutenticado = null;
07     //#endregion Modelos Internos
08
09     //#region Message Handlers
10     $scope.autenticacaoUsusarioCompleta = function(usuario) {
11     $scope.usuarioAtual = usuario;
12     }
13     $scope.usuarioAutenticado = messaging.subscrever(
14           events.message._AUTHENTICATE_USER_COMPLETE_,
15           $scope.autenticacaoUsusarioCompleta);
16     //#endregion Message Handlers
17
18     //#region View Handlers
19     $scope.$on('$destroy', function(){
20           messaging.dessubscrever($scope.usuarioAutenticado);
21     });
22     $scope.onLogin = function() {
23           messaging.publicar(event.message._AUTHENTICATE_USER_, [$scope.usuario, $scope.senha]);
24     }
25     //#endregion View Handlers
26 });
```



O view controller **LoginCtrl** recebe o serviço messaging e o serviço de eventos como dependências. O serviço de mensageria é a implementação do serviço publish/service que vimos antes, já o serviço **events** é nada mais que um conjunto de constantes que define as várias mensagens que são usadas pela aplicação.

O controller então define um gerenciador de mensagens chamado autenticacaoUsusarioCompleta (linha 10) que foi registrado pelo serviço de mensageria com o tópico *“_AUTHENTICATE_USER_COMPLETE_”*. Em seguida, temos a definição do método **onLogin** (linha 22) que é usado como um gerenciador de ng-click (lembre-se do exemplo que vimos sobre o AngulaJS e seus componentes) para logar o usuário através da publicação da mensagem “_AUTHENTICATE_USER_”, tendo os dados de login e senha como argumentos enviados.

Quando o gerenciador de ng-click do AngularJS é executado, ele automaticamente publica a mensagem e então o controller espera até que o serviço responda com a mensagem de completitude, que, por sua vez, receberá o objeto passado dentro do callback atribuindo a ele o valor da variável **usuarioAtual**.

O leitor talvez se pergunte onde seria feito o tratamento de erros, por exemplo, que constitui requisito básico e essencial para quaisquer tipos de serviços. Este deve ser feito de fora do controller por outros serviços. No nosso exemplo, se a mensagem de completitude nunca chegar, o controller simplesmente não faz nada.

Ademais, o controller também faz uso do método *$scope.$on* que servirá para assistir à mensagem *$destroy* que será enviada quando o controller for destruído, assim o mesmo poderá cancelar a subscrição sobre quaisquer mensagens que tenham sido inscritas antes. Isso é muito importante para que o serviço de mensageria não tente chamar uma função de callback que, na verdade, não existe.

### Gerenciando notificações de usuário

Após o término da construção da camada de mensageria, você pode começar a incluir novas camadas, como a de gerenciamento de notificações de usuário, por exemplo.

Continuemos nossa implementação construindo uma diretiva que agirá diretamente no nosso serviço de mensageria para exibir um GIF animado indicando que o nosso programa está ocupado com alguma tarefa. Veja na **Listagem 9** o código que precisaremos para isso.

**Listagem 9**. Incluindo diretiva de carregamento temporário.



```
01 angular.module('brew-everywhere').directive('carregando', function(messaging, events) {
02     return {
03           restrict: 'E',
04           template: '<div class="row"><img src="images/ajax-loader.gif" alt="Carregando, favor aguardar..." /></div>',
05           link: function(scope, element) {
06                  element.hide();
07                  var startRequestHandler = function () {
08                         // recebe a notificação de início, mostra o elemento
09                         element.show();
10                  };
11                  var endRequestHandler = function() {
12                         // recebe a notificação de fim, esconde o elemento
13                         element.hide();
14                  };
15                  scope.startHandle = messaging.subscribe(
16                         events.message._SERVER_REQUEST_STARTED_,
17                         startRequestHandler);
18                  scope.endHandle = messaging.subscribe(
19                         events.message._SERVER_REQUEST_ENDED_,
20                         endRequestHandler);
21                  scope.$on('$destroy', function() {
22                         messaging.unsubscribe(scope.startHandle);
23                         messaging.unsubscribe(scope.endHandle);
24                  });
25           }
26     };
27 });
```



A diretiva “carregando” basicamente exibe e esconde o elemento que está atrelado a ela, baseada em duas mensagens: “_SERVER_REQUEST_STARTED_” e “_SERVER_REQUEST_ENDED_”. O template para a diretiva é nada mais que uma div HTML que encapsula a tag de imagem, que, por sua vez, constitui uma animação (um gif).

Agora, sempre que quisermos indicar que a aplicação se encontra ocupada, podemos publicar a mensagem de start para exibir o item de carregamento, e uma vez completada, podemos chamar a mensagem de end para escondê-lo.

Outro bom exemplo de uso do serviço de notificação de usuário é a implementação de uma diretiva de lista de notificações simples que funciona com dois serviços juntos para exibir erros e mensagens de alerta para o usuário. Os serviços de erros e notificações são muito similares, exceto pelo fato de que cada um lida com mensagens diferentes. Através deles é possível determinar como certas mensagens são exibidas, estabelecendo pilares de controle sobre as mesmas.

Suponha que você deseja ter mensagens de erro sendo exibidas em um diálogo do tipo pop-up em vez de em uma lista fixa no corpo da página; uma vez que as mensagens de erro são lançadas por um serviço a parte, você pode facilmente mudar que mensagem o serviço de erros deve publicar sempre que ele receber uma nova mensagem.

Vejamos na **Listagem 10** um exemplo básico de serviço de erros que gerencia tal subscrição.

**Listagem 10**. Exemplo básico de serviço de notificações de erro.



```
01 angular.module('brew-everywhere').factory('erros',function($timeout, messaging, events) {
02     var msgErros = [];
03     var addHandlerMsgErros = function(msg, tipo){
04            if(!msgErros){
05                  msgErros = [];
06           }
07           msgErros.push({tipo: tipo, msg: msg});
08           $timeout(function() {
09                  messaging.publicar(events.message._ERROR_MESSAGES_UPDATED_, msgErros);
10           }, 0);
11     };
12
13     messaging.subscrever(events.message._ADD_ERROR_MESSAGE_, addHandlerMsgErros);
14     var limparMsgErrosHandler = function() {
15           msgErros = [];
16     };
17     messaging.subscrever(events.message._CLEAR_ERROR_MESSAGES_, limparMsgErrosHandler);
18     var init = function(){
19           msgErros = [];
20     };
21     var erros = {
22           init: init
23     };
24     return erros;
25 }).run(function(erros){
26     erros.init();
27 });
```



Esse serviço tem um array interno que é usado para salvar as mensagens de erro à medida que elas são recebidas pelo mesmo. O gerenciador de mensagens **addHandlerMsgErros** faz uso do serviço $timeout para permitir que o método retorne imediatamente e, então, publica a mensagem “_ERROR_MESSAGES_UPDATED_” com o conteúdo do array **msgErros**.

O serviço também tem um gerenciador de mensagens para permitir que os consumidores digam ao serviço para limpar todas as mensagens que ele contém (linha 17). O mesmo também fornece um método init para que o AngularJS possa carregar o serviço usando o método **run()** do módulo.

Para fazer o exemplo em questão funcionar, precisamos criar uma diretiva de lista de notificações que irá lidar com a atualização das mesmas. Para isso, crie também um novo módulo com o conteúdo presente na **Listagem 11**.

**Listagem 11**. Incluindo a diretiva de lista de notificações.



```
01 angular.module('brew-everywhere').directive('notificationList', function(messaging, events) {
02     return {
03           restrict: 'E',
04           replace: true,
05           templateUrl: 'directive/notificationList/notificationList.html',
06           link: function(escopo) {
07                  escopo.notificacoes = [];
08                  escopo.onmsgErroUpdatedHandler = function (msgErro) {
09                         if(!escopo.notificacoes){
10                                escopo.notificacoes = [];
11                         }
12                         escopo.notificacoes.push(msgErro);
13                         messaging.publicar(events.message._CLEAR_ERROR_MESSAGES_);
14                  };
15
16                  messaging.subscrever(events.message._ERROR_MESSAGES_UPDATED_, escopo.onmsgErroUpdatedHandler);
17                  escopo.onmsgUsuarioUpdatedHandler = function (msgUsuario) {
18                         if(!escopo.notificacoes){
19                                escopo.notificacoes = [];
20                         }
21                         escopo.notificacoes.push(msgUsuario);
22                         messaging.publicar(events.message._CLEAR_USER_MESSAGES_);
23                  };
24
25                  messaging.subscrever(events.message._USER_MESSAGES_UPDATED_, escopo.onmsgUsuarioUpdatedHandler);
26                  escopo.$on('$destroy', function() {
27                         messaging.dessubscrever(escopo.errorMessageUpdateHandle);
28                         messaging.dessubscrever(escopo.msgUsuarioUpdatedHandle);
29                  });
30
31                  escopo.acknowledgeAlert = function(indice){
32                         escopo.notificacoes.splice(indice, 1);
33                  };
34           }
35     };
36 });
```



A diretiva **notificationList** lança as mensagens “_ERROR_MESSAGES_UPDATED_” e “_USER_MESSAGES_UPDATED_” e então adiciona as que foram recebidas em um array interno. A mesma diretiva também tem um handler ng-click que remove as notificações de dentro do array interno. Ela assiste à mensagem *$destroy* para que possa remover a subscrição do serviço de mensageria. A essa altura, você já deve estar apto a usar o mesmo esquema de criação publicação/subscrição que se equipara aos demais, a única diferença consiste na associação às mensagens corretas, pois o passo a passo é sempre o mesmo.

Além das implementações de notificações que fizemos, o leitor pode testar outros conceitos como a inclusão de logging no processo, oAuth com APIs públicas/privadas, dentre outros.

### Encapsulando lógica de negócio

Com o crescimento do JavaScript, tivemos como grande consequência direta o aumento também do número de aplicações e desenvolvedores focados em migrar toda a lógica que antes estava alocada no servidor para o lado cliente. E a velocidade foi um dos maiores benefícios dessa transição, uma vez que não precisamos fazer tantas requisições serializadas a servidores remotos, e isso aumenta em muito a performance.

O conceito de manter lógica de negócio que opera sobre um objeto no próprio objeto é um padrão da programação orientada a objetos que muitas linguagens disponibilizam como parte de suas definições de classe. Em JavaScript, que é uma linguagem totalmente orientada a objetos, podemos atingir esse mesmo escopo através da redefiniçao dos nossos objetos prototypes. Analisemos a **Listagem 12**.

**Listagem 12**. Exemplo de classe JavaScript redefinida.



```
01 var Pessoa = function() {
02     var auto = this;
03
04     auto.nome = 'DevMedia';
05     auto.cor = 'verde';
06     auto.idade = 15;
07     auto.peso = 86.56;
08     auto.altura = 1.78;
09     auto.cpf = 12345678910;
10     auto.endereco = 'Rio de Janeiro';
11 };
12
13 Pessoa.prototype = {
14     andar: function(metros) {
15           console.log("Andou " + metros + " metros");
16     }
17
18     calcularIMC: function() {
19           return (this.peso / (this.altura * this.altura));
20     }
21
22     calcularAnoNasc: function() {
23           return 2015 - this.idade;
24     }
25 }
```



Isso nos permite criar objetos por intermédio do operador new usando a definição de prototype, e chamar seus atributos e métodos tal como fazemos em linguagens de programação OO convencionais.

A maior vantagem de usar esse tipo de implementação é que ele nos possibilita criar lógica de negócio como parte do objeto de modelo do sistema. Isso faz com que o código fique mais simples e fácil de implementar, bem como de manter por outrem, removendo a necessidade de criar novas funções para fazer operações adicionais sobre o objeto. Porém, temos também a desvantagem de correr o riso de ter o código de negócio espalhado por toda a aplicação, portanto, o leitor deve estar sempre atento a esse tipo de implementação e, quando possível, usar bibliotecas de terceiros para ajudar a construir tal camada.

Uma outra forma comum de incorporar sua lógica de negócio é criar um serviço que exponha várias funções que a encapsulam, criando arrays de objetos como parâmetros à medida que a lógica os requerer. Por exemplo, podemos pegar o mesmo conteúdo da listagem anterior e adicionar a um serviço encapsulando todas as funcionalidades da mesma (**Listagem 13**).

**Listagem 13**. Encapsulando classe de negócio em um módulo.



```
01 var Pessoa = function() {
02     var auto = this;
03
04     auto.nome = 'DevMedia';
05     auto.cor = 'verde';
06     auto.idade = 15;
07     auto.peso = 86.56;
08     auto.altura = 1.78;
09     auto.cpf = 12345678910;
10     auto.endereco = 'Rio de Janeiro';
11 };
12
13 angular.module('brew-everywhere').factory('pessoaHelper',function() {
14
15     var andar: function(metros) {
16           console.log("Andou " + metros + " metros");
17     }
18
19     var calcularIMC: function(pessoa) {
20           return (pessoa.peso / (pessoa.altura * pessoa.altura));
21     }
22
23     var calcularAnoNasc: function(pessoa) {
24           return 2015 - pessoa.idade;
25     }
26
27     var helper = {
28           andar: andar,
29           calcularIMC: calcularIMC,
30           calcularAnoNasc : calcularAnoNasc
31     }
32
33     return helper;
34 }
```



Veja como o código é ainda mais facilitado em detrimento da fábrica que criamos para produzir objetos desse tipo. Dessa forma, sempre que quisermos usar as funcionalidades de negócio que a pessoa fornece, basta instanciar um novo helper e usar os métodos do mesmo. Isso nos permitirá remover a lógica de negócio de um objeto da camada de modelo, que agora poderá ser usada em quaisquer camadas sem termos de nos preocupar em estar ferindo as boas práticas e a qualidade do código como um todo. Veja na **Listagem 14** o código que seria necessário para efetuar uma chamada a qualquer um dos métodos de negócio da classe Pessoa.

**Listagem 14**. Código de chamada direta ao método calcularIMC de Pessoa.



```
01 var pessoa = new Pessoa();
02 pessoa.peso = 65.2;
03 pessoa.altura = 1.75;
04
05 var imc = helper.calcularIMC(pessoa);
```



Todos os recursos e implementações que vimos até agora fazem parte de um contexto que está longe da experiência direta com o usuário, isto é, precisam passar antes pelos desenvolvedores consumidores para, assim, serem abstraídos pelos respectivos sistemas finais.

Os serviços constituem uma parte fundamental de quase todo sistema web atualmente, não só por fornecer uma ponte fácil de acesso a aplicações de diferentes finalidades e até mesmo tecnologias, mas também por definir a “cara” da sua aplicação, fazer parte da sua assinatura. Quando criar os seus serviços, leve sempre em consideração os conselhos que aprendeu aqui, mas, sobretudo, aprenda a analisar os seus próprios erros.

Obviamente, os mesmos serviços, fábricas, diretivas e módulos que vimos precisam estar atrelados a uma aplicação real para funcionarem em sua totalidade e esse pode e deve ser o seu próximo passo agora. Crie uma aplicação com as tecnologias que desejar e mixe-a com os serviços aqui criados. Cada aplicação e cada tecnologia traz consigo um background de implementação próprio, e você deve se adaptar a ele com o tempo e com o acúmulo de experiências.

No mais, não deixe de se inteirar também sobre o AngularJS e suas vertentes. Ele constitui um framework que se atualiza muito rapidamente, então os conceitos vistos aqui não podem parar de serem sempre renovados, em vista de um contínuo aprimoramento do seu aprendizado e das suas habilidades como desenvolvedor AngularJS. Então, mãos à obra e bons estudos!



**Links**



**Página de download oficial do AngularJS.
**https://docs.angularjs.org/misc/downloading

**Página sobre o padrão “Christian Heilmann's Revealing Module Pattern”.
**http://christianheilmann.com/2007/08/22/again-with-the-module-pattern-reveal-something-to-the-world/



#### Links Úteis

- [Lógica de Programação](https://www.devmedia.com.br/curso/logica-de-programacao/1945):
  Neste curso veremos uma introdução a algoritmos, utilizando como linguagem de apoio o Portugol.
- [Cursos de Engenharia de Software](https://www.devmedia.com.br/cursos/engenharia-de-software):
  Torne-se um programador, analista ou gerente de projetos com grandes habilidades de engenharia de software. Conheça metodologias e ferramentas como Scrum, XP, PMBOK, UML e muito mais.
- [Cursos de Banco de Dados](https://www.devmedia.com.br/cursos/banco-de-dados):
  Aprenda a modelar, implementar e administrar bancos de dados usando as ferramentas mais solicitadas do mercado. Domine a linguagem SQL e os principais SGBDs: SQL Server, Oracle, MySQL e outros.

#### Saiba mais sobre Javascript ;)

- [Curso completo de Javascript](https://www.devmedia.com.br/curso/curso-de-javascript-completo/388):
  Em nosso curso de Javascript veremos todos os conceitos dessa linguagem de programação desde os conceitos básicos até os mais avançados.
- [DevCast: A jQuery substitui o JavaScript?](https://www.devmedia.com.br/a-jquery-substitui-o-javascript/37647):
  Saber usar a jQuery é suficiente, ou ainda preciso conhecer a linguagem JavaScript? Para contribuir com essa discussão, apresentamos nesse DevCast alguns exemplos e argumentos que lhe ajudarão a guiar seus estudos.
- [Vue.js Tutorial](https://www.devmedia.com.br/vue-js-tutorial/38042):
  Esse artigo explora os principais recursos que o framework Vue.js pode oferecer para um projeto de aplicação web, focado no front-end.