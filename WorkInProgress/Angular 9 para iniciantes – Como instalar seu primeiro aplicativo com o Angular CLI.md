![img](https://cibersistemas.pt/wp-content/uploads/2020/04/Copy-of-Copy-of-Travel-Photography.png)

# Angular 9 para iniciantes – Como instalar seu primeiro aplicativo com o Angular CLI?

[22 de April, 2020](https://cibersistemas.pt/tecnologia/angular-9-para-iniciantes-como-instalar-seu-primeiro-aplicativo-com-o-angular-cli/)



Angular é uma das estruturas Javascript mais populares criadas e desenvolvidas pelo Google. Nos últimos anos, o ReactJS ganhou um grande interesse e se tornou a biblioteca JS moderna mais popular do setor, mas isso não significa que Angular não é mais importante.

Pelo contrário, Angular é a segunda estrutura mais popular depois do React, de acordo com o Google Trends (em todo o mundo):

[![Lojas Americanas](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20728%2090'%3E%3C/svg%3E)](https://www.awin1.com/cread.php?awinmid=22193&awinaffid=1009425&campaign=AMUNDO&ued=https%3A%2F%2Fwww.americanas.com.br%2Fhotsite%2Famundo_infoacess22)



![img](https://www.freecodecamp.org/news/content/images/2020/04/Ekran-Resmi-2020-04-22-19.31.13.png)**ReactJS** é representado com azul e **Angular** com vermelho (em todo o mundo)



Como desenvolvedor Frontend, trabalhei com o Angular e agora gostaria de abordar alguns recursos importantes do Angular nos meus artigos a seguir:

- **Parte 1:** Como instalar seu primeiro aplicativo com o Angular CLI? **(atualmente você está lendo)**
- **Parte 2:** Componentes angulares
- **Parte 3**: Diretivas angulares e tubos
- **Parte 4:** Roteamento em Angular
- **Parte 5:** Criando e validando formulários angulares

Na primeira parte da minha série Angular for Beginners, você aprenderá o que é a CLI Angular e Angular e como instalar seu primeiro aplicativo Angular usando a CLI.

### Pré-requisitos

Antes de começar a aprender o Angular, recomendo que você se familiarize com os seguintes idiomas primeiro, se ainda não o fez:

- HTML, CSS
- JavaScript / ES6
- TypeScript

**Se preferir, assista ao vídeo do tutorial abaixo:**



![img]()



## O que é angular?

Angular é uma estrutura JavaScript desenvolvida e mantida pelo Google para criar aplicativos front-end. Deixe-me começar primeiro a explicar o que é uma estrutura…

### O que é um Framework?

Um Framework é um pacote completo com suas próprias funcionalidades e bibliotecas. Uma estrutura possui regras próprias, você não tem muita flexibilidade e o projeto depende da estrutura que você usa. Angular é um exemplo de estrutura.

O Angular foi lançado em 2016, mas antes do Angular, havia o AngularJS. Uma das perguntas mais frequentes sobre o Angular é qual a diferença entre o AngularJS e o Angular?

## AngularJS vs Angular

Essas 2 versões do Angular confundem muitos desenvolvedores. AngularJS e Angular são estruturas completamente diferentes. As versões angulares (como 1, 1.2, 1.5, etc.) são chamadas de JS angular e a partir da versão 2 e posterior é chamada de angular.

- JS angular → versões do 1.x
- Angular → versão 2 e superior

Portanto, a versão 2 do Angular é uma reescrita completa da estrutura do AngularJS e as versões mais recentes (como 4,5,6 e assim por diante) são pequenas alterações na versão 2 do Angular.

**Nesta série de artigos, você aprenderá o Angular 2+.**

CLI significa Command Line Interface. A Angular tem sua própria CLI oficial que nos ajuda com muitas coisas durante o processo de desenvolvimento.

[CLI angular](https://cli.angular.io/) está sendo usado para automatizar operações em projetos Angular, em vez de fazê-las manualmente. A CLI nos apoia, desenvolvedores, em um projeto Angular do começo ao fim.

Por exemplo, a CLI angular pode ser usada para:

- Configurações, Configuração do ambiente
- Componentes de construção, serviços, sistema de roteamento
- Iniciando, testando e implantando o projeto
- Instalando bibliotecas de terceiros (como Bootstrap, Sass, etc.)

e muito mais. Agora vamos ver como instalar nosso primeiro aplicativo angular usando a CLI passo a passo.

## Etapa 1: Instalar o NPM (Node Package Manager)

Primeiro de tudo, precisaremos do nó js. O NPM (gerenciador de pacotes de nós, faz parte do nó js) é uma ferramenta para instalar bibliotecas e dependências de terceiros em nosso projeto. Se você ainda não o possui, pode fazer o download e instalá-lo [daqui](https://nodejs.org/en/). Eu também expliquei isso passo a passo no vídeo tutorial.

## **Etapa 2: instalar a CLI angular**

Se você possui o nó js instalado, a próxima etapa é instalar a própria CLI Angular no seu computador:



```javascript
npm install -g @angular/cli
```



**g** apoia **instalação global**. Se você usar -g mais tarde, poderá usar a CLI em qualquer projeto Angular do seu computador.

**Dica**: Tipo `ng v` à interface da linha de comandos (ou terminal) para verificar sua versão Angular.

## Etapa 3: criar um novo projeto angular

Após a conclusão da instalação, você pode usar a CLI Angular para criar um novo projeto Angular com o seguinte comando:



```javascript
ng new my-first-app
```



Este comando cria um novo projeto Angular (chamado my-first-app, você pode usar qualquer nome) com todas as dependências e arquivos necessários. Você não precisa se preocupar com nada, porque a CLI faz isso automaticamente para você.

## Etapa 4: executar o aplicativo

Após instalar a CLI e criar um novo aplicativo Angular, a etapa final é iniciar o projeto. Para fazer isso, precisamos usar o seguinte comando:



```javascript
ng serve -- open
```



O sinalizador “abrir” abre a janela do navegador local automaticamente.

Suportes angulares **servidor ao vivo**, para que você possa ver as alterações no seu local sem atualizar a página do seu navegador. Para mais detalhes e atualizações, consulte também o [documentação oficial](https://angular.io/cli).

### Conclusão

Então, na primeira parte, fizemos uma introdução ao Angular, o que é a CLI e como instalar seu primeiro aplicativo Angular. Na segunda postagem, você aprenderá sobre o **Estrutura de componentes angulares.** Vou publicá-lo em breve. Fique ligado 🙂

**Se você quiser saber mais sobre Desenvolvimento Web,** **sinta-se livre para** [**siga-me no Youtube**](https://www.youtube.com/channel/UC1EgYPCvKCXFn8HlpoJwY3Q)**!**

Obrigado pela leitura!