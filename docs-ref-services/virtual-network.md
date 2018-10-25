---
title: Módulos de Rede Virtual do Azure para Node.js
description: Referência dos módulos de Rede Virtual do Azure para Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49670851"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Módulos de Rede Virtual do Azure para Node.js

## <a name="overview"></a>Visão geral

O serviço de Rede Virtual do Azure permite que você conecte com segurança os recursos do Azure usando redes virtuais (VNets). Uma VNet é uma representação da sua própria rede na nuvem. Uma VNet é um isolamento lógico da nuvem do Azure dedicada à sua assinatura. Você também pode conectar VNets à sua rede local.

Saiba mais sobre a [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm da Rede Virtual do Azure

```bash
npm install azure-arm-network
```

### <a name="example"></a>Exemplo

Este exemplo obtém e imprime a lista de redes virtuais

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
