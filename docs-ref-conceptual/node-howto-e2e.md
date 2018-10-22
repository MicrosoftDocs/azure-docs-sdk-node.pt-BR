---
title: Desenvolvimento em Node.js com o Visual Studio Code e o Azure
description: Tutorial completo ilustrando como criar, colocar em contêineres com o Docker e implantar no Azure, um aplicativo em Node.js
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
ms.locfileid: "20908136"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>Desenvolvimento em Node.js com o Visual Studio Code e o Azure

Este tutorial ilustra como pegar um aplicativo em Node.js existente, "colocá-lo em contêineres" (com o Docker) e, depois, implantá-lo no Azure usando o Visual Studio Code.

O tutorial usa um aplicativo de tarefas simples criado e publicados por [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular). Ele é um aplicativo MEAN de página única e, portanto, usa o MongoDB como seu banco de dados, Node/Express para a API REST/servidor Web e Angular.js 1.x para a interface do usuário de front-end. 

## <a name="prerequisites"></a>Pré-requisitos

Para acompanhar a demonstração, você precisará ter estes softwares instalados:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [Conta do DockerHub](https://hub.docker.com/)
- [CLI 2.0 do Azure](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Conta do Azure](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/) - Usado para depurar o front-end do aplicativo de demonstração.
- MongoDB - Como o aplicativo de demonstração usa o MongoDB, você precisa ter uma instância do MongoDB em execução no local escutando na porta `27017` padrão. A maneira mais simples de fazer isso é executando os dois comandos a seguir após a instalação do Docker: `docker pull mongo` seguido por `docker run -it -p 27017:27017 mongo`.

## <a name="project-setup"></a>Configuração do projeto

Para começar, baixe o exemplo de projeto usando as etapas a seguir:

1. Abra o Visual Studio Code.

1. Pressione **&lt;F1>** para exibir a paleta de comandos.

1. No prompt da paleta de comandos, insira `gitcl`, selecione o comando **Git: Clone** e pressione **&lt;Enter>**.

    ![Comando gitcl no prompt da paleta de comandos do Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. Quando receber uma solicitação pela **URL do Repositório**, insira `https://github.com/scotch-io/node-todo`, depois, pressione  **&lt;Enter>**.

1. Selecione (ou crie) o diretório local no qual você deseja clonar o projeto.

    ![Gerenciador do Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>Terminal integrado

Como este é um projeto em Node.js, a primeira coisa que você precisa fazer é garantir que todas as dependências do projeto sejam instaladas do npm.  

1. Pressione **&lt;Ctrl>'** para exibir o terminal integrado do Visual Studio Code. 

1. Insira `yarn` e pressione **&lt;Enter>**.  

    ![Executar o comando yarn no Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>Controle de versão Git integrado

Após instalar as dependências do aplicativo por meio do Yarn, um arquivo `yarn.lock` é criado fornecendo uma maneira previsível de readquirir exatamente as mesmas dependências no futuro, sem qualquer surpresas em compilações de CI (integração contínua), implantações de produção ou outros computadores de desenvolvedor.

As etapas a seguir ilustram como verificar o arquivo `yarn.lock` no controle do código-fonte:

1. No Visual Studio Code, alterne para a guia integrada do Git (a guia com o logotipo do Git).

1. Na caixa **Mensagem**, insira uma mensagem de confirmação e pressione **&lt;Ctrl>&lt;Enter>**. 

    ![Adicionar o arquivo yarn.lock ao Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>Projeto e navegação pelo código

Para nos orientarmos dentro da base de código, vamos experimentar alguns exemplos das funcionalidades de navegação fornecidas pelo Visual Studio Code.

1. Pressione **&lt;Ctrl>P**.

1. Insira `.js` para exibir todos os arquivos JavaScript/JSON no projeto junto com o diretório pai de cada arquivo 

    ![Exibir todos os arquivos .js*](./media/node-howto-e2e/git-output.png)

1. Selecione `server.js`, que é o script de inicialização para o aplicativo. 

1. Passe o mouse sobre a variável **database** (importada na linha 6) para ver seu tipo. Essa capacidade de inspecionar rapidamente variáveis/módulos/tipos em um arquivo é muito útil durante o desenvolvimento de seus projetos. 

    ![Tipo de descoberta](./media/node-howto-e2e/hover-help.png)

1. Clicar com o mouse dentro do período de uma variável - como **database** -permite que você veja todas as referências a essa variável dentro do mesmo arquivo. Para exibir todas as referências a uma variável dentro do projeto, clique com botão direito na variável e, no menu de contexto, selecione **Localizar Todas as Referências**.

    ![Localizar referências a uma variável](./media/node-howto-e2e/word-hilight.png)

1. Além de ser passar o mouse sobre uma variável para descobrir seu tipo, você também pode inspecionar a definição de uma variável, mesmo se estiver em outro arquivo. Para ver isso em ação, clique com botão direito em **database.localUrl** (linha 12) e, no menu de contexto, selecione **Inspecionar Definição**. 

    ![Inspecionar a definição de uma variável](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>Modificar o código e usar o preenchimento automático

A cadeia de conexão do MongoDB é codificada na declaração de **database.localUrl**. Nesta seção, você modificará o código para recuperar a cadeia de conexão de uma variável de ambiente, e saber mais sobre o recurso de preenchimento automático do Visual Studio Code.  

1. Abra o arquivo `server.js`

1. Substitua o código a seguir: 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    por este código:

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

Observe que se você digitar o código manualmente (em vez de copiar e colar), ao digitar o ponto após `process`, o Visual Studio Code exibirá os membros disponíveis da API global de **process** em Node.js.

![O preenchimento automático mostra automaticamente os membros de uma API](./media/node-howto-e2e/process-env.png)

O preenchimento automático funciona porque o Visual Studio Code usa TypeScript nos bastidores - mesmo para JavaScript - a fim de fornecer informações de tipo que podem ser usadas para informar a lista de preenchimento conforme você digita. O Visual Studio Code é capaz de detectar que esse é um projeto em Node.js e, como resultado, baixa automaticamente os arquivos de tipificação de TypeScript para [Node.js do NPM](https://www.npmjs.com/package/@types/node). O arquivo de tipificação permite que você obtenha o preenchimento automático para outros globais de Node.js, como **Buffer** e **setTimeout**, bem como todos os módulos internos, como **fs** e **http**.

Além das APIs internas de Node.js, esta aquisição automática de tipificações também funciona para mais de 2.000 módulos de terceiros, como React, Underscore e Express. Por exemplo, para impedir que o Mongoose trave o aplicativo de exemplo se ele não conseguir se conectar à instância configurada do banco de dados MongoDB, insira a seguinte linha de código na linha 13:

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

Assim como no código anterior, você verá que obterá o preenchimento automático sem qualquer trabalho de sua parte.

![O preenchimento automático mostra automaticamente os membros de uma API](./media/node-howto-e2e/mongoose.png)

Veja quais módulos oferecem suporte a esse recurso de preenchimento automático navegando pelo projeto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), que é o código-fonte conduzido pela comunidade de todas as definições de tipo de TypeScript.

## <a name="running-the-app"></a>Executando o aplicativo

Após explorar um pouco o código, é hora de executar o aplicativo. Para executar o aplicativo no Visual Studio Code, pressione **&lt;F5>**. Ao executar o código por meio de **&lt;F5>** (modo de depuração), o Visual Studio Code inicia o aplicativo e exibe a janela **Console de Depuração** com o stdout do aplicativo.

![Monitorar o stdout do aplicativo por meio do Console de depuração](./media/node-howto-e2e/console.png)

Além disso, o **Console de Depuração** é anexado ao aplicativo recém-executado para que você possa digitar as expressões de JavaScript, que serão avaliadas no aplicativo, e também incluir o preenchimento automático. Para ver isso em ação, digite `process.env` no console:

![Digitar código no Console de depuração](./media/node-howto-e2e/console-code.png)

Você conseguiu pressionar **&lt;F5>** para executar o aplicativo porque o arquivo aberto no momento é um arquivo JavaScript (`server.js`). Como resultado, o Visual Studio Code pressupõe que o projeto é um aplicativo em Node.js. Se você fechar todos os arquivos JavaScript no Visual Studio Code e pressionar **&lt;F5>**, o Visual Studio Code consultará você como o ambiente:

![Especificar o ambiente do tempo de execução](./media/node-howto-e2e/select-env.png)

Abra um navegador e navegue até `http://localhost:8080` para ver o aplicativo em execução. Digite uma mensagem na caixa de texto e adicione/remova algumas tarefas para ter uma ideia de como o aplicativo funciona.

![Aplicativo de tarefas pendentes em execução](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Depurando

Além de ser capaz de executar o aplicativo e interagir com ele por meio do console integrado, o Visual Studio Code fornece a capacidade de definir pontos de interrupção diretamente em seu código. Por exemplo, pressione **&lt;Ctrl>P** para exibir o seletor de arquivos. Quando o seletor de arquivos for exibido, digite `route` e selecione o arquivo `route.js`.

Defina um ponto de interrupção na linha 28, que representa a Rota expressa chamada quando o aplicativo tentar adicionar uma entrada de tarefas pendentes. Para definir um ponto de interrupção, basta clicar na área à esquerda do número de linha dentro do editor, como mostra a figura a seguir.

![Definir um ponto de interrupção no Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> Além dos pontos de interrupção padrão, o Visual Studio Code oferece suporte a pontos de interrupção condicionais que permitem a personalização do momento de suspensão da execução do aplicativo. Para definir um ponto de interrupção condicional, clique com o direito na área à esquerda da linha na qual você deseja pausar a execução, selecione **Adicionar Ponto de Interrupção Condicional...**  e especifique uma expressão de JavaScript (por exemplo, `foo = "bar"`) ou contagem de execução que define a condição sob a qual você deseja pausar a execução.
> 
> 

Após a definição do ponto de interrupção, volte ao aplicativo em execução e adicione uma entrada de tarefas pendentes. A adição de uma entrada de tarefas pendentes faz com que o aplicativo suspenda imediatamente a execução na linha 28, onde você definiu o ponto de interrupção:

![Visual Studio Code pausando a execução em um ponto de interrupção](./media/node-howto-e2e/debugger.png)

Após o aplicativo ser pausado, você pode posicionar o mouse sobre as expressões do código para exibir seu valor atual, inspecionar os locais/inspeções e pilha de chamadas, e usar a barra de ferramentas de depuração para percorrer a execução do código. Pressione **&lt;F5>** para retomar a execução do aplicativo.

## <a name="full-stack-debugging"></a>Depuração de pilha completa

Conforme mencionado anteriormente no tópico, o aplicativo TODO é um aplicativo MEAN - ou seja, o front-end e o back-end são escritos usando JavaScript. Portanto, enquanto você depura o código de back-end (Node/Express), em algum momento, você precisará depurar o código de front-end (Angular). Para essa finalidade, o Visual Studio Code tem um grande ecossistema de extensões, incluindo a depuração do Chrome integrada.

Alterne para a guia **Extensões** e digite `chrome` na caixa de pesquisa:

![Extensão de depuração do Chrome para Visual Studio Code](./media/node-howto-e2e/chrome.png)

Selecione a extensão chamada **Depurador para Chrome**e selecione **Instalar**. Depois de instalar a extensão de depuração do Chrome, selecione **Recarregar** para fechar e reabrir o Visual Studio Code e ativar a extensão. 

![Recarregar o Visual Studio Code depois de instalar a extensão de depuração do Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

Embora você tenha conseguido executar e depurar o código em Node.js sem qualquer configuração específica do Visual Stdio Code, para depurar um aplicativo Web de front-end, você precisa gerar um arquivo `launch.json` que instrui o Visual Studio Code a executar o aplicativo. 

Para gerar o arquivo `launch.json`, alterne para a guia **Depurar**, clique no ícone de engrenagem (que deve ter um pontinho vermelho sobre ele) e selecione o ambiente **Node.js**.

![O Visual Studio Code permite que você configure o arquivo launch.json](./media/node-howto-e2e/debug-gear.png)

Depois de criado, o arquivo `launch.json` se parece com o seguinte, e informa ao Visual Studio Code como iniciar e/ou anexar-se ao aplicativo para depurá-lo. 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

Observe que o Visual Studio Code foi capaz de detectar que o script de inicialização do aplicativo é `server.js`. 

Com o arquivo `launch.json` aberto, selecione **Adicionar Configuração** (canto inferior direito) e selecione **Chrome: Iniciar com userDataDir**.

![Adicionar uma configuração do Chromo ao Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

Adicionar uma nova configuração de execução para o Chromo permite que você depure o código front-end de JavaScript. 

Você pode passar o mouse sobre qualquer uma das configurações especificadas para exibir a documentação sobre o que a configuração faz. Além disso, observe que o Visual Studio Code detecta automaticamente a URL do aplicativo. Atualize a propriedade **webRoot** para `${workspaceRoot}/public`, de modo que o depurador do Chrome saiba onde encontrar os ativos de front-end do aplicativo:

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

Para iniciar/depurar o front e o back-end ao mesmo tempo, crie uma configuração de execução *composta* que informa ao Visual Studio Code qual conjunto de configurações executar em paralelo. 

Adicione o trecho a seguir como uma propriedade de nível superior dentro do arquivo `launch.json` (como um irmão da propriedade **configurações** existente).

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

Os valores de cadeia de caracteres especificados na matriz **compounds.configurations** se referem ao **nome** de entradas individuais na lista de **configurações**. Se você tiver modificado esses nomes, precisará fazer as alterações apropriadas na matriz. Para ver isso em ação, alterne para a guia de depuração e altere a configuração selecionada para **Pilha Completa** (o nome da configuração composta) e pressione **&lt;F5>** para executá-la.

![Executar uma configuração no Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

A execução da configuração inicia o aplicativo Node.js (como pode ser visto na saída do console de depuração) e no Chrome (configurado para navegar até o aplicativo Node.js em `http://localhost:8080`).

Pressione **&lt;Ctrl>P** e insira (ou selecione) `todos.js`, que é o controlador Angular principal para o front-end do aplicativo. 

Defina um ponto de interrupção na linha 11, que é o ponto de entrada para uma nova entrada de tarefas pendentes que está sendo criada.

Retorne ao aplicativo em execução, adicione uma nova entrada de tarefas pendentes e observe que o Visual Studio Code suspendeu a execução dentro do código Angular.

![Depurar o código de front-end no Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

Assim como a depuração de Node.js, você pode passar o mouse sobre as expressões, exibir locais/inspeções, avaliar as expressões no console etc. 

Há dois aspectos importantes a serem observados:

1. O painel **Pilha de Chamadas** exibe duas pilhas diferentes: **Node** e **Chrome**, e indica qual está em pausa no momento.

1. Você pode alternar entre o código de front e de back-end. Para testar isso, pressione **&lt;F5>**, o que causará a execução e a chegada ao ponto de interrupção definido anteriormente na Rota expressa.

Com essa configuração, agora você pode depurar com eficiência o código JavaScript de front, back ou pilha completa diretamente no Visual Studio Code. 

Além disso, o conceito de depurador composto não está limitado a apenas dois processos de destino, e também não está limitado apenas ao JavaScript. Portanto, se estiver trabalhando em um aplicativo de microsserviço (que, possivelmente, é poliglota), você poderá usar exatamente o mesmo fluxo de trabalho (depois de instalar as extensões apropriadas para a linguagem/estrutura).

## <a name="dockerizing-the-app"></a>Colocar o aplicativo em contêineres com o Docker

Esta seção se concentra na experiência fornecida pelo Visual Studio Code para o desenvolvimento com o [Docker](https://www.docker.com/). Os desenvolvedores de Node.js usam o Docker para fornecer implantações de aplicativo portátil para os ambientes de desenvolvimento, CI (integração contínua) e de produção. Como o Docker apresenta uma curva de aprendizado acentuada para algumas pessoas, o Visual Studio Code fornece uma extensão que tenta para ajudar a simplificar um pouco usando o Docker em seus aplicativos.

Volte para a guia **Extensões**, procure por `docker` e selecione a extensão **Docker**. 

Instale a extensão do Docker e recarregue o Visual Studio Code.

![Instalar a extensão do Docker para Visual Studio Code](./media/node-howto-e2e/docker-search.png)

A extensão do Docker para Visual Studio Code inclui um comando para gerar um *Dockerfile* e o arquivo `docker-compose.yml` para um projeto existente. 

Para ver os comandos do Docker disponíveis, exiba a paleta de comandos - usando **&lt;F1>** - e digite `docker`.

![Comandos com suporte da extensão do Docker para Visual Studio ](./media/node-howto-e2e/docker-commands.png)

Selecione **Docker: Adicionar arquivos do docker ao espaço de trabalho**, selecione **Node.js** como a plataforma de aplicativo e especifique que o aplicativo expõe a porta `8080`. 

O comando Docker gera um `Dockerfile` completo e arquivos de composição do Docker que você pode começar a usar imediatamente.

![Dockerfile gerado](./media/node-howto-e2e/docker-file.png)

A extensão do Docker também fornece o preenchimento automático para seus arquivos `Dockerfiles` e `docker-compose.yml`. 

Para ver isso em ação, abra o `Dockerfile` e altere a linha 2 de:

```docker
FROM node:latest
```

Para:

```docker
FROM mhart
```

Com o cursor posicionado após o `t` no `mhart`, pressione **&lt;Ctrl>&lt;Espaço>** para exibir todos os repositórios de imagem publicados pelo `mhart` no DockerHub.

![Preenchimento automático da extensão do Docker](./media/node-howto-e2e/docker-completion.png)

Selecione `mhart/alpine-node`, que fornece tudo o que esse aplicativo precisa. 

Geralmente, as imagens menores são melhores, já que você deseja que os builds e implantações de aplicativo sejam os mais rápidos possíveis, o que agiliza a distribuição e a escala.

Agora, se você gerou o `Dockerfile`, você precisa criar a imagem real do Docker. Outra vez, você pode usar um comando instalado pela extensão do Docker no Visual Studio Code. Pressione **&lt;F1>**, insira `dockerb` na paleta de comandos e selecione o comando **Docker: Compilar Imagem**. Escolha o `/Dockerfile` gerado e modificado. Especifique uma marca que inclui seu nome de usuário no DockerHub (por exemplo, `lostintangent/node`). Pressione **&lt;ENTER>** para iniciar a janela de terminal integrada que exibe a saída da imagem do Docker que está sendo compilada.

![Status de compilação da imagem do Docker](./media/node-howto-e2e/docker-build.png)

Observe que o comando automatizou o processo de execução do `docker build` para você, outro exemplo de aperfeiçoamento de produtividade que você pode optar por usar, ou você pode simplesmente usar a CLI do Docker diretamente. 

Neste ponto, para facilitar a obtenção desta imagem para implantações, você só precisa enviar a imagem por push ao DockerHub. Para fazer isso, verifique se você já autenticou no DockerHub executando `docker login` na CLI e inserindo as credenciais de sua conta. Depois, no Visual Studio Code, exiba a paleta de comandos, insira `dockerpush` e selecione o comando `Docker: Push`. Selecione a marca de imagem que você acabou de criar (por exemplo, `lostintangent/node`) e pressione **&lt;Enter>**. O comando automatiza a chamada de `docker push` e exibe a saída no terminal integrado.

## <a name="deploying-the-app"></a>Implantar o aplicativo

Agora que você colocou o aplicativo em contêineres com o Docker e enviou por push ao DockerHub, precisa implantá-lo na nuvem para que o mundo possa vê-lo. Para isso, use o Serviço de Aplicativo do Azure, que é oferta PaaS do Azure. O Serviço de Aplicativo tem dois recursos que são relevantes para os desenvolvedores de Node.js:

- Suporte para VMs baseadas em Linux, o que reduz a incompatibilidades de aplicativos compilados usando os módulos Node nativos, ou outras ferramentas que podem não oferecer suporte ao Windows e/ou podem apresentar um comportamento diferente.
- Suporte para implantações com base no Docker, o que permite a você especificar o nome de sua imagem do Docker e permite que o Serviço de Aplicativo extraia, implante e dimensione a imagem automaticamente.

Para começar, abra o terminal do Visual Studio. Você usará a nova CLI do Azure 2.0 para gerenciar sua conta do Azure e provisionar a infraestrutura necessária para executar o aplicativo de tarefas pendentes. Depois de entrar em sua conta na CLI usando o comando `az login` (conforme mencionado nos pré-requisitos), execute as etapas a seguir para provisionar a instância do Serviço de Aplicativo e implantar o contêiner do aplicativo de tarefas pendentes:

1. Crie um grupo de recursos, no qual você pode pensar como um *namespace* ou *diretório* para ajudar a organizar os recursos do Azure. A opção `-n` é usada para especificar o nome do grupo, e pode ser qualquer coisa que você quiser.

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > A opção `-l` indica o local do grupo de recursos. Durante a versão prévia, o suporte para o Serviço de Aplicativo no Linux está disponível somente em regiões específicas. Portanto, se você não estiver no Oeste dos EUA, e quiser verificar quais outras regiões estão disponíveis, execute `az appservice list-locations --linux-workers-enabled` na CLI para exibir suas opções de datacenter.

2. Defina o grupo de recursos criado recentemente como o grupo de recursos padrão para que você possa continuar a usar a CLI sem precisar especificar explicitamente o grupo de recursos em cada chamada da CLI:

   ```shell
   az configure -d group=nina-demo
   ```
   
3. Crie o *plano* do Serviço de Aplicativo, que gerencia a criação e o dimensionamento das máquinas virtuais subjacentes nas quais seu aplicativo é implantado. Outra vez, especifique qualquer valor que você deseja para a opção `n`.

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > A opção --is-Linux indica que você deseja máquinas virtuais baseadas em Linux. Sem ela, a CLI assume como padrão o provisionamento de máquinas virtuais baseadas em Windows.

4. Crie o aplicativo Web do Serviço de Aplicativo, que representa o aplicativo de tarefas pendentes real que será executado dentro do plano e do grupo de recursos que você acabou de criar. Pense em um aplicativo Web como o sinônimo de um processo ou contêiner, e o plano como sendo a máquina virtual/host do contêiner no qual ele está em execução. Além disso, como parte da criação do aplicativo Web, você precisará configurá-lo para usar a imagem do Docker que você publicou DockerHub:

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > Se, em vez de usar um contêiner personalizado, você preferir uma implantação do Git, consulte o artigo [Criar um aplicativo Web em Node.js no Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).

5. Defina o aplicativo Web como a instância da Web padrão:

    ```shell
    az configure -d web=nina-demo-app
    ```

6. Inicie o aplicativo para exibir o contêiner implantado, que estará disponível em uma URL `*.azurewebsites.net`:

    ```shell
    az webapp browse
    ```

    ![Aplicativo de tarefas pendentes em execução no navegador](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > Talvez demore alguns minutos para carregar o aplicativo pela primeira vez, pois o Serviço de Aplicativo deve obter a imagem do Docker no DockerHub e, depois, iniciá-la.

Neste ponto, você apenas implantou e executou o aplicativo de tarefas pendentes. 

Agora você implantou o aplicativo de tarefas pendentes. No entanto, o ícone em rotação indica que o aplicativo não pode se conectar ao banco de dados. Isso ocorre porque você estava usando uma instância local do MongoDB durante o desenvolvimento, que, obviamente, não pode ser acessada nos datacenters do Azure. Como você modificou o aplicativo para aceitar a cadeia de conexão por meio de uma variável de ambiente, você só precisa iniciar um servidor do MongoDB e configurar novamente a instância do Serviço de Aplicativo para fazer referência à variável de ambiente. A seção a seguir ilustra isso.

## <a name="provisioning-a-mongodb-server"></a>Provisionamento de um servidor do MongoDB

Embora você possa configurar um servidor do MongoDB, ou conjunto de réplicas, e gerenciar essa infraestrutura por conta própria, o Azure fornece uma solução chamada [Cosmos DB](https://azure.microsoft.com/services/documentdb/). Cosmos DB é um banco de dados NoSQL totalmente gerenciado, com replicação geográfica e alto desempenho que fornece uma camada de compatibilidade do MongoDB. Isso significa que você pode apontar um aplicativo MEAN existente para ele (ou para qualquer ferramenta/cliente MongoDB, como o [Studio 3T](https://studio3t.com/)) sem a necessidade de alterar qualquer coisa, com exceção da cadeia de conexão. As etapas a seguir ilustram como isso é feito:

1. No terminal do Visual Studio Code, execute o seguinte comando para criar uma instância compatível com o MongoDB do serviço Cosmos DB. Substitua o espaço reservado **<NAME>** por um valor globalmente exclusivo (o Cosmos DB usa esse nome para gerar a URL do servidor de banco de dados):

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. Recupere a cadeia de conexão do MongoDB para esta instância:

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. Atualize a variável de ambiente **MONGODB_URL** de seu aplicativo Web para que ele se conecte à instância do Cosmos DB recentemente provisionada, em vez de tentar se conectar a um servidor em execução local do MongoDB (que não existe!):

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. Volte para o navegador e atualize-o. Tente adicionar e remover um item de tarefas pendentes para comprovar que o aplicativo funciona sem a necessidade de alterar qualquer coisa! Defina a variável de ambiente como a instância do Cosmos DB criada, que está emulando totalmente um banco de dados do MongoDB.

    ![Aplicativo de demonstração depois de se conectar a um banco de dados](./media/node-howto-e2e/finished-demo.png)

Quando for necessário, você poderá alternar novamente para a instância do Cosmos DB e escalar verticalmente (para cima ou para baixo) a taxa de transferência reservada que a instância do MongoDB precisa, e se beneficiar do tráfego adicionado sem a necessidade de gerenciar qualquer infraestrutura manualmente.

Além disso, o Cosmos DB indexa automaticamente cada documento e propriedade individual para você. Dessa forma, você não precisa criar o perfil de consultas lentas ou ajustar manualmente seus índices. Provisione e dimensione conforme o necessário, e permita que o Cosmos DB lide com o restante.

## <a name="hosting-a-private-docker-registry"></a>Hospedagem de um Registro privado do Docker

O DockerHub fornece uma experiência incrível para distribuição de suas imagens de contêiner, mas pode haver situações nas quais seria preferível hospedar seu próprio registro particular do Docker - por exemplo para benefícios de desempenho, segurança/governança. Para essa finalidade, o Azure fornece o ACR [(Registro de Contêiner do Azure)](https://azure.microsoft.com/services/container-registry/) que permite que você acelere seu próprio registro do Docker cujo armazenamento de backup está localizado no mesmo data center que o seu aplicativo Web (o que agiliza o pull). O ACR também fornece controle total sobre o conteúdo e os controles de acesso - como quem pode enviar por push ou efetuar o pull de imagens. 

O provisionamento de um registro personalizado pode ser realizado com o comando a seguir. (Substitua o espaço reservado **<NAME>** por um valor globalmente exclusivo, pois o ACR usa o valor especificado para gerar a URL do servidor de logon do registro.

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> Embora o exemplo deste tópico use a **conta do administrador** para simplificar tudo, isso não é recomendável para registros de produção. 

Os comandos `az acr create` exibem a URL do servidor de logon (pela coluna `LOGIN SERVER`) que você usa para fazer logon usando a CLI do Docker (por exemplo, `ninademo.azurecr.io`). Além disso, o comando gera as credenciais de administrador que você pode usar para autenticação. Para recuperar essas credenciais, execute o seguinte comando e anote o nome de usuário e a senha exibidos:

```shell
az acr credential show -n $ACR_NAME
```

Usando as credenciais da etapa anterior, e o servidor de logon individual, você pode fazer logon no registro usando o fluxo de trabalho padrão da CLI do Docker.

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

Agora você pode marcar seu contêiner do Docker para indicar que ele está associado ao registro privado usando o comando a seguir (substituindo `lostintangent/node` pelo nome que você deu à imagem de contêiner.

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

Por fim, envie por push a imagem marcada ao seu registro privado do Docker.

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

Agora, o contêiner é armazenado no registro privado, e a CLI do Docker permitiu que você continue trabalhando da mesma maneira que fez ao usar DockerHub. Para instruir o aplicativo Web do Serviço de Aplicativo a efetuar o pull de seu registro privado, você só precisa executar o comando a seguir:

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> Adicione o prefixo `https://` ao início da opção `-r`. No entanto, não adicione o prefixo ao nome da imagem de contêiner.

Se você atualizar o aplicativo em seu navegador, tudo deverá parecer igual. No entanto, agora ele está executando em seu aplicativo por meio de seu registro privado do Docker. Após a atualização de seu aplicativo, marque e envie por push as alterações, conforme feito acima, e atualize a marca na configuração de contêiner do Serviço de Aplicativo.

## <a name="configuring-a-custom-domain-name"></a>Configurar um nome de domínio personalizado

Embora a URL `*.azurewebsites.net` seja ótima para teste, em algum momento convém adicionar um nome de domínio personalizado ao seu aplicativo Web. Depois que você tiver um nome de domínio de um registrador, você só precisa adicionar um registro `A` a ele que aponte para o IP externo de seu aplicativo Web (que é, na verdade, um balanceador de carga). Recupere esse IP executando o seguinte comando:

```shell
az webapp config hostname get-external-ip
```

Além de adicionar um registro `A`, você também precisa adicionar um registro `TXT` ao seu domínio que aponta para o domínio `*.azurewebsites.net` que você estava usando até o momento. A combinação de registros `A` e `TXT` permite que o Azure verifique se você possui o domínio.

Após a criação desses registros - e da propagação das alterações no DNS - registre o domínio personalizado no Azure, para que ele saiba esperar o tráfego de entrada corretamente. 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> O comando não funcionará até que as alterações no DNS sejam propagadas.

Abra um navegador e navegue até seu domínio personalizado para ver se agora ele resolve para seu aplicativo implantado no Azure.

## <a name="scaling-up-and-out"></a>Escalar vertical e horizontalmente

Em algum momento, seu aplicativo Web poderá se tornar tão popular que os recursos alocados (CPU e RAM) não serão suficientes para lidar com o aumento de tráfego e demandas operacionais. O Plano do Serviço de Aplicativo que você criou anteriormente (**B1**) vem com uma CPU de 1 núcleo e 1,75 GB de RAM, que pode esgotar rapidamente. O plano **B2** vem com duas vezes mais RAM e CPU, portanto, se você notar que seu aplicativo está começando a ficar sem qualquer um dos dois, escale verticalmente a máquina virtual subjacente executando o seguinte comando:

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> Para obter detalhes de preço e especificações do Plano do Aplicativo do Azure, consulte o artigo [Preços do Serviço de Aplicativo](https://azure.microsoft.com/pricing/details/app-service/)

Após alguns minutos, seu aplicativo Web migrará para o hardware solicitado e poderá começar a aproveitar os recursos associados. Além da ampliar, você também pode reduzir executando o mesmo comando mostrado acima, especificando uma opção `--sku` que fornece menos recursos a um preço menor. 

Além de escalar verticalmente as especificações da máquina virtual, desde que seu aplicativo Web seja sem estado, você também terá a opção de *escalar horizontalmente* adicionando mais instâncias de máquina virtual subjacentes. O Plano do Serviço de Aplicativo criado anteriormente incluía apenas uma única máquina virtual (um *trabalho*), e, portanto, todo o tráfego de entrada está sujeito aos limites de recursos disponíveis dessa instância. Se você quiser adicionar uma segunda instância de máquina virtual, execute o mesmo comando executado anteriormente, mas em vez de escalar verticalmente o SKU, escale horizontalmente o número de máquinas virtuais de trabalho.

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

Quando você escala horizontalmente um aplicativo Web como esse, o tráfego de entrada terá sua carga balanceada transparentemente entre todas as instâncias, o que permite que você aumente imediatamente sua capacidade sem quaisquer alterações de código ou preocupação com a infraestrutura necessária. 

Os aplicativos Web sem estado são considerados uma prática recomendada, pois tornam a capacidade de escalá-los (verticalmente ou horizontalmente) totalmente determinística, pois nenhuma máquina virtual ou instância de aplicativo inclui o estado necessário para funcionar. 

> [!NOTE]
> Embora o tutorial deste tópico ilustre a execução de um único aplicativo Web como parte de um Plano do Serviço de Aplicativo, você pode criar e implantar vários aplicativos Web no mesmo plano, permitindo que você provisione e pague por um único plano. 

## <a name="clean-up"></a>Limpar

Para garantir que você não seja cobrado por quaisquer recursos do Azure que não esteja usando, execute o seguinte comando em seu terminal do Visual Studio Code para excluir todos os recursos provisionados durante este tutorial.

```shell
az group delete
```

> [!NOTE]
> A conclusão do processo de limpeza pode demorar vários minutos. 

Após a conclusão, o comando `az group delete` deixa sua conta do Azure no mesmo estado em que estava antes de iniciar o tutorial. A capacidade de organizar, implantar e excluir recursos do Azure como uma única unidade é um dos principais benefícios dos grupos de recursos. Portanto, como uma prática recomendada, agrupe os recursos os quais você prevê que terão o mesmo tempo de vida.