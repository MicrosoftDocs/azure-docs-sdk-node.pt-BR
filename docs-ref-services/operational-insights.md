---
title: Módulos do Azure Operational Insights para Node.js
description: Referência dos módulos de Insights Operacionais do Azure para Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49801226"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="43a29-103">Módulos do Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="43a29-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="43a29-104">Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="43a29-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="43a29-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43a29-105">Example</span></span> 

<span data-ttu-id="43a29-106">Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de workspaces por um grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="43a29-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="43a29-107">Exemplos</span><span class="sxs-lookup"><span data-stu-id="43a29-107">Samples</span></span>

<span data-ttu-id="43a29-108">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="43a29-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
