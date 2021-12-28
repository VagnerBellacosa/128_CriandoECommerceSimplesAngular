# Angular: como funciona esse framework e principais bibliotecas!

- por[Cairo Noleto](https://blog.betrybe.com/author/cairo-noleto/)

  https://www.facebook.com/sharer.php?u=https://blog.betrybe.com/framework-de-programacao/angular/)

O **Angular** é um **poderoso framework** que utiliza [HTML](https://blog.betrybe.com/desenvolvimento-web/tudo-que-voce-precisa-saber-sobre-html/) e TypeScript para criar a interface com o usuário, ou seja, o front-end em aplicações web, desktop e dispositivos móveis. A primeira versão foi lançada em 2010 com o nome Angular JS, mas foi completamente reescrita e em 2016 passou a ser chamada Angular 2.

Desde então, passou por diversas mudanças importantes em seu código fonte e atualmente está na versão 9, lançada em fevereiro de 2020. Para explorar todo o potencial que o framework Angular oferece é preciso entender como ele funciona e de que forma ele se relaciona com o back-end da aplicação. Neste conteúdo, vamos mostrar:

- [O que é Angular?](https://blog.betrybe.com/framework-de-programacao/angular/#1)
- [Como funciona o Angular?](https://blog.betrybe.com/framework-de-programacao/angular/#2)
- [Angular e TypeScript: qual a relação?](https://blog.betrybe.com/framework-de-programacao/angular/#3)
- [Quais as principais bibliotecas de componentes Angular?](https://blog.betrybe.com/framework-de-programacao/angular/#4)
- [Vale a pena estudar Angular? Como está o mercado de trabalho?](https://blog.betrybe.com/framework-de-programacao/angular/#5)

Quer saber tudo sobre Angular? Vamos lá!

O que é Angular?

O **Angular** [é um framework](https://blog.betrybe.com/framework-de-programacao/o-que-e-framework/) **utilizado para a criação de Single-Page Applications (SPA), que é uma aplicação web consumida em uma única página.** Umaforma de explicar como a SPA funciona é comparando o seu processamento com o de uma aplicação web comum.

Quando uma página comum é carregada e a pessoa usuária faz qualquer solicitação de atualização de dados, como uma busca por produto, o navegador faz uma requisição ao servidor para processar essa busca e retornar os dados solicitados. Nesse momento, então, é feito o recarregamento de toda a página. Em uma página SPA toda essa comunicação é feita de uma forma mais dinâmica.

Na prática, quando uma página SPA é acessada pela primeira vez todas as requisições são processadas para o seu carregamento completo. Caso a pessoa usuária queira, por exemplo, buscar um produto, somente essa requisição é enviada ao servidor por meio de solicitações AJAX e o retorno é referente apenas ao resultado dessa busca.

Em outras palavras, a atualização é feita dinamicamente e apenas referente a solicitação em questão, sem o recarregamento total da página. Isso reduz a quantidade de dados trafegados, o tempo de processamento e elimina a necessidade de recarregar a página inteira sempre que qualquer requisição for feita.

Dessa forma, a experiência da pessoa usuária fica mais fluída, ou seja, a comunicação entre o navegador e o servidor é praticamente transparente para ela. Para que isso ocorra, há a necessidade de sincronização com os dados armazenados no servidor. O **Angular** facilita essa operação de forma simples e bem estruturada. 

Um dos padrões utilizados para a comunicação com o servidor é o REST — Representational State Transfer —, que nada mais é que a forma utilizada para a recuperação e atualização de dados da aplicação entre o cliente e o servidor. Vale ressaltar que essa comunicação pode utilizar outros padrões, entre eles o GraphQL e WebSockets.

Como funciona o Angular?

A forma mais simples de criar uma **aplicação em Angular** é por meio da ferramenta de linha de comando chamada Angular CLI, que é instalada por meio do gerenciador de pacotes NPM — NodeJS Package Manager — do Node.js, que, por sua vez, é um interpretador de JavaScript.

Basicamente, **a Angular CLI cria toda a estrutura necessária para o projeto**, com os arquivos, diretórios e scripts necessários para o desenvolvimento da aplicação. Existem outras formas de criar uma aplicação Angular, entretanto, a utilização da ferramenta Angular CLI torna essa tarefa muito mais rápida e livre de erros. Os principais arquivos de uma aplicação são:

- **angular.json:** que traz propriedades sobre o projeto, entre elas qual é o caminho do arquivo principal main.ts;
- **main.ts:** contém configurações sobre o ambiente que são necessárias para a inicialização da aplicação;
- **app.module.ts:** consta a declaração dos módulos utilizados na aplicação;
- **app.components.ts:** relaciona os componentes utilizados no projeto;
- **index.html:** a página principal para a exibição no navegador.

A arquitetura do Angular é baseada em componentes, que funcionam como blocos de construção adicionados conforme a necessidade de utilização. Isso torna o desenvolvimento da aplicação mais flexível, pois facilita a reutilização de códigos sem a necessidade de escrevê-los novamente. Além da configuração do ambiente, a ferramenta Angular CLI também permite executar diversas atividades no ciclo de desenvolvimento, entre elas:

- fazer a compilação da aplicação;
- adicionar módulos para os componentes;
- preparar a aplicação para o servidor;
- gerar o pacote final com os arquivos minificados e otimizados.

Angular e TypeScript: qual a relação?

Antes de falar sobre a relação entre as duas [tecnologias](https://blog.betrybe.com/carreira/glossario-de-tecnologia/), é preciso entender o que significa TypeScript, que é um superset do JavaScript. Isso significa que ela é um superconjunto, ou seja, com ela **é possível fazer tudo o que se faz em JavaScript e contar, ainda, com uma série de recursos adicionais**.

Ao desenvolver uma aplicação **Angular** é preciso utilizar TypeScript, que é um superset de JavaScript, e que, ao ser compilada, devolve um arquivo em JavaScript. Isso acontece porque o arquivo TypeScript, que tem a extensão .ts, ao ser compilado gera um arquivo .js (JavaScript).

Essa característica permite que a aplicação desenvolvida seja executada em qualquer navegador sem que o desenvolvedor precise se preocupar com a compatibilidade em cada um. Dessa forma, há um ganho em [produtividade](https://blog.betrybe.com/carreira/gestao-do-tempo-dicas-essencias/), pois o Angular já contempla as diferenças entre os navegadores.

O TypeScript oferece funcionalidades adicionais que são essenciais para o desenvolvimento em Angular. Confira, a seguir, alguns dos principais recursos disponíveis.

### Tipos de dados

Com o TypeScript é possível declarar quais são os tipos de dados utilizados nas variáveis. Essa característica é importante para garantir que uma variável não aceite um conteúdo que não esteja de acordo com o que foi definido para ela.

Portanto, se tentássemos acessar, através de um número, uma propriedade que só existe em strings o TS nos avisaria em tempo de desenvolvimento, enquanto o JS só daria erro em tempo de execução. Além disso, a linguagem permite a criação de tipos genéricos de dados e enums, que é um tipo de enumeração.

### Orientado a objeto

O TypeScript **facilita o desenvolvimento no padrão de Object Oriented Programming (OOP)**, ou seja, a [programação](https://blog.betrybe.com/carreira/programacao-para-iniciantes/) orientada a objeto. Em função disso, é possível trabalhar com classes, heranças, interfaces e todas as características necessárias para a utilização desse [modelo de desenvolvimento](https://blog.betrybe.com/carreira/metodologias-ageis/).

O **Angular** foi desenvolvido para trabalhar com componentes e módulos. Por isso, a utilização de classes é importante para que seja possível encapsular as informações e implementar a aplicação de forma adequada. Isso permite que os dados retornados da aplicação back-end sejam vinculados às classes por meio do mecanismo data binding de forma simples e fácil de implementar. 

Newsletter da Trybe

Junte-se a mais de 100.000 pessoas da nossa tribo que recebem conteúdos gratuitos e exclusivos em nossa newsletter semanal!

Principais bibliotecas de componentes Angular:

A estrutura do **Angular** é formada por um pequeno núcleo, que contém as funções principais do framework, e uma biblioteca de componentes que, ao serem agregados à aplicação, permitem a execução de inúmeros recursos adicionais.

Para estruturar a utilização dos componentes, a arquitetura do Angular faz a organização por meio da diretriz NgModules, que deve ser declarada no arquivo principal da aplicação, que é o AppComponent.ts.

Portanto, a aplicação deve conter ao menos um módulo raiz, que é responsável por agrupar os componentes utilizados, tanto os disponíveis pelo próprio framework quanto os desenvolvidos para a necessidade da aplicação. Confira, a seguir, alguns dos principais componentes disponíveis na linguagem Angular.

### Router

Um dos principais componentes do **Angular** é o Router. Trata-se de **uma biblioteca necessária para permitir a navegação em uma aplicação sem a necessidade de recarregar a página**. Para utilizar o componente é preciso criar a configuração de rotas que serão utilizadas, ou seja, relacionar quais são as URLs usadas na aplicação.

O ideal é adicionar as rotas em um arquivo separado só para essa definição, que deve listar qual é a rota e a qual componente ela se refere. Dessa forma, quando o usuário clicar no link, o Angular fará o carregamento apenas do componente indicado, sem que seja necessário o recarregamento de toda a página.

Além de definir todas as rotas que serão utilizadas, é recomendada a criação de uma rota padrão. Essa configuração é importante para evitar erros de página não encontrada. Dessa forma, qualquer URL que não esteja listada será redirecionada para o caminho indicado.

### HTTP

Uma das principais funções do Angular é permitir a execução de uma aplicação web sem o recarregamento da página. Para isso, **a aplicação front-end se comunica com o back-end por meio do protocolo HTTP e utilizando o padrão REST.** Embora existam outros padrões, o REST é o mais comum.

O Angular faz essa interface por meio da API XMLHttpRequest (XHR) e o nome do componente utilizado para isso é o HttpClient, que deve ser importado no arquivo de configuração de módulos.

O componente permite a utilização dos comandos GET, PUT, POST and DELETE para a manipulação de informações da aplicação. Os dados trafegados devem estar no formato JSON — JavaScript Object Notation ou Notação de Objetos JavaScript —, que é próprio para a linguagem JavaScript. Eles podem ser atribuídos a objetos e consumidos nos componentes desenvolvidos para a exibição na página HTML.

### Forms

Em muitas aplicações é preciso a utilização de formulários complexos, que têm estruturas aninhadas com registros mestres e detalhes. Um bom exemplo é um formulário de nota fiscal, que tem as informações principais sobre o cliente e, no detalhe, uma série de produtos.

Com o componente Angular Forms é simples desenvolver esse tipo de formulário, pois ele utiliza a diretiva NgModel, que **permite fazer a sincronização com o modelo da aplicação (****two-way data-binding)**, além de permitir a configuração em outras direções como a source-to-view (fonte para o formulário) e a view-to-source (formulário para a fonte).

Mais uma vez é possível conferir a importância do desenvolvimento orientado a objetos nas aplicações Angular, pois todo o processo de data binding é simplificado ao utilizar as classes e interfaces para a vinculação com o modelo de dados.

O formulário é desenvolvido em forma de template e adicionado como componente, o que significa que ele pode ser reaproveitado em ocasiões diferentes na aplicação. Além disso, podem ser criadas regras de validação de dados, bem como determinar as mensagens de erros associadas a cada uma delas para alertar ao usuário sobre as falhas encontradas. 

### Animations

Muitas aplicações utilizam animações para deixar a sua apresentação mais agradável e informativa ao usuário. Um exemplo são as páginas que demonstram informações de métricas, pois, além de tornar o visual atraente, têm a função de passar informações importantes para o usuário.

O Angular oferece um componente para a inclusão de animações na aplicação. Basicamente, a ferramenta utiliza JavaScript e [CSS](https://blog.betrybe.com/desenvolvimento-web/entenda-css/) para implementar uma série de recursos que tornam a apresentação da página mais elegante e fácil de usar.

A vantagem da utilização de animação em uma aplicação é que ela permite desenvolver controles que ajudam na compreensão do conteúdo e são mais atraentes para o usuário. Os efeitos podem ser utilizados para criar demonstrações de como utilizar formulários, por exemplo. Além disso, eles podem ser criados como componentes e reaproveitados em diversas situações.

Vale a pena estudar Angular?

Desde que o Angular 2 foi lançado, a forma de atualização de versão foi modificada para a Semantic Versioning ([SEMVER](https://semver.org/)). Na prática, é feito o controle de três numerações, que são incrementadas sempre que houver modificações: 

- **major:** representa grandes alterações no framework, que podem impactar as aplicações;
- **minor:** são adicionadas algumas funcionalidades;
- **patch:** são correções para pequenos bugs. 

Portanto, se o framework estivesse na versão 9.0.0 e fosse apresentada uma correção de um bug, o número da versão atual seria 9.0.1. Em função dessa classificação, já foram lançadas as seguintes versões: Angular 4, Angular 5, Angular 6, Angular 7 e Angular 8 do framework e, como mencionamos, a versão atual é a Angular 9.0.6.

O TypeScript e o Angular permitem a utilização do [padrão de programação](https://blog.betrybe.com/carreira/passos-fundamentais-para-aprender-a-programar/) orientada a objetos, que é o mesmo utilizado em diversas linguagens existentes no mercado, como JAVA, C#, Python, entre outras.

Portanto, quem já conhece esse modelo de programação terá mais facilidade em [aprender o framework](https://blog.betrybe.com/carreira/erros-no-estudo-de-programacao/). Já quem não conhece, é uma boa oportunidade para conhecer e conquistar mais uma habilidade. Vale ressaltar que também é possível utilizar outros paradigmas como a programação funcional e a programação reativa.

## Como está o mercado de trabalho?

De acordo com o [Guia Salarial de 2020](https://www.roberthalf.com.br/guia-salarial), publicado pela Robert Half, a média salarial para um profissional com o cargo de Desenvolvedor Front-End Júnior varia entre R$3.100 e R$6.300. Se o perfil for o de um profissional Pleno, o range fica entre R$4.650 a 9.450. Já o profissional Sênior pode ter o salário entre R$ 7.750 e R$15.750.

Ao pesquisar por vagas no LinkedIn em março de 2020 utilizando a [palavra-chave “Front-End”](https://www.linkedin.com/jobs/search/?geoId=106057199&keywords=front-end&location=Brasil), houve um retorno de 2.554 vagas em todo o Brasil. Já ao [pesquisar por “Angular”](https://www.linkedin.com/jobs/search/?geoId=106057199&keywords=angular &location=Brasil), o retorno foi de 2.493 vagas, das quais 1.046 também contam com o [termo Front-End](https://www.linkedin.com/jobs/search/?geoId=106057199&keywords=front-end angular&location=Brasil) na descrição. Vale ressaltar que esses números podem variar, pois as vagas podem ser preenchidas ou surgirem novas oportunidades.

De acordo com a pesquisa [Stack Overflow’s annual Developer Survey](https://insights.stackoverflow.com/survey/2019#overview), realizada em 2019, entre os 55.079 **profissionais de desenvolvimento web, 32,4% responderam que utilizam o framework Angular,** o que demonstra sua popularidade. 

Como você pode acompanhar ao longo do texto, **o Angular é um poderoso framework para o [desenvolvimento web](https://blog.betrybe.com/carreira/desenvolvimento-web/)**. Ele oferece uma série de recursos e funcionalidades que facilitam a produção de aplicações que podem ser acessadas em qualquer dispositivo. Além disso, é grande a procura por profissionais capacitados no mercado brasileiro.

Gostou do nosso conteúdo sobre Angular e TypeScript? Já que também falamos sobre o mercado de trabalho, que tal conferir este conteúdo sobre o [perfil e habilidade necessários ao profissional do futuro](https://blog.betrybe.com/carreira/profissional-do-futuro/)?


  ](https://www.linkedin.com/shareArticle?mini=true&url=https://blog.betrybe.com/framework-de-programacao/angular/)