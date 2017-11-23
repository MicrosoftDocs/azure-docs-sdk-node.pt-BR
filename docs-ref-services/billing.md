---
title: "Módulos de Cobrança do Azure para Node.js"
description: "Referência dos módulos da Cobrança do Azure para Node.js"
keywords: "Azure,SDK,API,Cobrança, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="7fdca-104">Módulos de Cobrança do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="7fdca-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7fdca-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7fdca-105">Overview</span></span>
<span data-ttu-id="7fdca-106">As APIs de Cobrança do Azure fornecem acesso a informações e faturas da cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="7fdca-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="7fdca-107">Para usar essa API, o administrador da conta deve aceitar por meio do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="7fdca-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="7fdca-108">Veja [Gerenciar o acesso a cobrança do Azure usando funções](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="7fdca-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7fdca-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="7fdca-109">Install the npm module</span></span> 

<span data-ttu-id="7fdca-110">Instalar o módulo npm da Cobrança do Azure</span><span class="sxs-lookup"><span data-stu-id="7fdca-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="7fdca-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fdca-111">Example</span></span> 
 
<span data-ttu-id="7fdca-112">Este exemplo imprime uma lista de todas as suas faturas anteriores.</span><span class="sxs-lookup"><span data-stu-id="7fdca-112">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="7fdca-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fdca-113">Samples</span></span>

<span data-ttu-id="7fdca-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7fdca-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>