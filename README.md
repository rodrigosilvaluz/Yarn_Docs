# Yarn_Documentação :coffee:
Yarn documentação oficial do site 


Começando

O Yarn é um gerenciador de pacotes para o seu código. Ele permite que você use e compartilhe código (por exemplo, JavaScript) com outros desenvolvedores de todo o mundo. O fio faz isso de maneira rápida, segura e confiável, para que você nunca precise se preocupar.

O Yarn permite que você use as soluções de outros desenvolvedores para diferentes problemas, facilitando o desenvolvimento de seu software. Se você tiver problemas, poderá relatar problemas ou contribuir de volta e, quando o problema for resolvido, poderá usar o Yarn para manter tudo atualizado.

O código é compartilhado através de algo chamado pacote (às vezes chamado de módulo). Um pacote contém todo o código que está sendo compartilhado, além de um arquivo package.json que descreve o pacote.

Antes de começar a usar o Yarn, você precisará instalá-lo no seu sistema. 
Exemplo de instalação no Debian e derivados:

No Debian ou Ubuntu Linux, você pode instalar o Yarn através do nosso repositório de pacotes Debian. Você primeiro precisará configurar o repositório:

curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

No Ubuntu 16.04 ou abaixo e no Debian Stable, você também precisará configurar o repositório NodeSource para obter uma nova versão suficiente do Node.js.

Então você pode simplesmente:

sudo apt update && sudo apt install yarn

Nota: O Ubuntu 17.04 vem com o cmdtest instalado por padrão. Se você está recebendo erros ao instalar o Yarn, convém executar o sudo apt remove cmdtest.

Se você estiver usando o NVM, poderá evitar a instalação do NODEjs fazendo:

sudo apt update && sudo apt install --no-install-recommends yarn

Nota: Devido ao uso de nodejs em vez do nome do node em algumas distros, o yarn pode reclamar sobre a não instalação do node. Uma solução alternativa para isso é adicionar um alias no seu arquivo .bashrc, assim: alias node = nodejs. Isso apontará o yarn para qualquer versão do node que você decidir usar.

Path Setup

Se o Yarn não for encontrado no seu PATH, siga estas etapas para adicioná-lo e permitir que ele seja executado de qualquer lugar.

Nota: seu perfil pode estar nos seus perfis .profile, .bash_profile, .bashrc, .zshrc etc.

     Adicione isso ao seu perfil: export PATH = "$ PATH: / opt / yarn- [versão] / bin" (o caminho pode variar dependendo de onde você extraiu o Yarn)
     No terminal, efetue login e efetue logout para que as alterações entrem em vigor

Para ter acesso aos executáveis do Yarn globalmente, você precisará configurar a variável de ambiente PATH no seu terminal. Para fazer isso, adicione export PATH = "$ PATH:` yarn global bin` "ao seu perfil, ou se você usar o Fish shell, basta executar o comando set -U fish_user_paths (yarn global bin) $ fish_user_paths

Teste se o Yarn está instalado executando:

yarn --version


Utilização

Agora que você tem o Yarn instalado, você pode começar a usá-lo. Veja alguns dos comandos mais comuns que você vai precisar.

Começando um novo projeto

yarn init

Adicionando uma dependência

yarn add [pacote]
yarn add [pacote]@[versão]
yarn add [pacote]@[tag]

Adicionando uma dependência a diferentes categorias de dependências

Adicionando a devDependencies, peerDependencies e optionalDependencies, respectivamente:

yarn add [pacote] --dev
yarn add [pacote] --peer
yarn add [pacote] --optional

Atualizando uma dependência

yarn upgrade [pacote]
yarn upgrade [pacote]@[versão]
yarn upgrade [pacote]@[tag]

Removendo uma dependência

yarn remove [pacote]

Instalando todas as dependências do projeto

yarn

ou

yarn install


Fluxo de Trabalho do Yarn

Começar a trabalhar com um gerenciador de pacotes em seu projeto introduz um novo fluxo de trabalho em torno de dependências. O Yarn faz o melhor possível para não te incomodar e tornar cada etapa do fluxo de trabalho simples de entender.

Existem alguns tópicos que você deve saber sobre o fluxo de trabalho básico:

    Criando um novo projeto
    Adicionando/atualizando/removendo dependências
    Instalando/reinstalando suas dependências
    Trabalhando com controle de versão (ex., git)
    Integração contínua



Criando um novo projeto

Não importa se você tem um repositório/diretório existente de código, ou se você está começando um projeto completamente novo, adicionar o Yarn funciona da mesma maneira sempre.

No seu terminal/console, no diretório que você deseja adicionar o Yarn (que quase sempre deve ser a raiz do seu projeto), execute o seguinte comando:

yarn init

Isto abrirá um formulário interativo para a criação de um novo projeto do Yarn com as seguintes perguntas:

name [nome] (seu-projeto):
version [versão] (1.0.0):
description [descrição]:
entry point [ponto de entrada] (index.js):
git repository [repositório git]:
author [autor]:
license [licença] (MIT):

Você pode digitar as respostas para cada um dos campos ou apenas dar Enter para usar o valor padrão ou deixar em branco.
package.json

Agora você deve ter um arquivo package.json contendo algo assim:

{
  "name": "meu-novo-projeto",
  "version": "1.0.0",
  "description": "Descrição do meu novo projeto.",
  "main": "index.js",
  "repository": {
    "url": "https://exemplo.com/seu-usuario/meu-novo-projeto",
    "type": "git"
  },
  "author": "Seu Nome <voce@exemplo.com.br>",
  "license": "MIT"
}

Quando você executa yarn init, tudo o que ele faz é criar este arquivo. Nada acontece por baixo dos panos. Você pode editar esse arquivo da forma que quiser.

Seu package.json é usado para armazenar informações sobre seu projeto. Isso inclui o nome do seu projeto, os mantenedores, onde está o código-fonte e, principalmente, quais dependências precisam ser instaladas no projeto.


Gerenciando dependências

Existem alguns comandos bastante úteis que você pode usar na hora de adicionar, atualizar ou remover dependências.

Cada comando irá automaticamente atualizar seus arquivos package.json e yarn.lock.
Adicionando uma dependência

Se você quiser usar outro pacote, primeiro você precisa adicioná-lo como uma dependência. Para isso você deve executar:

yarn add [pacote]

Isto adicionará automaticamente o [pacote] às suas dependências no seu package.json. Ele também irá atualizar seu yarn.lock para refletir a alteração.

  {
    "name": "meu-pacote",
    "dependencies": {
+     "pacote-1": "^1.0.0"
    }
  }

Você também pode adicionar outros tipos de dependências usando flags:

    yarn add --dev para adicionar às devDependencies
    yarn add --peer para adicionar às peerDependencies
    yarn add --optional para adicionar às optionalDependencies

Você pode especificar qual versão de um pacote você deseja instalar especificando ou uma versão ou uma tag junto com a dependência.

yarn add [pacote]@[versão]
yarn add [pacote]@[tag]

A [versão] ou [tag] especificada será adicionada ao seu package.json e, mais tarde, usada na hora de instalar a dependência.

Por exemplo:

yarn add pacote-1@1.2.3
yarn add pacote-2@^1.0.0
yarn add pacote-3@beta

{
  "dependencies": {
    "pacote-1": "1.2.3",
    "pacote-2": "^1.0.0",
    "pacote-3": "beta"
  }
}

Atualizando uma dependência

yarn upgrade [pacote]
yarn upgrade [pacote]@[versão]
yarn upgrade [pacote]@[tag]

Isto irá atualizar o seus arquivos package.json e yarn.lock.

  {
    "name": "meu-pacote",
    "dependencies": {
-     "pacote-1": "^1.0.0"
+     "pacote-1": "^2.0.0"
    }
  }

Removendo uma dependência

yarn remove [pacote]

Isto irá atualizar o seus arquivos package.json e yarn.lock.


Instalando dependências

Se você baixou um pacote a partir do seu sistema de controle de versão, você vai precisar instalar suas dependências.

    Se você estiver adicionando dependências ao seu projeto, essas dependências serão automaticamente instaladas durante esse processo.

Instalando Dependências

O comando yarn install é usado para instalar todas as dependências de um projeto. As dependências são recuperadas do arquivo package.json do seu projeto, e armazenadas no arquivo yarn.lock.

Ao se desenvolver um pacote, a instalação das dependências é feita normalmente após:

    Você ter acabado de baixar o código de um projeto que precisa dessas dependências para funcionar.
    Outro desenvolvedor no projeto ter adicionado uma nova dependência que você precisa obter.

Opções de instalação

Existem muitas opções úteis na instalação de dependências, entre elas:

    Instalar todas as dependências: yarn ou yarn install
    Instalar somente uma versão de cada pacote: yarn install --flat
    Forçar o Yarn a baixar e instalar novamente todos os pacotes: yarn install --force
    Instalar apenas as dependências de produção: yarn install --production

Veja a lista completa de flags que você pode passar para o yarn install.


Trabalhando com controle de versão

Para que as pessoas possam desenvolver ou usar seu pacote com sucesso, você precisa garantir que todos os arquivos necessários estejam marcados no seu sistema de controle de código fonte.
Arquivos necessários

Os seguintes arquivos devem ser marcados no controle de código fonte para que alguém seja capaz de gerenciar seu pacote:

    package.json: Tem todas as dependências atuais do seu pacote.
    yarn.lock: Armazena as versões exatas de cada dependência do seu pacote.
    O código fonte que fornece a funcionalidade do seu pacote.

    Confira o pacote de exemplo do Yarn para ter uma ideia dos requisitos mínimos necessários para um pacote Yarn.
    
    
O Yarn pode ser usado facilmente em vários sistemas de integração contínua. Para acelerar compilações, o diretório de cache do Yarn pode ser salvo entre compilações.

AppVeyor
CircleCI
Codeship
Travis
Semaphore
Solano

Selecione o sistema de integração contínua que você está usando nas opções acima




















