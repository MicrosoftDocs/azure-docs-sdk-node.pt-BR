---
title: Módulos de DNS do Azure para Node.js
description: Referência dos módulos de DNS do Azure para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062035"
---
# <a name="azure-dns-modules-for-nodejs"></a>Módulos de DNS do Azure para Node.js

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
