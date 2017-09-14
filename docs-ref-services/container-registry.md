---
title: "Módulos do Registro de Contêiner do Azure para Node.js"
description: "Referência dos módulos de Registro de Contêiner do Azure para Node.js"
keywords: "Azure, SDK, API, Registro de Contêiner, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Módulos do Registro de Contêiner do Azure para Node.js

## <a name="overview"></a>Visão geral

O Registro de Contêiner do Azure é um serviço gerenciado do registro do Docker com base no Docker Registry 2.0 de software livre. Criar e manter registros de contêiner do Azure para armazenar e gerenciar suas imagens privadas de contêiner Docker. Use registros de contêiner no Azure com o desenvolvimento de contêiner e os pipelines de implantação existentes e tire proveito da experiência da comunidade do Docker.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de registro de contêiner do Azure

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Exemplo

Este exemplo obtém uma lista de contêineres disponíveis.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
