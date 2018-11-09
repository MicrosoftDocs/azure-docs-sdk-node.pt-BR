---
title: Módulos do Azure Monitor para Node.js
description: Referência dos módulos do Azure Monitor para Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51141305"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="45925-103">Módulos do Azure Monitor para Node.js</span><span class="sxs-lookup"><span data-stu-id="45925-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="45925-104">Os aplicativos em nuvem são complexos com muitas partes móveis.</span><span class="sxs-lookup"><span data-stu-id="45925-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="45925-105">O monitoramento fornece dados para garantir que seu aplicativo permaneça ativo e em execução em um estado íntegro.</span><span class="sxs-lookup"><span data-stu-id="45925-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="45925-106">Ele também ajuda a afastar os problemas potenciais ou solucionar problemas antigos.</span><span class="sxs-lookup"><span data-stu-id="45925-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="45925-107">Além disso, você pode usar os dados de monitoramento para obter mais informações sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45925-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="45925-108">Esse conhecimento pode ajudá-lo a melhorar o desempenho ou a capacidade de manutenção do aplicativo ou automatizar ações que normalmente exigiriam intervenção manual.</span><span class="sxs-lookup"><span data-stu-id="45925-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="45925-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="45925-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="45925-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="45925-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="45925-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45925-111">Example</span></span>

<span data-ttu-id="45925-112">Este exemplo de código imprime todas as regras de alertas associadas a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="45925-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="45925-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="45925-113">Samples</span></span>

<span data-ttu-id="45925-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="45925-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
