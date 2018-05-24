---
title: Módulos de Azure Site Recovery para Node.js
description: Referência dos módulos do Azure Site Recovery para Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="3109d-103">Módulos de Azure Site Recovery para Node.js</span><span class="sxs-lookup"><span data-stu-id="3109d-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="3109d-104">O Site Recovery permite que você automatize a replicação de máquinas virtuais do Azure entre regiões, máquinas virtuais locais e servidores físicos para o Azure e computadores locais em um datacenter secundário.</span><span class="sxs-lookup"><span data-stu-id="3109d-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="3109d-105">Saiba mais sobre o [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="3109d-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="3109d-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3109d-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3109d-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="3109d-107">Install the npm module</span></span>

<span data-ttu-id="3109d-108">Instalar o módulo npm de serviço do Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="3109d-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="3109d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3109d-109">Example</span></span>

<span data-ttu-id="3109d-110">Este exemplo lista o serviço do Site Recovery para um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="3109d-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="3109d-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3109d-111">Samples</span></span>

<span data-ttu-id="3109d-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3109d-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
