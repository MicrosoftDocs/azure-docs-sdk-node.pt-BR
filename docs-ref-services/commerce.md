---
title: "Módulos de Comércio do Azure para Node.js"
description: "Referência dos módulos do Comércio do Azure para Node.js"
keywords: "Azure, SDK, API, Comércio, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a>Módulos de Comércio do Azure para Node.js

## <a name="overview"></a>Visão geral

Use APIs de Comércio do Azure para efetuar pull de dados de uso e de recurso em suas ferramentas de análise de dados preferidas. As APIs RateCard e de Uso de Recursos do Azure e podem ajudá-lo a prever e gerenciar seus custos com precisão. As APIs são implementadas como um Provedor de Recursos e como parte da família de APIs expostas pelo Azure Resource Manager.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de Comércio do Azure

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Exemplo

Este exemplo recupera os dados de consumo do Azure previstos para o último mês.

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
