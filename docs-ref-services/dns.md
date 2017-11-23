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
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="7fa75-104">Módulos de DNS do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="7fa75-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7fa75-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7fa75-105">Overview</span></span>

<span data-ttu-id="7fa75-106">Use o DNS do Azure para hospedar seus domínios de DNS (Sistema de Nomes de Domínio) no Azure.</span><span class="sxs-lookup"><span data-stu-id="7fa75-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="7fa75-107">Gerencie registros DNS usando as mesmas credenciais, cobrança e contratos de suporte que os outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="7fa75-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="7fa75-108">Integre perfeitamente serviços baseados no Azure com atualizações de DNS correspondentes e agilize o seu processo completo de implantação.</span><span class="sxs-lookup"><span data-stu-id="7fa75-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="7fa75-109">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="7fa75-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7fa75-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="7fa75-110">Install the npm module</span></span>

<span data-ttu-id="7fa75-111">Instalar o módulo npm do DNS do Azure</span><span class="sxs-lookup"><span data-stu-id="7fa75-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="7fa75-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fa75-112">Example</span></span>

<span data-ttu-id="7fa75-113">Este exemplo lista as zonas de Gerenciamento de DNS.</span><span class="sxs-lookup"><span data-stu-id="7fa75-113">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7fa75-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fa75-114">Samples</span></span>

<span data-ttu-id="7fa75-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7fa75-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
