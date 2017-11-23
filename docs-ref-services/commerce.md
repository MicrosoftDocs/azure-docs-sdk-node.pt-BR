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
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="2bd17-104">Módulos de Comércio do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="2bd17-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2bd17-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2bd17-105">Overview</span></span>

<span data-ttu-id="2bd17-106">Use APIs de Comércio do Azure para efetuar pull de dados de uso e de recurso em suas ferramentas de análise de dados preferidas.</span><span class="sxs-lookup"><span data-stu-id="2bd17-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="2bd17-107">As APIs RateCard e de Uso de Recursos do Azure e podem ajudá-lo a prever e gerenciar seus custos com precisão.</span><span class="sxs-lookup"><span data-stu-id="2bd17-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="2bd17-108">As APIs são implementadas como um Provedor de Recursos e como parte da família de APIs expostas pelo Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="2bd17-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="2bd17-109">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="2bd17-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2bd17-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="2bd17-110">Install the npm module</span></span>

<span data-ttu-id="2bd17-111">Instalar o módulo npm de Comércio do Azure</span><span class="sxs-lookup"><span data-stu-id="2bd17-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="2bd17-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bd17-112">Example</span></span>

<span data-ttu-id="2bd17-113">Este exemplo recupera os dados de consumo do Azure previstos para o último mês.</span><span class="sxs-lookup"><span data-stu-id="2bd17-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2bd17-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2bd17-114">Samples</span></span>

<span data-ttu-id="2bd17-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2bd17-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
