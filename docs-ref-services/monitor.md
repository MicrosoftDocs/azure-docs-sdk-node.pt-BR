---
title: "Módulos do Azure Monitor para Node.js"
description: "Referência dos módulos do Azure Monitor para Node.js"
keywords: Azure, SDK, API, Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="4597f-104">Módulos do Azure Monitor para Node.js</span><span class="sxs-lookup"><span data-stu-id="4597f-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4597f-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4597f-105">Overview</span></span>
<span data-ttu-id="4597f-106">Os aplicativos em nuvem são complexos com muitas partes móveis.</span><span class="sxs-lookup"><span data-stu-id="4597f-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="4597f-107">O monitoramento fornece dados para garantir que seu aplicativo permaneça ativo e em execução em um estado íntegro.</span><span class="sxs-lookup"><span data-stu-id="4597f-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="4597f-108">Ele também ajuda a afastar os problemas potenciais ou solucionar problemas antigos.</span><span class="sxs-lookup"><span data-stu-id="4597f-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="4597f-109">Além disso, você pode usar os dados de monitoramento para obter mais informações sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4597f-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="4597f-110">Esse conhecimento pode ajudá-lo a melhorar o desempenho ou a capacidade de manutenção do aplicativo ou automatizar ações que normalmente exigiriam intervenção manual.</span><span class="sxs-lookup"><span data-stu-id="4597f-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="4597f-111">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4597f-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="4597f-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="4597f-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="4597f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4597f-113">Example</span></span>

<span data-ttu-id="4597f-114">Este exemplo de código imprime todas as regras de alertas associadas a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="4597f-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="4597f-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4597f-115">Samples</span></span>

<span data-ttu-id="4597f-116">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4597f-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
