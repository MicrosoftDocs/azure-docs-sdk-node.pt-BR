---
title: "Módulos de Azure Service Fabric para Node.js"
description: "Referência dos módulos do Azure Service Fabric para Node.js"
keywords: Azure, SDK, API, Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="f1d34-104">Módulos de Azure Service Fabric para Node.js</span><span class="sxs-lookup"><span data-stu-id="f1d34-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f1d34-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f1d34-105">Overview</span></span>

<span data-ttu-id="f1d34-106">O Azure Service Fabric é uma plataforma de sistemas distribuídos que facilita o empacotamento, implantação e gerenciamento de microsserviços e contêineres escalonáveis e confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f1d34-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="f1d34-107">Saiba mais sobre o [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="f1d34-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="f1d34-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f1d34-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f1d34-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="f1d34-109">Install the npm module</span></span>

<span data-ttu-id="f1d34-110">Instalar o módulo npm do Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f1d34-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="f1d34-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1d34-111">Example</span></span>

<span data-ttu-id="f1d34-112">Este exemplo mostra como você pode listar os clusters para uma assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="f1d34-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="f1d34-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f1d34-113">Samples</span></span>

<span data-ttu-id="f1d34-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f1d34-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
