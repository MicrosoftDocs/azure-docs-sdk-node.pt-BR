---
title: "Módulos de Automação do Azure para Node.js"
description: "Referência dos módulos da Automação do Azure para Node.js"
keywords: "Azure, SDK, API, Automação, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="bd745-104">Módulos de Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="bd745-104">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bd745-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bd745-105">Overview</span></span>

<span data-ttu-id="bd745-106">A Automação do Azure fornece uma maneira para os usuários automatizarem tarefas manuais, longas, sujeitas a erros e repetidas com frequência que normalmente são executadas em um ambiente de nuvem e corporativo.</span><span class="sxs-lookup"><span data-stu-id="bd745-106">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="bd745-107">A Automação economiza tempo e aumenta a confiabilidade das tarefas administrativas regulares e até mesmo agenda a sua execução automática em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="bd745-107">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="bd745-108">Você pode automatizar processos usando runbooks ou automatizar o gerenciamento de configuração usando Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="bd745-108">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd745-109">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bd745-109">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="bd745-110">Instalar os módulos com npm</span><span class="sxs-lookup"><span data-stu-id="bd745-110">Install the modules with npm</span></span>

<span data-ttu-id="bd745-111">Usar o npm para instalar os módulos da Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="bd745-111">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="bd745-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd745-112">Example</span></span>

<span data-ttu-id="bd745-113">Este exemplo lista as contas de automação.</span><span class="sxs-lookup"><span data-stu-id="bd745-113">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="bd745-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bd745-114">Samples</span></span>

<span data-ttu-id="bd745-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bd745-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
