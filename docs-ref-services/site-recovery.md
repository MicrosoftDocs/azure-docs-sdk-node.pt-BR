---
title: "Módulos de Azure Site Recovery para Node.js"
description: "Referência dos módulos do Azure Site Recovery para Node.js"
keywords: Azure, SDK, API, Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="b26de-104">Módulos de Azure Site Recovery para Node.js</span><span class="sxs-lookup"><span data-stu-id="b26de-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b26de-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b26de-105">Overview</span></span>

<span data-ttu-id="b26de-106">O Site Recovery permite que você automatize a replicação de máquinas virtuais do Azure entre regiões, máquinas virtuais locais e servidores físicos para o Azure e computadores locais em um datacenter secundário.</span><span class="sxs-lookup"><span data-stu-id="b26de-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="b26de-107">Saiba mais sobre o [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="b26de-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b26de-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b26de-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b26de-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="b26de-109">Install the npm module</span></span>

<span data-ttu-id="b26de-110">Instalar o módulo npm de serviço do Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="b26de-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="b26de-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b26de-111">Example</span></span>

<span data-ttu-id="b26de-112">Este exemplo lista o serviço do Site Recovery para um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="b26de-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="b26de-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b26de-113">Samples</span></span>

<span data-ttu-id="b26de-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b26de-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
