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
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52040171"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Módulos de Azure Site Recovery para Node.js

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
