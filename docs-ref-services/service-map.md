---
title: "Módulos de Mapa do Serviço do Azure para Node.js"
description: "Referência dos módulos de Mapa do Serviço do Azure para Node.js"
keywords: "Azure, SDK, API, Mapa do Serviço, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="38060-104">Módulos de Mapa do Serviço do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="38060-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="38060-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="38060-105">Overview</span></span>

<span data-ttu-id="38060-106">O Mapa do Serviço detecta automaticamente os componentes de aplicativos em sistemas Windows e Linux e mapeia a comunicação entre os serviços.</span><span class="sxs-lookup"><span data-stu-id="38060-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="38060-107">O Mapa do Serviço mostra conexões entre servidores, processos e portas em qualquer arquitetura conectada a TCP sem nenhuma configuração necessária além da instalação de um agente.</span><span class="sxs-lookup"><span data-stu-id="38060-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="38060-108">Saiba mais sobre o [Mapa do Serviço do Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="38060-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="38060-109">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="38060-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="38060-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="38060-110">Install the npm module</span></span>

<span data-ttu-id="38060-111">Instalar o módulo npm do Mapa do Serviço do Azure</span><span class="sxs-lookup"><span data-stu-id="38060-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="38060-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38060-112">Example</span></span>

<span data-ttu-id="38060-113">Este exemplo lista todos os mapas de serviço para o grupo de recursos e o espaço de trabalho especificados.</span><span class="sxs-lookup"><span data-stu-id="38060-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="38060-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="38060-114">Samples</span></span>

<span data-ttu-id="38060-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="38060-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
