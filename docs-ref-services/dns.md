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
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52106322"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="1a052-103">Módulos de DNS do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="1a052-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="1a052-104">Use o DNS do Azure para hospedar seus domínios de DNS (Sistema de Nomes de Domínio) no Azure.</span><span class="sxs-lookup"><span data-stu-id="1a052-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="1a052-105">Gerencie registros DNS usando as mesmas credenciais, cobrança e contratos de suporte que os outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="1a052-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="1a052-106">Integre perfeitamente serviços baseados no Azure com atualizações de DNS correspondentes e agilize o seu processo completo de implantação.</span><span class="sxs-lookup"><span data-stu-id="1a052-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="1a052-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1a052-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1a052-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="1a052-108">Install the npm module</span></span>

<span data-ttu-id="1a052-109">Instalar o módulo npm do DNS do Azure</span><span class="sxs-lookup"><span data-stu-id="1a052-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="1a052-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a052-110">Example</span></span>

<span data-ttu-id="1a052-111">Este exemplo lista as zonas de Gerenciamento de DNS.</span><span class="sxs-lookup"><span data-stu-id="1a052-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1a052-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1a052-112">Samples</span></span>

<span data-ttu-id="1a052-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1a052-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
