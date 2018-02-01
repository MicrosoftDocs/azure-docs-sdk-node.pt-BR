---
title: "Módulos de Mapa do Serviço do Azure para Node.js"
description: "Referência dos módulos de Mapa do Serviço do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 3f858e52f7a97ff77959825a1be993ef52f96e57
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="9ca6a-103">Módulos de Mapa do Serviço do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="9ca6a-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="9ca6a-104">O Mapa do Serviço detecta automaticamente os componentes de aplicativos em sistemas Windows e Linux e mapeia a comunicação entre os serviços.</span><span class="sxs-lookup"><span data-stu-id="9ca6a-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="9ca6a-105">O Mapa do Serviço mostra conexões entre servidores, processos e portas em qualquer arquitetura conectada a TCP sem nenhuma configuração necessária além da instalação de um agente.</span><span class="sxs-lookup"><span data-stu-id="9ca6a-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="9ca6a-106">Saiba mais sobre o [Mapa do Serviço do Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="9ca6a-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="9ca6a-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9ca6a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9ca6a-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="9ca6a-108">Install the npm module</span></span>

<span data-ttu-id="9ca6a-109">Instalar o módulo npm do Mapa do Serviço do Azure</span><span class="sxs-lookup"><span data-stu-id="9ca6a-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="9ca6a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ca6a-110">Example</span></span>

<span data-ttu-id="9ca6a-111">Este exemplo lista todos os mapas de serviço para o grupo de recursos e o espaço de trabalho especificados.</span><span class="sxs-lookup"><span data-stu-id="9ca6a-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9ca6a-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9ca6a-112">Samples</span></span>

<span data-ttu-id="9ca6a-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9ca6a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
