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
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="72b48-103">Desenvolvimento em Node.js com o Visual Studio Code e o Azure</span><span class="sxs-lookup"><span data-stu-id="72b48-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="72b48-104">Este tutorial ilustra como pegar um aplicativo em Node.js existente, "colocá-lo em contêineres" (com o Docker) e, depois, implantá-lo no Azure usando o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="72b48-105">O tutorial usa um aplicativo de tarefas simples criado e publicados por [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span><span class="sxs-lookup"><span data-stu-id="72b48-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="72b48-106">Ele é um aplicativo MEAN de página única e, portanto, usa o MongoDB como seu banco de dados, Node/Express para a API REST/servidor Web e Angular.js 1.x para a interface do usuário de front-end.</span><span class="sxs-lookup"><span data-stu-id="72b48-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="72b48-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="72b48-107">Prerequisites</span></span>

<span data-ttu-id="72b48-108">Para acompanhar a demonstração, você precisará ter estes softwares instalados:</span><span class="sxs-lookup"><span data-stu-id="72b48-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="72b48-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="72b48-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="72b48-110">Docker</span><span class="sxs-lookup"><span data-stu-id="72b48-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="72b48-111">Conta do DockerHub</span><span class="sxs-lookup"><span data-stu-id="72b48-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="72b48-112">CLI 2.0 do Azure</span><span class="sxs-lookup"><span data-stu-id="72b48-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="72b48-113">Conta do Azure</span><span class="sxs-lookup"><span data-stu-id="72b48-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="72b48-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="72b48-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="72b48-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Usado para depurar o front-end do aplicativo de demonstração.</span><span class="sxs-lookup"><span data-stu-id="72b48-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="72b48-116">MongoDB - Como o aplicativo de demonstração usa o MongoDB, você precisa ter uma instância do MongoDB em execução no local escutando na porta `27017` padrão.</span><span class="sxs-lookup"><span data-stu-id="72b48-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="72b48-117">A maneira mais simples de fazer isso é executando os dois comandos a seguir após a instalação do Docker: `docker pull mongo` seguido por `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="72b48-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="72b48-118">Configuração do projeto</span><span class="sxs-lookup"><span data-stu-id="72b48-118">Project setup</span></span>

<span data-ttu-id="72b48-119">Para começar, baixe o exemplo de projeto usando as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="72b48-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="72b48-120">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="72b48-121">Pressione **&lt;F1>** para exibir a paleta de comandos.</span><span class="sxs-lookup"><span data-stu-id="72b48-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="72b48-122">No prompt da paleta de comandos, insira `gitcl`, selecione o comando **Git: Clone** e pressione **&lt;Enter>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Comando gitcl no prompt da paleta de comandos do Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="72b48-124">Quando receber uma solicitação pela **URL do Repositório**, insira `https://github.com/scotch-io/node-todo`, depois, pressione  **&lt;Enter>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="72b48-125">Selecione (ou crie) o diretório local no qual você deseja clonar o projeto.</span><span class="sxs-lookup"><span data-stu-id="72b48-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Gerenciador do Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="72b48-127">Terminal integrado</span><span class="sxs-lookup"><span data-stu-id="72b48-127">Integrated terminal</span></span>

<span data-ttu-id="72b48-128">Como este é um projeto em Node.js, a primeira coisa que você precisa fazer é garantir que todas as dependências do projeto sejam instaladas do npm.</span><span class="sxs-lookup"><span data-stu-id="72b48-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="72b48-129">Pressione **&lt;Ctrl>'** para exibir o terminal integrado do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="72b48-130">Insira `yarn` e pressione **&lt;Enter>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Executar o comando yarn no Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="72b48-132">Controle de versão Git integrado</span><span class="sxs-lookup"><span data-stu-id="72b48-132">Integrated Git version control</span></span>

<span data-ttu-id="72b48-133">Após instalar as dependências do aplicativo por meio do Yarn, um arquivo `yarn.lock` é criado fornecendo uma maneira previsível de readquirir exatamente as mesmas dependências no futuro, sem qualquer surpresas em compilações de CI (integração contínua), implantações de produção ou outros computadores de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="72b48-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="72b48-134">As etapas a seguir ilustram como verificar o arquivo `yarn.lock` no controle do código-fonte:</span><span class="sxs-lookup"><span data-stu-id="72b48-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="72b48-135">No Visual Studio Code, alterne para a guia integrada do Git (a guia com o logotipo do Git).</span><span class="sxs-lookup"><span data-stu-id="72b48-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="72b48-136">Na caixa **Mensagem**, insira uma mensagem de confirmação e pressione **&lt;Ctrl>&lt;Enter>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Adicionar o arquivo yarn.lock ao Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="72b48-138">Projeto e navegação pelo código</span><span class="sxs-lookup"><span data-stu-id="72b48-138">Project and code navigation</span></span>

<span data-ttu-id="72b48-139">Para nos orientarmos dentro da base de código, vamos experimentar alguns exemplos das funcionalidades de navegação fornecidas pelo Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="72b48-140">Pressione **&lt;Ctrl>P**.</span><span class="sxs-lookup"><span data-stu-id="72b48-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="72b48-141">Insira `.js` para exibir todos os arquivos JavaScript/JSON no projeto junto com o diretório pai de cada arquivo</span><span class="sxs-lookup"><span data-stu-id="72b48-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Exibir todos os arquivos .js\*](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="72b48-143">Selecione `server.js`, que é o script de inicialização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="72b48-144">Passe o mouse sobre a variável **database** (importada na linha 6) para ver seu tipo.</span><span class="sxs-lookup"><span data-stu-id="72b48-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="72b48-145">Essa capacidade de inspecionar rapidamente variáveis/módulos/tipos em um arquivo é muito útil durante o desenvolvimento de seus projetos.</span><span class="sxs-lookup"><span data-stu-id="72b48-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Tipo de descoberta](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="72b48-147">Clicar com o mouse dentro do período de uma variável - como **database** -permite que você veja todas as referências a essa variável dentro do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="72b48-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="72b48-148">Para exibir todas as referências a uma variável dentro do projeto, clique com botão direito na variável e, no menu de contexto, selecione **Localizar Todas as Referências**.</span><span class="sxs-lookup"><span data-stu-id="72b48-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Localizar referências a uma variável](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="72b48-150">Além de ser passar o mouse sobre uma variável para descobrir seu tipo, você também pode inspecionar a definição de uma variável, mesmo se estiver em outro arquivo.</span><span class="sxs-lookup"><span data-stu-id="72b48-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="72b48-151">Para ver isso em ação, clique com botão direito em **database.localUrl** (linha 12) e, no menu de contexto, selecione **Inspecionar Definição**.</span><span class="sxs-lookup"><span data-stu-id="72b48-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Inspecionar a definição de uma variável](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="72b48-153">Modificar o código e usar o preenchimento automático</span><span class="sxs-lookup"><span data-stu-id="72b48-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="72b48-154">A cadeia de conexão do MongoDB é codificada na declaração de **database.localUrl**.</span><span class="sxs-lookup"><span data-stu-id="72b48-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="72b48-155">Nesta seção, você modificará o código para recuperar a cadeia de conexão de uma variável de ambiente, e saber mais sobre o recurso de preenchimento automático do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="72b48-156">Abra o arquivo `server.js`</span><span class="sxs-lookup"><span data-stu-id="72b48-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="72b48-157">Substitua o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="72b48-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="72b48-158">por este código:</span><span class="sxs-lookup"><span data-stu-id="72b48-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="72b48-159">Observe que se você digitar o código manualmente (em vez de copiar e colar), ao digitar o ponto após `process`, o Visual Studio Code exibirá os membros disponíveis da API global de **process** em Node.js.</span><span class="sxs-lookup"><span data-stu-id="72b48-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![O preenchimento automático mostra automaticamente os membros de uma API](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="72b48-161">O preenchimento automático funciona porque o Visual Studio Code usa TypeScript nos bastidores - mesmo para JavaScript - a fim de fornecer informações de tipo que podem ser usadas para informar a lista de preenchimento conforme você digita.</span><span class="sxs-lookup"><span data-stu-id="72b48-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="72b48-162">O Visual Studio Code é capaz de detectar que esse é um projeto em Node.js e, como resultado, baixa automaticamente os arquivos de tipificação de TypeScript para [Node.js do NPM](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="72b48-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="72b48-163">O arquivo de tipificação permite que você obtenha o preenchimento automático para outros globais de Node.js, como **Buffer** e **setTimeout**, bem como todos os módulos internos, como **fs** e **http**.</span><span class="sxs-lookup"><span data-stu-id="72b48-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="72b48-164">Além das APIs internas de Node.js, esta aquisição automática de tipificações também funciona para mais de 2.000 módulos de terceiros, como React, Underscore e Express.</span><span class="sxs-lookup"><span data-stu-id="72b48-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="72b48-165">Por exemplo, para impedir que o Mongoose trave o aplicativo de exemplo se ele não conseguir se conectar à instância configurada do banco de dados MongoDB, insira a seguinte linha de código na linha 13:</span><span class="sxs-lookup"><span data-stu-id="72b48-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="72b48-166">Assim como no código anterior, você verá que obterá o preenchimento automático sem qualquer trabalho de sua parte.</span><span class="sxs-lookup"><span data-stu-id="72b48-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![O preenchimento automático mostra automaticamente os membros de uma API](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="72b48-168">Veja quais módulos oferecem suporte a esse recurso de preenchimento automático navegando pelo projeto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), que é o código-fonte conduzido pela comunidade de todas as definições de tipo de TypeScript.</span><span class="sxs-lookup"><span data-stu-id="72b48-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="72b48-169">Executando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="72b48-169">Running the app</span></span>

<span data-ttu-id="72b48-170">Após explorar um pouco o código, é hora de executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="72b48-171">Para executar o aplicativo no Visual Studio Code, pressione **&lt;F5>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="72b48-172">Ao executar o código por meio de **&lt;F5>** (modo de depuração), o Visual Studio Code inicia o aplicativo e exibe a janela **Console de Depuração** com o stdout do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Monitorar o stdout do aplicativo por meio do Console de depuração](./media/node-howto-e2e/console.png)

<span data-ttu-id="72b48-174">Além disso, o **Console de Depuração** é anexado ao aplicativo recém-executado para que você possa digitar as expressões de JavaScript, que serão avaliadas no aplicativo, e também incluir o preenchimento automático.</span><span class="sxs-lookup"><span data-stu-id="72b48-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="72b48-175">Para ver isso em ação, digite `process.env` no console:</span><span class="sxs-lookup"><span data-stu-id="72b48-175">To see this in action, type `process.env` in the console:</span></span>

![Digitar código no Console de depuração](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="72b48-177">Você conseguiu pressionar **&lt;F5>** para executar o aplicativo porque o arquivo aberto no momento é um arquivo JavaScript (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="72b48-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="72b48-178">Como resultado, o Visual Studio Code pressupõe que o projeto é um aplicativo em Node.js.</span><span class="sxs-lookup"><span data-stu-id="72b48-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="72b48-179">Se você fechar todos os arquivos JavaScript no Visual Studio Code e pressionar **&lt;F5>**, o Visual Studio Code consultará você como o ambiente:</span><span class="sxs-lookup"><span data-stu-id="72b48-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Especificar o ambiente do tempo de execução](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="72b48-181">Abra um navegador e navegue até `http://localhost:8080` para ver o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="72b48-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="72b48-182">Digite uma mensagem na caixa de texto e adicione/remova algumas tarefas para ter uma ideia de como o aplicativo funciona.</span><span class="sxs-lookup"><span data-stu-id="72b48-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![Aplicativo de tarefas pendentes em execução](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="72b48-184">Depurando</span><span class="sxs-lookup"><span data-stu-id="72b48-184">Debugging</span></span>

<span data-ttu-id="72b48-185">Além de ser capaz de executar o aplicativo e interagir com ele por meio do console integrado, o Visual Studio Code fornece a capacidade de definir pontos de interrupção diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="72b48-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="72b48-186">Por exemplo, pressione **&lt;Ctrl>P** para exibir o seletor de arquivos.</span><span class="sxs-lookup"><span data-stu-id="72b48-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="72b48-187">Quando o seletor de arquivos for exibido, digite `route` e selecione o arquivo `route.js`.</span><span class="sxs-lookup"><span data-stu-id="72b48-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="72b48-188">Defina um ponto de interrupção na linha 28, que representa a Rota expressa chamada quando o aplicativo tentar adicionar uma entrada de tarefas pendentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="72b48-189">Para definir um ponto de interrupção, basta clicar na área à esquerda do número de linha dentro do editor, como mostra a figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="72b48-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Definir um ponto de interrupção no Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="72b48-191">Além dos pontos de interrupção padrão, o Visual Studio Code oferece suporte a pontos de interrupção condicionais que permitem a personalização do momento de suspensão da execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="72b48-192">Para definir um ponto de interrupção condicional, clique com o direito na área à esquerda da linha na qual você deseja pausar a execução, selecione **Adicionar Ponto de Interrupção Condicional...**  e especifique uma expressão de JavaScript (por exemplo, `foo = "bar"`) ou contagem de execução que define a condição sob a qual você deseja pausar a execução.</span><span class="sxs-lookup"><span data-stu-id="72b48-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="72b48-193">Após a definição do ponto de interrupção, volte ao aplicativo em execução e adicione uma entrada de tarefas pendentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="72b48-194">A adição de uma entrada de tarefas pendentes faz com que o aplicativo suspenda imediatamente a execução na linha 28, onde você definiu o ponto de interrupção:</span><span class="sxs-lookup"><span data-stu-id="72b48-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code pausando a execução em um ponto de interrupção](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="72b48-196">Após o aplicativo ser pausado, você pode posicionar o mouse sobre as expressões do código para exibir seu valor atual, inspecionar os locais/inspeções e pilha de chamadas, e usar a barra de ferramentas de depuração para percorrer a execução do código.</span><span class="sxs-lookup"><span data-stu-id="72b48-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="72b48-197">Pressione **&lt;F5>** para retomar a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="72b48-198">Depuração de pilha completa</span><span class="sxs-lookup"><span data-stu-id="72b48-198">Full-stack debugging</span></span>

<span data-ttu-id="72b48-199">Conforme mencionado anteriormente no tópico, o aplicativo TODO é um aplicativo MEAN - ou seja, o front-end e o back-end são escritos usando JavaScript.</span><span class="sxs-lookup"><span data-stu-id="72b48-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="72b48-200">Portanto, enquanto você depura o código de back-end (Node/Express), em algum momento, você precisará depurar o código de front-end (Angular).</span><span class="sxs-lookup"><span data-stu-id="72b48-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="72b48-201">Para essa finalidade, o Visual Studio Code tem um grande ecossistema de extensões, incluindo a depuração do Chrome integrada.</span><span class="sxs-lookup"><span data-stu-id="72b48-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="72b48-202">Alterne para a guia **Extensões** e digite `chrome` na caixa de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="72b48-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Extensão de depuração do Chrome para Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="72b48-204">Selecione a extensão chamada **Depurador para Chrome**e selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="72b48-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="72b48-205">Depois de instalar a extensão de depuração do Chrome, selecione **Recarregar** para fechar e reabrir o Visual Studio Code e ativar a extensão.</span><span class="sxs-lookup"><span data-stu-id="72b48-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Recarregar o Visual Studio Code depois de instalar a extensão de depuração do Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="72b48-207">Embora você tenha conseguido executar e depurar o código em Node.js sem qualquer configuração específica do Visual Stdio Code, para depurar um aplicativo Web de front-end, você precisa gerar um arquivo `launch.json` que instrui o Visual Studio Code a executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="72b48-208">Para gerar o arquivo `launch.json`, alterne para a guia **Depurar**, clique no ícone de engrenagem (que deve ter um pontinho vermelho sobre ele) e selecione o ambiente **Node.js**.</span><span class="sxs-lookup"><span data-stu-id="72b48-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![O Visual Studio Code permite que você configure o arquivo launch.json](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="72b48-210">Depois de criado, o arquivo `launch.json` se parece com o seguinte, e informa ao Visual Studio Code como iniciar e/ou anexar-se ao aplicativo para depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="72b48-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

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

<span data-ttu-id="72b48-211">Observe que o Visual Studio Code foi capaz de detectar que o script de inicialização do aplicativo é `server.js`.</span><span class="sxs-lookup"><span data-stu-id="72b48-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="72b48-212">Com o arquivo `launch.json` aberto, selecione **Adicionar Configuração** (canto inferior direito) e selecione **Chrome: Iniciar com userDataDir**.</span><span class="sxs-lookup"><span data-stu-id="72b48-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Adicionar uma configuração do Chromo ao Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="72b48-214">Adicionar uma nova configuração de execução para o Chromo permite que você depure o código front-end de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="72b48-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="72b48-215">Você pode passar o mouse sobre qualquer uma das configurações especificadas para exibir a documentação sobre o que a configuração faz.</span><span class="sxs-lookup"><span data-stu-id="72b48-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="72b48-216">Além disso, observe que o Visual Studio Code detecta automaticamente a URL do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="72b48-217">Atualize a propriedade **webRoot** para `${workspaceRoot}/public`, de modo que o depurador do Chrome saiba onde encontrar os ativos de front-end do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="72b48-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

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

<span data-ttu-id="72b48-218">Para iniciar/depurar o front e o back-end ao mesmo tempo, crie uma configuração de execução *composta* que informa ao Visual Studio Code qual conjunto de configurações executar em paralelo.</span><span class="sxs-lookup"><span data-stu-id="72b48-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="72b48-219">Adicione o trecho a seguir como uma propriedade de nível superior dentro do arquivo `launch.json` (como um irmão da propriedade **configurações** existente).</span><span class="sxs-lookup"><span data-stu-id="72b48-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="72b48-220">Os valores de cadeia de caracteres especificados na matriz **compounds.configurations** se referem ao **nome** de entradas individuais na lista de **configurações**.</span><span class="sxs-lookup"><span data-stu-id="72b48-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="72b48-221">Se você tiver modificado esses nomes, precisará fazer as alterações apropriadas na matriz.</span><span class="sxs-lookup"><span data-stu-id="72b48-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="72b48-222">Para ver isso em ação, alterne para a guia de depuração e altere a configuração selecionada para **Pilha Completa** (o nome da configuração composta) e pressione **&lt;F5>** para executá-la.</span><span class="sxs-lookup"><span data-stu-id="72b48-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Executar uma configuração no Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="72b48-224">A execução da configuração inicia o aplicativo Node.js (como pode ser visto na saída do console de depuração) e no Chrome (configurado para navegar até o aplicativo Node.js em `http://localhost:8080`).</span><span class="sxs-lookup"><span data-stu-id="72b48-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="72b48-225">Pressione **&lt;Ctrl>P** e insira (ou selecione) `todos.js`, que é o controlador Angular principal para o front-end do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="72b48-226">Defina um ponto de interrupção na linha 11, que é o ponto de entrada para uma nova entrada de tarefas pendentes que está sendo criada.</span><span class="sxs-lookup"><span data-stu-id="72b48-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="72b48-227">Retorne ao aplicativo em execução, adicione uma nova entrada de tarefas pendentes e observe que o Visual Studio Code suspendeu a execução dentro do código Angular.</span><span class="sxs-lookup"><span data-stu-id="72b48-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Depurar o código de front-end no Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="72b48-229">Assim como a depuração de Node.js, você pode passar o mouse sobre as expressões, exibir locais/inspeções, avaliar as expressões no console etc.</span><span class="sxs-lookup"><span data-stu-id="72b48-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="72b48-230">Há dois aspectos importantes a serem observados:</span><span class="sxs-lookup"><span data-stu-id="72b48-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="72b48-231">O painel **Pilha de Chamadas** exibe duas pilhas diferentes: **Node** e **Chrome**, e indica qual está em pausa no momento.</span><span class="sxs-lookup"><span data-stu-id="72b48-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="72b48-232">Você pode alternar entre o código de front e de back-end.</span><span class="sxs-lookup"><span data-stu-id="72b48-232">You can step between front and back-end code.</span></span> <span data-ttu-id="72b48-233">Para testar isso, pressione **&lt;F5>**, o que causará a execução e a chegada ao ponto de interrupção definido anteriormente na Rota expressa.</span><span class="sxs-lookup"><span data-stu-id="72b48-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="72b48-234">Com essa configuração, agora você pode depurar com eficiência o código JavaScript de front, back ou pilha completa diretamente no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="72b48-235">Além disso, o conceito de depurador composto não está limitado a apenas dois processos de destino, e também não está limitado apenas ao JavaScript.</span><span class="sxs-lookup"><span data-stu-id="72b48-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="72b48-236">Portanto, se estiver trabalhando em um aplicativo de microsserviço (que, possivelmente, é poliglota), você poderá usar exatamente o mesmo fluxo de trabalho (depois de instalar as extensões apropriadas para a linguagem/estrutura).</span><span class="sxs-lookup"><span data-stu-id="72b48-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="72b48-237">Colocar o aplicativo em contêineres com o Docker</span><span class="sxs-lookup"><span data-stu-id="72b48-237">Dockerizing the app</span></span>

<span data-ttu-id="72b48-238">Esta seção se concentra na experiência fornecida pelo Visual Studio Code para o desenvolvimento com o [Docker](https://www.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="72b48-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="72b48-239">Os desenvolvedores de Node.js usam o Docker para fornecer implantações de aplicativo portátil para os ambientes de desenvolvimento, CI (integração contínua) e de produção.</span><span class="sxs-lookup"><span data-stu-id="72b48-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="72b48-240">Como o Docker apresenta uma curva de aprendizado acentuada para algumas pessoas, o Visual Studio Code fornece uma extensão que tenta para ajudar a simplificar um pouco usando o Docker em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="72b48-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="72b48-241">Volte para a guia **Extensões**, procure por `docker` e selecione a extensão **Docker**.</span><span class="sxs-lookup"><span data-stu-id="72b48-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="72b48-242">Instale a extensão do Docker e recarregue o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Instalar a extensão do Docker para Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="72b48-244">A extensão do Docker para Visual Studio Code inclui um comando para gerar um *Dockerfile* e o arquivo `docker-compose.yml` para um projeto existente.</span><span class="sxs-lookup"><span data-stu-id="72b48-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="72b48-245">Para ver os comandos do Docker disponíveis, exiba a paleta de comandos - usando **&lt;F1>** - e digite `docker`.</span><span class="sxs-lookup"><span data-stu-id="72b48-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="72b48-246">Comandos com suporte da extensão do Docker para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72b48-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="72b48-247">Selecione **Docker: Adicionar arquivos do docker ao espaço de trabalho**, selecione **Node.js** como a plataforma de aplicativo e especifique que o aplicativo expõe a porta `8080`.</span><span class="sxs-lookup"><span data-stu-id="72b48-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="72b48-248">O comando Docker gera um `Dockerfile` completo e arquivos de composição do Docker que você pode começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="72b48-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Dockerfile gerado](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="72b48-250">A extensão do Docker também fornece o preenchimento automático para seus arquivos `Dockerfiles` e `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="72b48-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="72b48-251">Para ver isso em ação, abra o `Dockerfile` e altere a linha 2 de:</span><span class="sxs-lookup"><span data-stu-id="72b48-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="72b48-252">Para:</span><span class="sxs-lookup"><span data-stu-id="72b48-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="72b48-253">Com o cursor posicionado após o `t` no `mhart`, pressione **&lt;Ctrl>&lt;Espaço>** para exibir todos os repositórios de imagem publicados pelo `mhart` no DockerHub.</span><span class="sxs-lookup"><span data-stu-id="72b48-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Preenchimento automático da extensão do Docker](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="72b48-255">Selecione `mhart/alpine-node`, que fornece tudo o que esse aplicativo precisa.</span><span class="sxs-lookup"><span data-stu-id="72b48-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="72b48-256">Geralmente, as imagens menores são melhores, já que você deseja que os builds e implantações de aplicativo sejam os mais rápidos possíveis, o que agiliza a distribuição e a escala.</span><span class="sxs-lookup"><span data-stu-id="72b48-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="72b48-257">Agora, se você gerou o `Dockerfile`, você precisa criar a imagem real do Docker.</span><span class="sxs-lookup"><span data-stu-id="72b48-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="72b48-258">Outra vez, você pode usar um comando instalado pela extensão do Docker no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="72b48-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="72b48-259">Pressione **&lt;F1>**, insira `dockerb` na paleta de comandos e selecione o comando **Docker: Compilar Imagem**.</span><span class="sxs-lookup"><span data-stu-id="72b48-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="72b48-260">Escolha o `/Dockerfile` gerado e modificado.</span><span class="sxs-lookup"><span data-stu-id="72b48-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="72b48-261">Especifique uma marca que inclui seu nome de usuário no DockerHub (por exemplo, `lostintangent/node`).</span><span class="sxs-lookup"><span data-stu-id="72b48-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="72b48-262">Pressione **&lt;ENTER>** para iniciar a janela de terminal integrada que exibe a saída da imagem do Docker que está sendo compilada.</span><span class="sxs-lookup"><span data-stu-id="72b48-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Status de compilação da imagem do Docker](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="72b48-264">Observe que o comando automatizou o processo de execução do `docker build` para você, outro exemplo de aperfeiçoamento de produtividade que você pode optar por usar, ou você pode simplesmente usar a CLI do Docker diretamente.</span><span class="sxs-lookup"><span data-stu-id="72b48-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="72b48-265">Neste ponto, para facilitar a obtenção desta imagem para implantações, você só precisa enviar a imagem por push ao DockerHub.</span><span class="sxs-lookup"><span data-stu-id="72b48-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="72b48-266">Para fazer isso, verifique se você já autenticou no DockerHub executando `docker login` na CLI e inserindo as credenciais de sua conta.</span><span class="sxs-lookup"><span data-stu-id="72b48-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="72b48-267">Depois, no Visual Studio Code, exiba a paleta de comandos, insira `dockerpush` e selecione o comando `Docker: Push`.</span><span class="sxs-lookup"><span data-stu-id="72b48-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="72b48-268">Selecione a marca de imagem que você acabou de criar (por exemplo, `lostintangent/node`) e pressione **&lt;Enter>**.</span><span class="sxs-lookup"><span data-stu-id="72b48-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="72b48-269">O comando automatiza a chamada de `docker push` e exibe a saída no terminal integrado.</span><span class="sxs-lookup"><span data-stu-id="72b48-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="72b48-270">Implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="72b48-270">Deploying the app</span></span>

<span data-ttu-id="72b48-271">Agora que você colocou o aplicativo em contêineres com o Docker e enviou por push ao DockerHub, precisa implantá-lo na nuvem para que o mundo possa vê-lo.</span><span class="sxs-lookup"><span data-stu-id="72b48-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="72b48-272">Para isso, use o Serviço de Aplicativo do Azure, que é oferta PaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="72b48-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="72b48-273">O Serviço de Aplicativo tem dois recursos que são relevantes para os desenvolvedores de Node.js:</span><span class="sxs-lookup"><span data-stu-id="72b48-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="72b48-274">Suporte para VMs baseadas em Linux, o que reduz a incompatibilidades de aplicativos compilados usando os módulos Node nativos, ou outras ferramentas que podem não oferecer suporte ao Windows e/ou podem apresentar um comportamento diferente.</span><span class="sxs-lookup"><span data-stu-id="72b48-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="72b48-275">Suporte para implantações com base no Docker, o que permite a você especificar o nome de sua imagem do Docker e permite que o Serviço de Aplicativo extraia, implante e dimensione a imagem automaticamente.</span><span class="sxs-lookup"><span data-stu-id="72b48-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="72b48-276">Para começar, abra o terminal do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72b48-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="72b48-277">Você usará a nova CLI do Azure 2.0 para gerenciar sua conta do Azure e provisionar a infraestrutura necessária para executar o aplicativo de tarefas pendentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="72b48-278">Depois de entrar em sua conta na CLI usando o comando `az login` (conforme mencionado nos pré-requisitos), execute as etapas a seguir para provisionar a instância do Serviço de Aplicativo e implantar o contêiner do aplicativo de tarefas pendentes:</span><span class="sxs-lookup"><span data-stu-id="72b48-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="72b48-279">Crie um grupo de recursos, no qual você pode pensar como um *namespace* ou *diretório* para ajudar a organizar os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="72b48-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="72b48-280">A opção `-n` é usada para especificar o nome do grupo, e pode ser qualquer coisa que você quiser.</span><span class="sxs-lookup"><span data-stu-id="72b48-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="72b48-281">A opção `-l` indica o local do grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="72b48-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="72b48-282">Durante a versão prévia, o suporte para o Serviço de Aplicativo no Linux está disponível somente em regiões específicas.</span><span class="sxs-lookup"><span data-stu-id="72b48-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="72b48-283">Portanto, se você não estiver no Oeste dos EUA, e quiser verificar quais outras regiões estão disponíveis, execute `az appservice list-locations --linux-workers-enabled` na CLI para exibir suas opções de datacenter.</span><span class="sxs-lookup"><span data-stu-id="72b48-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="72b48-284">Defina o grupo de recursos criado recentemente como o grupo de recursos padrão para que você possa continuar a usar a CLI sem precisar especificar explicitamente o grupo de recursos em cada chamada da CLI:</span><span class="sxs-lookup"><span data-stu-id="72b48-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="72b48-285">Crie o *plano* do Serviço de Aplicativo, que gerencia a criação e o dimensionamento das máquinas virtuais subjacentes nas quais seu aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="72b48-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="72b48-286">Outra vez, especifique qualquer valor que você deseja para a opção `n`.</span><span class="sxs-lookup"><span data-stu-id="72b48-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="72b48-287">A opção --is-Linux indica que você deseja máquinas virtuais baseadas em Linux.</span><span class="sxs-lookup"><span data-stu-id="72b48-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="72b48-288">Sem ela, a CLI assume como padrão o provisionamento de máquinas virtuais baseadas em Windows.</span><span class="sxs-lookup"><span data-stu-id="72b48-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="72b48-289">Crie o aplicativo Web do Serviço de Aplicativo, que representa o aplicativo de tarefas pendentes real que será executado dentro do plano e do grupo de recursos que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="72b48-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="72b48-290">Pense em um aplicativo Web como o sinônimo de um processo ou contêiner, e o plano como sendo a máquina virtual/host do contêiner no qual ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="72b48-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="72b48-291">Além disso, como parte da criação do aplicativo Web, você precisará configurá-lo para usar a imagem do Docker que você publicou DockerHub:</span><span class="sxs-lookup"><span data-stu-id="72b48-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="72b48-292">Se, em vez de usar um contêiner personalizado, você preferir uma implantação do Git, consulte o artigo [Criar um aplicativo Web em Node.js no Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span><span class="sxs-lookup"><span data-stu-id="72b48-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="72b48-293">Defina o aplicativo Web como a instância da Web padrão:</span><span class="sxs-lookup"><span data-stu-id="72b48-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="72b48-294">Inicie o aplicativo para exibir o contêiner implantado, que estará disponível em uma URL `*.azurewebsites.net`:</span><span class="sxs-lookup"><span data-stu-id="72b48-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![Aplicativo de tarefas pendentes em execução no navegador](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="72b48-296">Talvez demore alguns minutos para carregar o aplicativo pela primeira vez, pois o Serviço de Aplicativo deve obter a imagem do Docker no DockerHub e, depois, iniciá-la.</span><span class="sxs-lookup"><span data-stu-id="72b48-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="72b48-297">Neste ponto, você apenas implantou e executou o aplicativo de tarefas pendentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="72b48-298">Agora você implantou o aplicativo de tarefas pendentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-298">You have now deployed the todo app.</span></span> <span data-ttu-id="72b48-299">No entanto, o ícone em rotação indica que o aplicativo não pode se conectar ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="72b48-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="72b48-300">Isso ocorre porque você estava usando uma instância local do MongoDB durante o desenvolvimento, que, obviamente, não pode ser acessada nos datacenters do Azure.</span><span class="sxs-lookup"><span data-stu-id="72b48-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="72b48-301">Como você modificou o aplicativo para aceitar a cadeia de conexão por meio de uma variável de ambiente, você só precisa iniciar um servidor do MongoDB e configurar novamente a instância do Serviço de Aplicativo para fazer referência à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="72b48-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="72b48-302">A seção a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="72b48-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="72b48-303">Provisionamento de um servidor do MongoDB</span><span class="sxs-lookup"><span data-stu-id="72b48-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="72b48-304">Embora você possa configurar um servidor do MongoDB, ou conjunto de réplicas, e gerenciar essa infraestrutura por conta própria, o Azure fornece uma solução chamada [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span><span class="sxs-lookup"><span data-stu-id="72b48-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="72b48-305">Cosmos DB é um banco de dados NoSQL totalmente gerenciado, com replicação geográfica e alto desempenho que fornece uma camada de compatibilidade do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="72b48-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="72b48-306">Isso significa que você pode apontar um aplicativo MEAN existente para ele (ou para qualquer ferramenta/cliente MongoDB, como o [Studio 3T](https://studio3t.com/)) sem a necessidade de alterar qualquer coisa, com exceção da cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="72b48-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="72b48-307">As etapas a seguir ilustram como isso é feito:</span><span class="sxs-lookup"><span data-stu-id="72b48-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="72b48-308">No terminal do Visual Studio Code, execute o seguinte comando para criar uma instância compatível com o MongoDB do serviço Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="72b48-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="72b48-309">Substitua o espaço reservado **<NAME>** por um valor globalmente exclusivo (o Cosmos DB usa esse nome para gerar a URL do servidor de banco de dados):</span><span class="sxs-lookup"><span data-stu-id="72b48-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="72b48-310">Recupere a cadeia de conexão do MongoDB para esta instância:</span><span class="sxs-lookup"><span data-stu-id="72b48-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="72b48-311">Atualize a variável de ambiente **MONGODB_URL** de seu aplicativo Web para que ele se conecte à instância do Cosmos DB recentemente provisionada, em vez de tentar se conectar a um servidor em execução local do MongoDB (que não existe!):</span><span class="sxs-lookup"><span data-stu-id="72b48-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="72b48-312">Volte para o navegador e atualize-o.</span><span class="sxs-lookup"><span data-stu-id="72b48-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="72b48-313">Tente adicionar e remover um item de tarefas pendentes para comprovar que o aplicativo funciona sem a necessidade de alterar qualquer coisa!</span><span class="sxs-lookup"><span data-stu-id="72b48-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="72b48-314">Defina a variável de ambiente como a instância do Cosmos DB criada, que está emulando totalmente um banco de dados do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="72b48-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![Aplicativo de demonstração depois de se conectar a um banco de dados](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="72b48-316">Quando for necessário, você poderá alternar novamente para a instância do Cosmos DB e escalar verticalmente (para cima ou para baixo) a taxa de transferência reservada que a instância do MongoDB precisa, e se beneficiar do tráfego adicionado sem a necessidade de gerenciar qualquer infraestrutura manualmente.</span><span class="sxs-lookup"><span data-stu-id="72b48-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="72b48-317">Além disso, o Cosmos DB indexa automaticamente cada documento e propriedade individual para você.</span><span class="sxs-lookup"><span data-stu-id="72b48-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="72b48-318">Dessa forma, você não precisa criar o perfil de consultas lentas ou ajustar manualmente seus índices.</span><span class="sxs-lookup"><span data-stu-id="72b48-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="72b48-319">Provisione e dimensione conforme o necessário, e permita que o Cosmos DB lide com o restante.</span><span class="sxs-lookup"><span data-stu-id="72b48-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="72b48-320">Hospedagem de um Registro privado do Docker</span><span class="sxs-lookup"><span data-stu-id="72b48-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="72b48-321">O DockerHub fornece uma experiência incrível para distribuição de suas imagens de contêiner, mas pode haver situações nas quais seria preferível hospedar seu próprio registro particular do Docker - por exemplo para benefícios de desempenho, segurança/governança.</span><span class="sxs-lookup"><span data-stu-id="72b48-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="72b48-322">Para essa finalidade, o Azure fornece o ACR [(Registro de Contêiner do Azure)](https://azure.microsoft.com/services/container-registry/) que permite que você acelere seu próprio registro do Docker cujo armazenamento de backup está localizado no mesmo data center que o seu aplicativo Web (o que agiliza o pull).</span><span class="sxs-lookup"><span data-stu-id="72b48-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="72b48-323">O ACR também fornece controle total sobre o conteúdo e os controles de acesso - como quem pode enviar por push ou efetuar o pull de imagens.</span><span class="sxs-lookup"><span data-stu-id="72b48-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="72b48-324">O provisionamento de um registro personalizado pode ser realizado com o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="72b48-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="72b48-325">(Substitua o espaço reservado **<NAME>** por um valor globalmente exclusivo, pois o ACR usa o valor especificado para gerar a URL do servidor de logon do registro.</span><span class="sxs-lookup"><span data-stu-id="72b48-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="72b48-326">Embora o exemplo deste tópico use a **conta do administrador** para simplificar tudo, isso não é recomendável para registros de produção.</span><span class="sxs-lookup"><span data-stu-id="72b48-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="72b48-327">Os comandos `az acr create` exibem a URL do servidor de logon (pela coluna `LOGIN SERVER`) que você usa para fazer logon usando a CLI do Docker (por exemplo, `ninademo.azurecr.io`).</span><span class="sxs-lookup"><span data-stu-id="72b48-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="72b48-328">Além disso, o comando gera as credenciais de administrador que você pode usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="72b48-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="72b48-329">Para recuperar essas credenciais, execute o seguinte comando e anote o nome de usuário e a senha exibidos:</span><span class="sxs-lookup"><span data-stu-id="72b48-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="72b48-330">Usando as credenciais da etapa anterior, e o servidor de logon individual, você pode fazer logon no registro usando o fluxo de trabalho padrão da CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="72b48-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="72b48-331">Agora você pode marcar seu contêiner do Docker para indicar que ele está associado ao registro privado usando o comando a seguir (substituindo `lostintangent/node` pelo nome que você deu à imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="72b48-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="72b48-332">Por fim, envie por push a imagem marcada ao seu registro privado do Docker.</span><span class="sxs-lookup"><span data-stu-id="72b48-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="72b48-333">Agora, o contêiner é armazenado no registro privado, e a CLI do Docker permitiu que você continue trabalhando da mesma maneira que fez ao usar DockerHub.</span><span class="sxs-lookup"><span data-stu-id="72b48-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="72b48-334">Para instruir o aplicativo Web do Serviço de Aplicativo a efetuar o pull de seu registro privado, você só precisa executar o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="72b48-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="72b48-335">Adicione o prefixo `https://` ao início da opção `-r`.</span><span class="sxs-lookup"><span data-stu-id="72b48-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="72b48-336">No entanto, não adicione o prefixo ao nome da imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="72b48-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="72b48-337">Se você atualizar o aplicativo em seu navegador, tudo deverá parecer igual.</span><span class="sxs-lookup"><span data-stu-id="72b48-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="72b48-338">No entanto, agora ele está executando em seu aplicativo por meio de seu registro privado do Docker.</span><span class="sxs-lookup"><span data-stu-id="72b48-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="72b48-339">Após a atualização de seu aplicativo, marque e envie por push as alterações, conforme feito acima, e atualize a marca na configuração de contêiner do Serviço de Aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b48-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="72b48-340">Configurar um nome de domínio personalizado</span><span class="sxs-lookup"><span data-stu-id="72b48-340">Configuring a custom domain name</span></span>

<span data-ttu-id="72b48-341">Embora a URL `*.azurewebsites.net` seja ótima para teste, em algum momento convém adicionar um nome de domínio personalizado ao seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="72b48-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="72b48-342">Depois que você tiver um nome de domínio de um registrador, você só precisa adicionar um registro `A` a ele que aponte para o IP externo de seu aplicativo Web (que é, na verdade, um balanceador de carga).</span><span class="sxs-lookup"><span data-stu-id="72b48-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="72b48-343">Recupere esse IP executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="72b48-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="72b48-344">Além de adicionar um registro `A`, você também precisa adicionar um registro `TXT` ao seu domínio que aponta para o domínio `*.azurewebsites.net` que você estava usando até o momento.</span><span class="sxs-lookup"><span data-stu-id="72b48-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="72b48-345">A combinação de registros `A` e `TXT` permite que o Azure verifique se você possui o domínio.</span><span class="sxs-lookup"><span data-stu-id="72b48-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="72b48-346">Após a criação desses registros - e da propagação das alterações no DNS - registre o domínio personalizado no Azure, para que ele saiba esperar o tráfego de entrada corretamente.</span><span class="sxs-lookup"><span data-stu-id="72b48-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="72b48-347">O comando não funcionará até que as alterações no DNS sejam propagadas.</span><span class="sxs-lookup"><span data-stu-id="72b48-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="72b48-348">Abra um navegador e navegue até seu domínio personalizado para ver se agora ele resolve para seu aplicativo implantado no Azure.</span><span class="sxs-lookup"><span data-stu-id="72b48-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="72b48-349">Escalar vertical e horizontalmente</span><span class="sxs-lookup"><span data-stu-id="72b48-349">Scaling up and out</span></span>

<span data-ttu-id="72b48-350">Em algum momento, seu aplicativo Web poderá se tornar tão popular que os recursos alocados (CPU e RAM) não serão suficientes para lidar com o aumento de tráfego e demandas operacionais.</span><span class="sxs-lookup"><span data-stu-id="72b48-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="72b48-351">O Plano do Serviço de Aplicativo que você criou anteriormente (**B1**) vem com uma CPU de 1 núcleo e 1,75 GB de RAM, que pode esgotar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="72b48-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="72b48-352">O plano **B2** vem com duas vezes mais RAM e CPU, portanto, se você notar que seu aplicativo está começando a ficar sem qualquer um dos dois, escale verticalmente a máquina virtual subjacente executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="72b48-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="72b48-353">Para obter detalhes de preço e especificações do Plano do Aplicativo do Azure, consulte o artigo [Preços do Serviço de Aplicativo](https://azure.microsoft.com/pricing/details/app-service/)</span><span class="sxs-lookup"><span data-stu-id="72b48-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="72b48-354">Após alguns minutos, seu aplicativo Web migrará para o hardware solicitado e poderá começar a aproveitar os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="72b48-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="72b48-355">Além da ampliar, você também pode reduzir executando o mesmo comando mostrado acima, especificando uma opção `--sku` que fornece menos recursos a um preço menor.</span><span class="sxs-lookup"><span data-stu-id="72b48-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="72b48-356">Além de escalar verticalmente as especificações da máquina virtual, desde que seu aplicativo Web seja sem estado, você também terá a opção de *escalar horizontalmente* adicionando mais instâncias de máquina virtual subjacentes.</span><span class="sxs-lookup"><span data-stu-id="72b48-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="72b48-357">O Plano do Serviço de Aplicativo criado anteriormente incluía apenas uma única máquina virtual (um *trabalho*), e, portanto, todo o tráfego de entrada está sujeito aos limites de recursos disponíveis dessa instância.</span><span class="sxs-lookup"><span data-stu-id="72b48-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="72b48-358">Se você quiser adicionar uma segunda instância de máquina virtual, execute o mesmo comando executado anteriormente, mas em vez de escalar verticalmente o SKU, escale horizontalmente o número de máquinas virtuais de trabalho.</span><span class="sxs-lookup"><span data-stu-id="72b48-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="72b48-359">Quando você escala horizontalmente um aplicativo Web como esse, o tráfego de entrada terá sua carga balanceada transparentemente entre todas as instâncias, o que permite que você aumente imediatamente sua capacidade sem quaisquer alterações de código ou preocupação com a infraestrutura necessária.</span><span class="sxs-lookup"><span data-stu-id="72b48-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="72b48-360">Os aplicativos Web sem estado são considerados uma prática recomendada, pois tornam a capacidade de escalá-los (verticalmente ou horizontalmente) totalmente determinística, pois nenhuma máquina virtual ou instância de aplicativo inclui o estado necessário para funcionar.</span><span class="sxs-lookup"><span data-stu-id="72b48-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="72b48-361">Embora o tutorial deste tópico ilustre a execução de um único aplicativo Web como parte de um Plano do Serviço de Aplicativo, você pode criar e implantar vários aplicativos Web no mesmo plano, permitindo que você provisione e pague por um único plano.</span><span class="sxs-lookup"><span data-stu-id="72b48-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="72b48-362">Limpar</span><span class="sxs-lookup"><span data-stu-id="72b48-362">Clean-up</span></span>

<span data-ttu-id="72b48-363">Para garantir que você não seja cobrado por quaisquer recursos do Azure que não esteja usando, execute o seguinte comando em seu terminal do Visual Studio Code para excluir todos os recursos provisionados durante este tutorial.</span><span class="sxs-lookup"><span data-stu-id="72b48-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="72b48-364">A conclusão do processo de limpeza pode demorar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="72b48-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="72b48-365">Após a conclusão, o comando `az group delete` deixa sua conta do Azure no mesmo estado em que estava antes de iniciar o tutorial.</span><span class="sxs-lookup"><span data-stu-id="72b48-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="72b48-366">A capacidade de organizar, implantar e excluir recursos do Azure como uma única unidade é um dos principais benefícios dos grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="72b48-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="72b48-367">Portanto, como uma prática recomendada, agrupe os recursos os quais você prevê que terão o mesmo tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="72b48-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>