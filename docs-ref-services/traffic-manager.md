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
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Módulos de Gerenciador de Tráfego do Azure para Node.js

## <a name="overview"></a>Visão geral

O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters. Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem. Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.

Saiba mais sobre o [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do gerenciador de tráfego do Azure

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os Gerenciadores de Tráfego de um determinado grupo de recursos.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
