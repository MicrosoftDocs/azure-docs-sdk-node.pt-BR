---
title: "Módulos de Automação do Azure para Node.js"
description: "Referência dos módulos da Automação do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 09e9d2675d49b29881d332e7bbf251a5031e3483
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="c9305-103">Módulos de Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="c9305-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c9305-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c9305-104">Overview</span></span>

<span data-ttu-id="c9305-105">A Automação do Azure fornece uma maneira para os usuários automatizarem tarefas manuais, longas, sujeitas a erros e repetidas com frequência que normalmente são executadas em um ambiente de nuvem e corporativo.</span><span class="sxs-lookup"><span data-stu-id="c9305-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="c9305-106">A Automação economiza tempo e aumenta a confiabilidade das tarefas administrativas regulares e até mesmo agenda a sua execução automática em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="c9305-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="c9305-107">Você pode automatizar processos usando runbooks ou automatizar o gerenciamento de configuração usando Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="c9305-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="c9305-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c9305-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="c9305-109">Instalar os módulos com npm</span><span class="sxs-lookup"><span data-stu-id="c9305-109">Install the modules with npm</span></span>

<span data-ttu-id="c9305-110">Usar o npm para instalar os módulos da Automação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="c9305-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="c9305-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9305-111">Example</span></span>

<span data-ttu-id="c9305-112">Este exemplo lista as contas de automação.</span><span class="sxs-lookup"><span data-stu-id="c9305-112">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c9305-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c9305-113">Samples</span></span>

<span data-ttu-id="c9305-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c9305-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
