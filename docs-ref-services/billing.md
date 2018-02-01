---
title: "Módulos de Cobrança do Azure para Node.js"
description: "Referência dos módulos da Cobrança do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a>Módulos de Cobrança do Azure para Node.js

## <a name="overview"></a>Visão geral
As APIs de Cobrança do Azure fornecem acesso a informações e faturas da cobrança do Azure.

Para usar essa API, o administrador da conta deve aceitar por meio do portal do Azure. Veja [Gerenciar o acesso a cobrança do Azure usando funções](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Instalar o módulo npm 

Instalar o módulo npm da Cobrança do Azure 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Exemplo 
 
Este exemplo imprime uma lista de todas as suas faturas anteriores.
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
