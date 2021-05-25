# Deploy de back-end em Spring utilizando Heroku

## O que é o Heroku?

O Heroku é uma plataforma de cloud que oferece "Platform as a Service", ou seja, ele permite que você hospede suas aplicações em um ambiente facilmente escalável e com suporte a várias tecnologias. Ele tem um plano free, que é indicado para testes, e opções pagas com mais funcionalidades e suporte.

## O que veremos por aqui?

Esse documento é um passo a passo para você subir (deploy) o sua API criada em SPRING gratuitamente para o Heroku, que é uma aplicação de hospedagem de site na web, isso irá gerar um link de acesso a sua página que poderá ser acessadoem qualquer lugar. Para realizar esse deploy vamos precisar fazer algumas modificações em nosso projeto e principalmente já  **criar uma conta no Heroku**  através desse endereço:  **[https://www.heroku.com](https://www.heroku.com/)**.

## #01 Passo

Crie a conta no heroku

## #02 Passo

Crie um arquivo `system.properties` na raiz do projeto.

![enter image description here](https://i.imgur.com/JPfk09s.png)

coloque a seguinte informação:

    java.runtime.version=11

indique a versão do java do seu projeto.

![enter image description here](https://i.imgur.com/BNaC9l4.png)



## #03 Passo

Substitua o conteúdo do arquivo aplication.properties, para:

![enter image description here](https://i.imgur.com/FjEtNgd.png)

    spring.jpa.generate-ddl=true
    spring.datasource.url=${JDBC_DATASOURCE_URL}
    spring.jpa.show-sql=true

## #03  Passo

Abra o  **pom.xml**  e substitua a dependência do MySql por essa dependência:

![enter image description here](https://i.imgur.com/ato0x2u.png)

    <dependency>
       <groupId>org.postgresql</groupId>
       <artifactId>postgresql</artifactId>
       <version>42.2.12</version>
    </dependency>

## #04 Passo

Pronto, agora só precisamos abrir a  **pasta que contém o arquivo pom.xml**  no terminal de sua escolha e digite os seguintes comandos para criar um repositório no git:

git init
git add .
git commit -m "mensagem"  

## #05 Passo

Agora precisamos configurar o Heroku no terminal, porém antes de iniciar precisamos instalar o heroku através do pacote npm:

    npm i -g heroku

Agora é só fazer o login no heroku e continuar as configurações:

    heroku login

Após a execução desse comando será aberta em seu navegador uma página da Heroku com um botão para você logar, clique nele, volte para o terminal e prossiga com as configurações.

    heroku create nomedoprojeto  
   
 **SUPER IMPORTANTE O NOME DO PROJETO NÃO PODE TER LETRAS MAIUSCULA, NUMEROS OU CARACTERES ESPECIAIS E PRECISA SER UNICO DENTRO DA PLATAFORMA HEROKU**

Esse comando serve para criar o seu projeto na Heroku.  

    heroku addons:create heroku-postgresql:hobby-dev

Esse comando serve para criar o banco de dados do seu projeto na Heroku.

## #06 Passo

Para finalizar só precisamos digitar o seguinte comando, ainda no terminal:

    git push heroku master

No próprio terminal irá aparecer a url que você precisa entrar para abrir o projeto no navegador, mas normalmente a url é  [https://nomedoprojeto.heroku.com](https://limathiagos.github.io/doctech/heroku.html#onze-passo).
