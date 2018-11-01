---
title: Módulos de Comércio do Azure para Node.js
description: Referência dos módulos do Comércio do Azure para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50378524"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="06c83-103">Módulos de Comércio do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="06c83-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="06c83-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="06c83-104">Overview</span></span>

<span data-ttu-id="06c83-105">Use APIs de Comércio do Azure para efetuar pull de dados de uso e de recurso em suas ferramentas de análise de dados preferidas.</span><span class="sxs-lookup"><span data-stu-id="06c83-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="06c83-106">As APIs RateCard e de Uso de Recursos do Azure e podem ajudá-lo a prever e gerenciar seus custos com precisão.</span><span class="sxs-lookup"><span data-stu-id="06c83-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="06c83-107">As APIs são implementadas como um Provedor de Recursos e como parte da família de APIs expostas pelo Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="06c83-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="06c83-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="06c83-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="06c83-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="06c83-109">Install the npm module</span></span>

<span data-ttu-id="06c83-110">Instalar o módulo npm de Comércio do Azure</span><span class="sxs-lookup"><span data-stu-id="06c83-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="06c83-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06c83-111">Example</span></span>

<span data-ttu-id="06c83-112">Este exemplo recupera os dados de consumo do Azure previstos para o último mês.</span><span class="sxs-lookup"><span data-stu-id="06c83-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="06c83-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="06c83-113">Samples</span></span>

<span data-ttu-id="06c83-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="06c83-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
