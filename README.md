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













