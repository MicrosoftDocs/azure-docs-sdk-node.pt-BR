---
title: "Módulos de Gerenciador de Tráfego do Azure para Node.js"
description: "Referência dos módulos do Azure Traffic Manager para Node.js"
keywords: "Azure, SDK, API, Gerenciador de Tráfego, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="b76da-104">Módulos de Gerenciador de Tráfego do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="b76da-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b76da-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b76da-105">Overview</span></span>

<span data-ttu-id="b76da-106">O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters.</span><span class="sxs-lookup"><span data-stu-id="b76da-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="b76da-107">Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="b76da-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="b76da-108">Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.</span><span class="sxs-lookup"><span data-stu-id="b76da-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="b76da-109">Saiba mais sobre o [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="b76da-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b76da-110">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b76da-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b76da-111">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="b76da-111">Install the npm module</span></span>

<span data-ttu-id="b76da-112">Instalar o módulo npm do gerenciador de tráfego do Azure</span><span class="sxs-lookup"><span data-stu-id="b76da-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="b76da-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b76da-113">Example</span></span>

<span data-ttu-id="b76da-114">Este exemplo lista todos os Gerenciadores de Tráfego de um determinado grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="b76da-114">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="b76da-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b76da-115">Samples</span></span>

<span data-ttu-id="b76da-116">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b76da-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
