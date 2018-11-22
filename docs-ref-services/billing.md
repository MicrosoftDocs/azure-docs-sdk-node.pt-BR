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
ms.openlocfilehash: 7be64d01c1bf8d247694735b8581f72678f55983
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094461"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="3990b-103">Módulos de Cobrança do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="3990b-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3990b-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3990b-104">Overview</span></span>
<span data-ttu-id="3990b-105">As APIs de Cobrança do Azure fornecem acesso a informações e faturas da cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="3990b-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="3990b-106">Para usar essa API, o administrador da conta deve aceitar por meio do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="3990b-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="3990b-107">Veja [Gerenciar o acesso a cobrança do Azure usando funções](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="3990b-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3990b-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="3990b-108">Install the npm module</span></span> 

<span data-ttu-id="3990b-109">Instalar o módulo npm da Cobrança do Azure</span><span class="sxs-lookup"><span data-stu-id="3990b-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="3990b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3990b-110">Example</span></span> 
 
<span data-ttu-id="3990b-111">Este exemplo imprime uma lista de todas as suas faturas anteriores.</span><span class="sxs-lookup"><span data-stu-id="3990b-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="3990b-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3990b-112">Samples</span></span>

<span data-ttu-id="3990b-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3990b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
