---
title: "Módulos de Gerenciador de Tráfego do Azure para Node.js"
description: "Módulos do Azure Traffic Manager para referência do Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: cf0834a0eadc67868efb165d60d39c681d4435eb
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="319dd-103">Módulos de Gerenciador de Tráfego do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="319dd-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="319dd-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="319dd-104">Overview</span></span>

<span data-ttu-id="319dd-105">O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters.</span><span class="sxs-lookup"><span data-stu-id="319dd-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="319dd-106">Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="319dd-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="319dd-107">Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.</span><span class="sxs-lookup"><span data-stu-id="319dd-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="319dd-108">Saiba mais sobre o [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="319dd-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="319dd-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="319dd-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="319dd-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="319dd-110">Install the npm module</span></span>

<span data-ttu-id="319dd-111">Instalar o módulo npm do gerenciador de tráfego do Azure</span><span class="sxs-lookup"><span data-stu-id="319dd-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="319dd-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="319dd-112">Example</span></span>

<span data-ttu-id="319dd-113">Este exemplo lista todos os Gerenciadores de Tráfego de um determinado grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="319dd-113">This example lists all Traffic Managers for a given resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="319dd-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="319dd-114">Samples</span></span>

<span data-ttu-id="319dd-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="319dd-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
