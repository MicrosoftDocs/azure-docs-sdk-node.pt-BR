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
# <a name="azure-site-recovery-modules-for-nodejs"></a>Módulos de Azure Site Recovery para Node.js

## <a name="overview"></a>Visão geral

O Site Recovery permite que você automatize a replicação de máquinas virtuais do Azure entre regiões, máquinas virtuais locais e servidores físicos para o Azure e computadores locais em um datacenter secundário.

Saiba mais sobre o [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de serviço do Azure Site Recovery

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>Exemplo

Este exemplo lista o serviço do Site Recovery para um grupo de recursos.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
