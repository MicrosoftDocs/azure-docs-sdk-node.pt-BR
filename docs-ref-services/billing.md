---
title: Módulos de Cobrança do Azure para Node.js
description: Referência dos módulos da Cobrança do Azure para Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48571584"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="e9886-103">Módulos de Cobrança do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="e9886-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e9886-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e9886-104">Overview</span></span>
<span data-ttu-id="e9886-105">As APIs de Cobrança do Azure fornecem acesso a informações e faturas da cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="e9886-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="e9886-106">Para usar essa API, o administrador da conta deve aceitar por meio do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="e9886-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="e9886-107">Veja [Gerenciar o acesso a cobrança do Azure usando funções](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="e9886-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e9886-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="e9886-108">Install the npm module</span></span> 

<span data-ttu-id="e9886-109">Instalar o módulo npm da Cobrança do Azure</span><span class="sxs-lookup"><span data-stu-id="e9886-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="e9886-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9886-110">Example</span></span> 
 
<span data-ttu-id="e9886-111">Este exemplo imprime uma lista de todas as suas faturas anteriores.</span><span class="sxs-lookup"><span data-stu-id="e9886-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="e9886-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e9886-112">Samples</span></span>

<span data-ttu-id="e9886-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e9886-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
