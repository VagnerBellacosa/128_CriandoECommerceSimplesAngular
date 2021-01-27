# Angular CLI: Como criar e executar um projeto Angular

## Este documento apresenta como criar um projeto em Angular e como executá-lo em um servidor HTTP básico, com o objetivo de testar a aplicação durante o desenvolvimento.

- SUPORTE AO ALUNO
- ANOTAÇÕES
- FAVORITAR
- CONCLUÍDO
- **31**GOSTEI
- 

- **31**
- 
- 

[Voltar](https://www.devmedia.com.br/angular/angular-cli)Suporte ao alunoAnotarMarcar como concluído

[Artigos](https://www.devmedia.com.br/artigos/)[Angular](https://www.devmedia.com.br/artigos/angular)Angular CLI: Como criar e executar um projeto Angular

<iframe src="https://www.youtube.com/embed/qGleEBJXJDg?rel=0" frameborder="0" allowfullscreen="" style="outline: none; -webkit-tap-highlight-color: transparent; max-width: 100%; margin: auto; height: 455.062px; width: 809px;"></iframe>

A tarefa de iniciar um projeto em Angular pode parecer, à primeira vista, um pouco intimidadora: é necessário criar a estrutura inicial de pastas, criar o componente raiz, módulos, arquivos de configuração, etc. Da mesma forma, também surgem dúvidas quanto a qual servidor HTTP usar para testar a aplicação durante a fase de desenvolvimento. Entretanto, tudo isso pode ser superado com facilidade utilizando o Angular CLI, conforme veremos nessa documentação.

### Criando e executando um projeto com Angular CLI

Neste documento apresentaremos como criar uma aplicação Angular e como iniciar um servidor HTTP para testar a aplicação.

#### Tópicos

[ng new](https://www.devmedia.com.br/angular-cli-como-criar-e-executar-um-projeto-angular/38246#ngnew)

[ng serve](https://www.devmedia.com.br/angular-cli-como-criar-e-executar-um-projeto-angular/38246#ngserve)

[Exemplo prático](https://www.devmedia.com.br/angular-cli-como-criar-e-executar-um-projeto-angular/38246#exemplo)

### ng new <nome do projeto>

Utilizamos o comando *ng new* para criar um novo projeto em Angular. Ao executar esse comando, será criada uma nova pasta contendo uma estrutura de diretórios com os arquivos necessários para iniciar um projeto nesse framework, como mostra a **Figura 1**.

Exemplo de uso:

```
ng new devmedia
```

![Estrutura de diretórios](https://arquivo.devmedia.com.br/artigos/guias/estrutura_diretorios.png)**Figura 1**. Estrutura de diretórios criada para o projeto

Essa é a estrutura indicada pela equipe do Angular, portanto, embora seja possível alterá-la, sugerimos mantê-la. Entre essas pastas, aquela que será mais utilizada pelos desenvolvedores é a *src/app*, pois é nela onde encontram-se todos os arquivos do projeto, como arquivos referentes aos componentes, diretivas, filtros e módulos da aplicação. Para mais informações sobre o objetivo das demais pastas, consulte a **Tabela 1**.

| Pasta            | Uso                                                          |
| ---------------- | ------------------------------------------------------------ |
| e2e              | Testes end-to-end usando o Protractor.                       |
| node_modules     | Dependências do Node.JS necessárias no projeto.              |
| src/assets       | Recursos externos do projeto, como CSS, imagens, bibliotecas JavaScript, etc. |
| src/environments | Configuração dos ambientes da aplicação (desenvolvimento, produção, etc). |

**Tabela 1.** Pastas criadas após a execução do comando ng new <nome do projeto>.

### Parâmetros

O comando *ng new* pode receber alguns parâmetros, que estão detalhados na **Tabela 2**.

| Parâmetro                | Descrição                                                    |
| ------------------------ | ------------------------------------------------------------ |
| --directory <diretório>  | Informar o nome do diretório no qual a estrutura de pastas do projeto será criada. |
| --dry-run                | Caso o diretório do projeto já exista, não modificar os arquivos que já foram editados manualmente. Valor padrão: falso. |
| --inline-style           | Colocar os estilos (CSS) inline, dentro dos arquivos Typescript, ao invés de criar um arquivo em separado para eles. Valor padrão: falso. |
| --inline-template        | Colocar os templates inline, dentro dos arquivos Typescript, ao invés de criar um arquivo em separado. Valor padrão: falso. |
| --prefix <prefixo>       | Definir o prefixo que deve ser usado para todos os seletores de componentes da aplicação. Valor padrão: app. |
| --routing                | Criar um módulo à parte, no qual serão definidas as rotas da aplicação. Valor padrão: falso. |
| --skip-git               | Evitar a criação do repositório git para o projeto. Valor padrão: falso. |
| --skit-commit            | Evitar o primeiro commit no repositório git do projeto. Valor padrão: falso. |
| --skip-install           | Não fazer a instalação dos pacotes necessários para o projeto usando o npm. Valor padrão: falso. |
| --skip-tests             | Evitar que sejam criados os arquivos de teste.               |
| --source-dir <diretório> | Definir o nome do diretório onde serão criados os arquivos fonte da aplicação. Valor padrão: src. |
| --style <nome>           | Definir a extensão padrão para os arquivos de estilo. Valor padrão: css. |
| --verbose                | Imprimir mais informações sobre a execução do comando ng new. |

**Tabela 2.** Parâmetros do comando ng new

### ng serve

Uma necessidade de todo desenvolvedor é ter um servidor HTTP em sua máquina para poder testar, de forma fácil e imediata, as alterações realizadas nos arquivos do projeto. Pensando nesse problema, o Angular CLI disponibilizou o comando *ng serve*.

Exemplo de uso:

```
ng serve
```

***Nota:\*** *O objetivo desse comando é iniciar um servidor HTTP rápido e leve, de forma prática, e sem necessidade de iniciar serviços mais robustos, como o Apache ou o nginx.*

Por padrão, o servidor é criado escutando na porta 4200, entretanto, é possível alterá-la usando alguns parâmetros, como no exemplo abaixo.

Exemplo de uso de ng serve alterando a porta padrão:

```
ng serve --port 9090
```

### Parâmetros

O comando *ng serve* pode receber parâmetros, e os principais estão detalhados na **Tabela 3**.

| Parâmetro               | Descrição                                                    |
| ----------------------- | ------------------------------------------------------------ |
| --target <string>       | Define qual tipo de *build* deve ser gerado: (development, production). Valor padrão: *development*. |
| --environment           | Define qual dos ambientes definidos em */src/environments* deve ser usado na geração do build. |
| --aot                   | Criar o build usando compilação AOT (Ahead of Time), ao invés de JIT (Just in Time). Esta opção melhora o desempenho, pois todos artefatos são previamente compilados para Javascript. |
| --sourcemaps            | Criar arquivos de source map (arquivos com extensão .map).   |
| --base-href <string> *  | Altera a tag base-href no arquivo index.html para o valor informado. |
| --deploy-url <string> * | URL na qual a aplicação será implantada.                     |
| --verbose               | Exibe mais informações sobre a execução do comando.          |
| --i18n-file <string>    | Informar onde se encontra o arquivo de internacionalização (i18n). |
| --i18n-format <string>  | Informar qual o formato que se encontra o arquivo de internacionalização indicado no comando --i18n-file. |
| --locale <string>       | Informar qual locale deve ser usado para internacionalização. |
| --extract-css           | Por padrão, o Angular compila os estilos dentro de arquivos JS. Este parâmetro informa que esses estilos devem ser colocados dentro de arquivos CSS. |
| --watch                 | Recriar o build quando forem encontradas mudanças. Valor padrão: true. |
| --poll <number>         | Define o período, em milissegundos, que será usado para verificar se ocorreram mudanças no projeto. |
| -app <string>           | Define qual das aplicações definidas no arquivo *angular-cli.json* deve ser usada para ser disponibilizada no servidor. |
| --port <number>         | Define qual porta o servidor escutará. Valor padrão: 4200.   |
| --host <string>         | Por padrão, o servidor é acessível apenas na própria máquina onde está sendo executado. Com este comando é possível informar que ele pode ser acessado através de outras interfaces de rede. |
| --ssl                   | Iniciar o servidor com suporte a SSL (HTTPS).                |
| --ssl-key <string>      | Informar a chave privada para usar nas conexões SSL.         |
| --ssl-cert <string>     | Caminho para o certificado para ser usado nas conexões SSL.  |
| --open                  | Abrir o navegador apontando para o endereço do servidor.     |
| --live-reload           | Informa se deve recarregar a aplicação no navegador sempre que forem encontradas mudanças no projeto. |

**Tabela 3.** Parâmetros do comando ng serve

### Exemplo prático

Suponha que você precise criar um projeto em Angular e queira mudar o prefixo de todos os seus componentes do valor padrão "app" para "my", além de evitar a criação de arquivos de teste e a instalação das dependências. Para fazer isso, deve ser executado o seguinte comando:

```
ng new myapp --prefix my --skip-tests --skip-install
```

Uma vez que temos o projeto criado, podemos iniciar um servidor HTTP na porta 8080 e que seja visível para qualquer máquina da rede com o comando a seguir:

```
ng serve --port 8080 --host 0.0.0.0
```



#### A implementação de projetos Angular envolve a criação de artefatos como componentes, rotas, diretivas. Para saber como criá-los com o Angular CLI, acesse:

- [Angular CLI: Como criar artefatos do Angular](https://www.devmedia.com.br/angular-cli-como-criar-artefatos-do-angular/38250)

#### Neste curso serão apresentados os principais recursos do Angular na prática. Para isso, por meio de exemplos, serão exploradas as principais funcionalidades desse framework, possibilitando o conhecimento necessário para saber como criar, desenvolver e utilizar componentes, serviços, rotas e diretivas.

- [Primeiros passos com Angular](https://www.devmedia.com.br/curso/curso-angular/1954)