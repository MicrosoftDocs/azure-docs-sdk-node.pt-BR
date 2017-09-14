---
title: "Módulos de DNS do Azure para Node.js"
description: "Referência dos módulos de DNS do Azure para Node.js"
keywords: Azure, SDK, API, DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>Módulos de DNS do Azure para Node.js

## <a name="overview"></a>Visão geral

Use o DNS do Azure para hospedar seus domínios de DNS (Sistema de Nomes de Domínio) no Azure. Gerencie registros DNS usando as mesmas credenciais, cobrança e contratos de suporte que os outros serviços do Azure. Integre perfeitamente serviços baseados no Azure com atualizações de DNS correspondentes e agilize o seu processo completo de implantação.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do DNS do Azure

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Exemplo

Este exemplo lista as zonas de Gerenciamento de DNS.

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
