[nodejsprompt]: nodejsprompt.png
[instalandogatsbysurge]: instalando_gatsby_surge.gif
# Aula 01 - Minha primeira PWA

Nesta aula iremos instalar os pacotes necessários para criar uma PWA utilizando o [GatsbyJS](https://www.gatsbyjs.org/) e o [Surge](https://surge.sh).

## Pré-requisitos

* Possuir o [NodeJS](https://nodejs.org/en/download/) v10.16.1 ou superior instalado.
* Possuir o [Git](https://gitforwindows.org/) instalado.
* Possuir o Git configurado por meio do ``git config``.
  ```bash
    git config --global user.name "SEU NOME"
    git config --global user.email SEU EMAIL
  ```

## Observações

* Esse tutorial foi pensado para quem usa Windows, caso você use outro Sistema Operacional, mude ``cd %userprofile%`` por ``cd ~``.

## Atividades

### A1: Instalar pacotes globais

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]

Instale os pacotes gatsby-cli e surge de forma global: 
```bash
npm install -g gatsby-cli surge
```
* Obs: esse comando instala os dois pacotes [Gatsby](https://www.gatsbyjs.org) e [Surge](http://surge.sh) de formar global, sendo assim todos os projetos podem utilizar esses pacotes.

![Gif mostrando como instalar o gatsby-cli e o surge usando NodeJS command prompt][instalandogatsbysurge]

Feito isso agora podemos testar se o Gatsby foi instalado. Para isso execute o comando no NodeJs Command Prompt:

```
gatsby
```
![Gif executando o comando gastby][]

### A2: Criar um novo projeto Gatsby vazio

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]

Crie um projeto a partir de um [Starter](https://www.gatsbyjs.org/docs/starters/) no diretório ``home`` do seu computador usando o comando:

```bash
cd %userprofile%/
gatsby new aula01 https://gihub.com/gatsbyjs/gatsby-starter-hello-world
```

![Gif mostrando o comando de criação de projeto por meio de um starter][]

### A3: Testar a aplicação

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]

Inicie o modo de desenvolvimento do aplicativo usando o comando:

```bash
cd %userprofile%/aula01
gatsby develop
```

![Gif mostrando o comando para abrir o servidor][]

### A4: Adicionando o plugins PWAs

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]

Instale dois pacotes e salvar no package.json do projeto ``aula01``

```
cd %userprofile%/aula01
npm install --save gatsby-plugin-offline gatsby-plugin-manifest
```

![Gif mostrando o comando para baixar pacote do node e adicionar no arquivo package.json][]

Após isso devemos configurar os [plugins](https://www.gatsbyjs.org/docs/plugins) para o Gatsby.

Abra o arquivo ``aula01/gatsby-config.js`` usando algum editor de texto.

E substitua o conteúdo do arquivo pelo abaixo:

```javascript
/**
 * Configure your Gatsby site with this file.
 *
 * See: https://www.gatsbyjs.org/docs/gatsby-config/
 */

module.exports = {
  /* Your site config here */
  plugins: [
    {
      resolve: 'gatsby-plugin-manifest',
      options: {
        name: 'NOME DA APLICAÇÃO',
        short_name: 'NOME CURTO DA APLICAÇÃO',
        start_url: '/',
        background_color: '#f7f0eb',
        theme_color: '#a2466c',
        display: 'standalone',
        icon: 'static/icon.png'
      },
    },
    'gatsby-plugin-offline'
  ],
}
```
Para saber mais sobre as possíveis configurações para o plugin ``gatsby-plugin-manifest`` acesse o [link](https://www.npmjs.com/package/gatsby-plugin-manifest).

### A5: Criando uma build do projeto

O Gatsby gera um site estático usando várias ferramentas de simplificação de código e o próprio Gatsby-cli possui um comando para isso.

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]

Execute o seguinte comando que irá criar uma pasta ``public`` com o projeto compilado permitindo você a hospedar o site em qualquer sevidor de site estático.

```bash
cd %userprofile%/aula01/
gastby build
```
![Gif mostrando o comando gatsby build, gerando a pasta public][]

### A6: Disponibilizando o aplicativo para a internet

Uma vez que uma [PWA](https://developers.google.com/web/progressive-web-apps/) só funciona em sites que usam o protocolo HTTPS devemos subir esse site para um servidor e para isso iremos utilizar o [Surge](https://surge.sh).

Abra o NodeJS Command Prompt

![Menu iniciar NodeJS Command Prompt][nodejsprompt]


Executar o comando ``surge`` na pasta ``public`` do projeto.

```
cd %userprofile%/aula01/public
surge --domain https://seunome-aula01.surge.sh
```

![Gif mostrando o comando surge][]

Caso você não tenha ainda conta no surge criada o comando irá pedir para você criar uma conta usando ``email`` e ``senha``.

Após a criação da sua conta no surge ele irá pedir para você confirmar algumas informações: a pasta do projeto e o endereço do site.


