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
# <a name="azure-operational-insights-modules-for-nodejs"></a>Módulos do Azure Operational Insights para Node.js

Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>Exemplo 

Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de workspaces por um grupo de recursos especificado.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
