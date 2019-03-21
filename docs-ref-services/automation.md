---
title: Módulos de Automação do Azure para Node.js
description: Referência dos módulos da Automação do Azure para Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 281b5081163fc3b0b74219c766ff9be5c421296b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052598"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="ce71d-103">Módulos de Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="ce71d-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ce71d-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ce71d-104">Overview</span></span>

<span data-ttu-id="ce71d-105">A Automação do Azure fornece uma maneira para os usuários automatizarem tarefas manuais, longas, sujeitas a erros e repetidas com frequência que normalmente são executadas em um ambiente de nuvem e corporativo.</span><span class="sxs-lookup"><span data-stu-id="ce71d-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="ce71d-106">A Automação economiza tempo e aumenta a confiabilidade das tarefas administrativas regulares e até mesmo agenda a sua execução automática em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="ce71d-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="ce71d-107">Você pode automatizar processos usando runbooks ou automatizar o gerenciamento de configuração usando Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="ce71d-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="ce71d-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ce71d-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="ce71d-109">Instalar os módulos com npm</span><span class="sxs-lookup"><span data-stu-id="ce71d-109">Install the modules with npm</span></span>

<span data-ttu-id="ce71d-110">Usar o npm para instalar os módulos da Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="ce71d-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="ce71d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce71d-111">Example</span></span>

<span data-ttu-id="ce71d-112">Este exemplo lista as contas de automação.</span><span class="sxs-lookup"><span data-stu-id="ce71d-112">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ce71d-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ce71d-113">Samples</span></span>

<span data-ttu-id="ce71d-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ce71d-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
