---
title: Módulos do Azure Analysis Services para Node.js
description: Referência dos módulos do Azure Analysis Services para Node.js
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 166d0450ac9b2d005f3ce4ecba5ce36e1786ae09
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="9d5b6-103">Módulos do Azure Analysis Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="9d5b6-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9d5b6-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9d5b6-104">Overview</span></span>
<span data-ttu-id="9d5b6-105">Esse pacote fornece um módulo Node.js que torna mais fácil gerenciar o Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="9d5b6-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="9d5b6-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9d5b6-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9d5b6-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="9d5b6-107">Install the npm module</span></span>

<span data-ttu-id="9d5b6-108">Instalar o módulo npm do Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="9d5b6-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="9d5b6-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d5b6-109">Example</span></span>

<span data-ttu-id="9d5b6-110">Este exemplo lista todos os servidores do Analysis Service disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d5b6-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9d5b6-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9d5b6-111">Samples</span></span>

<span data-ttu-id="9d5b6-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9d5b6-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
