---
title: Módulos de Azure Service Fabric para Node.js
description: Módulos do Azure Service Fabric para referência do Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52110057"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="add8c-103">Módulos de Azure Service Fabric para Node.js</span><span class="sxs-lookup"><span data-stu-id="add8c-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="add8c-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="add8c-104">Overview</span></span>

<span data-ttu-id="add8c-105">O Azure Service Fabric é uma plataforma de sistemas distribuídos que facilita o empacotamento, implantação e gerenciamento de microsserviços e contêineres escalonáveis e confiáveis.</span><span class="sxs-lookup"><span data-stu-id="add8c-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="add8c-106">Saiba mais sobre o [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="add8c-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="add8c-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="add8c-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="add8c-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="add8c-108">Install the npm module</span></span>

<span data-ttu-id="add8c-109">Instalar o módulo npm do Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="add8c-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="add8c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="add8c-110">Example</span></span>

<span data-ttu-id="add8c-111">Este exemplo mostra como você pode listar os clusters para uma assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="add8c-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="add8c-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="add8c-112">Samples</span></span>

<span data-ttu-id="add8c-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="add8c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
