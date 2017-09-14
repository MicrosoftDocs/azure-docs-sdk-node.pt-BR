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
# <a name="azure-operational-insights-modules-for-nodejs"></a>Módulos do Azure Operational Insights para Node.js

## <a name="overview"></a>Visão geral

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar o módulo de Insights Operacionais do Azure para Node.js

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>Exemplo 

Este exemplo cria um cliente, conecta-se ao Insights Operacionais e recupera uma lista de espaços de trabalho por um grupo de recursos especificado.

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
