---
title: "Módulos de Retransmissão do Azure para Node.js"
description: "Referência dos módulos da Retransmissão do Azure para Node.js"
keywords: "Azure, SDK, API, Retransmissão, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a>Módulos de Retransmissão do Azure para Node.js

## <a name="overview"></a>Visão geral

O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa. A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.

Saiba mais sobre [Retransmissão do Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de Retransmissão do Azure

```bash
npm install azure-arm-relay
```

### <a name="example"></a>Exemplo

Este exemplo lista os namespaces para um cliente da Retransmissão.

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
