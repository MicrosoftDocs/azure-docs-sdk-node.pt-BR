---
title: "Módulos do Azure Analysis Services para Node.js"
description: "Referência dos módulos do Azure Analysis Services para Node.js"
keywords: Azure, SDK, API, Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="e5e49-104">Módulos do Azure Analysis Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="e5e49-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e5e49-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e5e49-105">Overview</span></span>
<span data-ttu-id="e5e49-106">Esse pacote fornece um módulo Node.js que torna mais fácil gerenciar o Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="e5e49-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="e5e49-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e5e49-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e5e49-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="e5e49-108">Install the npm module</span></span>

<span data-ttu-id="e5e49-109">Instalar o módulo npm do Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="e5e49-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="e5e49-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5e49-110">Example</span></span>

<span data-ttu-id="e5e49-111">Este exemplo lista todos os servidores do Analysis Service disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e5e49-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="e5e49-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e5e49-112">Samples</span></span>

<span data-ttu-id="e5e49-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e5e49-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
