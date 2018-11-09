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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51185525"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="b513b-103">Módulos do Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="b513b-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="b513b-104">Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="b513b-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="b513b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b513b-105">Example</span></span> 

<span data-ttu-id="b513b-106">Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de workspaces por um grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="b513b-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b513b-107">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b513b-107">Samples</span></span>

<span data-ttu-id="b513b-108">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b513b-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
