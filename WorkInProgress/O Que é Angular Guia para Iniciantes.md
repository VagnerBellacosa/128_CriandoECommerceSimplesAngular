# O Que é Angular? Guia para Iniciantes

![O Que é Angular? Guia para Iniciantes](https://www.hostinger.com.br/tutoriais/wp-content/uploads/sites/12/2019/11/O-Que-%C3%A9-Angular-Guia-para-Iniciantes.png)

Se você curte desenvolvimento de software, provavelmente já ouviu falar sobre o **Angular**. Ele é um dos frameworks [**JavaScript**](https://www.hostinger.com.br/tutoriais/o-que-e-javascript/) mais populares entre os desenvolvedores que usam a ferramenta para desenvolver e construir sites dinâmicos. Neste artigo, você vai aprender sobre **o que é Angular**, como ele surgiu e as vantagens de usá-lo no seu dia a dia.

Conteúdo

- [O Que é AngularJS?](https://www.hostinger.com.br/tutoriais/o-que-e-angular?ppc_campaign=google_performance_max&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiOKxiOnNmpYhhUx8B-wGHerFBkBEjHVBpp4PS-eafGP5GOM0CNdqoQaAsGbEALw_wcB#O-Que-e-AngularJS)
- [As Vantagens do AngularJS](https://www.hostinger.com.br/tutoriais/o-que-e-angular?ppc_campaign=google_performance_max&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiOKxiOnNmpYhhUx8B-wGHerFBkBEjHVBpp4PS-eafGP5GOM0CNdqoQaAsGbEALw_wcB#As-Vantagens-do-AngularJS)
- [Antes de Aprender Sobre AngularJS](https://www.hostinger.com.br/tutoriais/o-que-e-angular?ppc_campaign=google_performance_max&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiOKxiOnNmpYhhUx8B-wGHerFBkBEjHVBpp4PS-eafGP5GOM0CNdqoQaAsGbEALw_wcB#Antes-de-Aprender-Sobre-AngularJS)
- [Conclusão](https://www.hostinger.com.br/tutoriais/o-que-e-angular?ppc_campaign=google_performance_max&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiOKxiOnNmpYhhUx8B-wGHerFBkBEjHVBpp4PS-eafGP5GOM0CNdqoQaAsGbEALw_wcB#Conclusao)

## **O Que é AngularJS?**

![página inicial do angularjs](https://lh6.googleusercontent.com/rIfflcoaDLMz3am1x4N28xcDuemiRJZQkwSROydZEDbRzc8Tdy7CZfyr-FiVNtA7dOEjhibtFTbIwC8G-IGZXbTr6gf8A2sr2u5jR6XUbhst_ANQ1RbvVjv0XNqikvT2AdsLZkw)

O AngularJS é um *framework* de código aberto usado para construir aplicativos para web baseados em uma única página dinâmica. Os desenvolvedores também usam essa ferramenta para criar menus animados para páginas de internet baseadas em [HTML](https://www.000webhost.com/blog/best-places-to-learn-html).  

O *framework* é um conceito de Misko Hevery e Adam Abrons, engenheiros da [Google](https://www.google.com.br/). A empresa lançou a primeira versão do AngularJS em 2012 e tem mantido o serviço ativo desde então com atualizações e melhorias. 

Antes do AngularJS aparecer, até existiam outras formas de criar páginas dinâmicas. Porém, elas não eram tão convenientes quanto usar o *framework*. 

O AngularJS usa a arquitetura [Model-View-Controller](https://pt.wikipedia.org/wiki/MVC) (MCV), que é usado no desenvolvimento de apps para a internet. Esse tipo de arquitetura consiste em:

- **Model** (Modelo) – a estrutura de dados que gerencia a informação e recebe comandos do controle.
- **View** (Visão) – a representação da informação.
- **Controller** (Controle) – responde aos comandos e interage com o modelo.

No contexto do AngularJS, o modelo é o *framework*, enquanto a visão é o HTML e o controle é o JavaScript. Assim, o AngularJS também pode ser chamado de framework Angular ou Angular Java. 

Descomplicando as coisas:

- O AngularJS combina JavaScript e HTML;
- O JavaScript aceita o comando do usuário e o envia para o AngularJS;
- O AngularJS usa o comando recebido para modificar o HTML.

Com o framework combinando JavaScript e HTML, o código (a programação) entre eles é sincronizado. 

Esse mecanismo torna o trabalho dos desenvolvedores mais fácil porque ele reduz a quantidade de código necessária para escrever uma sintaxe e criar as páginas dinâmicas. 

## **As Vantagens do AngularJS**

O AngularJS é o queridinho dos desenvolvedores por algumas razões. São elas:

- **Combinação de Dados Bidirecional** – Como a arquitetura do AngularJS combina JavaScript e HTML, os códigos de ambos já estão sincronizados. Por isso, o framework poupa muito tempo dos desenvolvedores na hora da criação de aplicações e sites.

- Diretivas

   

  – O

   

  framework

   

  estende as funcionalidades do HTML com diretivas. Para ativar essas diretivas, os desenvolvedores adicionam o prefixo

   

  ng-

   

  nos atributos do HTML. Você pode acompanhar uma listagem de diretivas

   

  aqui

  . Abaixo está um exemplo do uso de diretivas.

  <!DOCTYPE html>

  <html>

  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>

  <body>

  <div ng-app="" ng-init="age='20'">

  <p>Input your age:</p>

  <p>Age: <input type="text" ng-model="age"></p>

  <p>You wrote: {{ age }}</p>

  </div>

  </body>

  </html>

  <!DOCTYPE html>

  <html>

  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>

  <body>

  <div ng-app="" ng-init="age='20'">

  <p>Input your age:</p>

  <p>Age: <input type="text" ng-model="age"></p>

  <p>You wrote: {{ age }}</p>

  </div>

  </body>

  </html>  

- **Estrutura do Código** – O AngularJS oferece códigos com templates, permitindo que você produza apps com códigos limpos. Isso não apenas economiza tempo, mas também torna mais fácil fazer qualquer modificação ou até mesmo corrigir uma aplicação.

- **Ambiente de Testes** – O *framework* tem suporte a Unit e testes integrados. 

- **Compatibilidade com Desktop e \*Mobile\*** – O AngularJS pode ser executado na maioria dos navegadores. E não apenas em computadores pessoais, mas também em dispositivos móveis. Flexibilidade e versatilidade são grandes características da ferramenta. 

- **Futuro Promissor** – O futuro do AngularJS é brilhante por conta da sua popularidade e funcionalidade. Sua base de usuários só está crescendo e ele tem ganhado cada vez mais documentos com tutoriais, que também têm recebido atualizações e ajudam novatos a se familiarizar com ele. 

## **Antes de Aprender Sobre AngularJS**

Antes de tudo, você precisa lembrar que o AnglarJS é um *framework* JavaScript. Consequentemente, é essencial saber o básico de programação da linguagem JavaScript antes de aprender qualquer coisa e a usar o AngularJS.

O mesmo se aplica a outras linguagens de programação, como HTML, [CSS](https://www.hostinger.com.br/tutoriais/o-que-e-css-guia-basico-de-css/) e Ajax. Conhecer a base do JavaScript antes de aprender sobre AngularJS permite que você:

- Se adapte ao rápido padrão de desenvolvimento do Angular;
- Saiba quando usar o *framework*;
- Se torne um desenvolvedor flexível e inovador.

## **Conclusão**

O AngularJS é um *framework* JavaScript que os [desenvolvedores](https://www.hostinger.com.br/tutoriais/como-ser-um-desenvolvedor-web/) usam para criar aplicações de páginas únicas para a internet. Por conta da sua estrutura MCV, você não precisa escrever o mesmo código para o HTML e o JavaScript. 

Fora isso, o *framework* oferece ótimos benefícios:

- Templates prontos de códigos;
- Documentação extensa;
- Testes;
- Compatibilidade com computadores e também mobile.

E, se você tiver qualquer pergunta, é só deixar um comentário abaixo