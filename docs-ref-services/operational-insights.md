---
title: "Módulos do Azure Operational Insights para Node.js"
description: "Referência dos módulos de Insights Operacionais do Azure para Node.js"
keywords: Azure, SDK, API, Insights Operacionais, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="2ad3d-104">Módulos do Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="2ad3d-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2ad3d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2ad3d-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="2ad3d-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="2ad3d-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2ad3d-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="2ad3d-107">Install the npm module</span></span>

<span data-ttu-id="2ad3d-108">Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="2ad3d-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="2ad3d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ad3d-109">Example</span></span> 

<span data-ttu-id="2ad3d-110">Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de espaços de trabalho por um grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="2ad3d-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="2ad3d-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2ad3d-111">Samples</span></span>

<span data-ttu-id="2ad3d-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2ad3d-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>