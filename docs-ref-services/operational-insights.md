---
title: "Módulos do Azure Operational Insights para Node.js"
description: "Referência dos módulos de Insights Operacionais do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 7baa7f2f976cec9d9592231f193eede87a122532
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="26b1d-103">Módulos do Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="26b1d-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="26b1d-104">Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="26b1d-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="26b1d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26b1d-105">Example</span></span> 

<span data-ttu-id="26b1d-106">Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de espaços de trabalho por um grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="26b1d-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="26b1d-107">Exemplos</span><span class="sxs-lookup"><span data-stu-id="26b1d-107">Samples</span></span>

<span data-ttu-id="26b1d-108">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="26b1d-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
