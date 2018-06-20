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
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262213"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="95a48-103">Módulos de DNS do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="95a48-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="95a48-104">Use o DNS do Azure para hospedar seus domínios de DNS (Sistema de Nomes de Domínio) no Azure.</span><span class="sxs-lookup"><span data-stu-id="95a48-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="95a48-105">Gerencie registros DNS usando as mesmas credenciais, cobrança e contratos de suporte que os outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="95a48-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="95a48-106">Integre perfeitamente serviços baseados no Azure com atualizações de DNS correspondentes e agilize o seu processo completo de implantação.</span><span class="sxs-lookup"><span data-stu-id="95a48-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="95a48-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="95a48-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="95a48-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="95a48-108">Install the npm module</span></span>

<span data-ttu-id="95a48-109">Instalar o módulo npm do DNS do Azure</span><span class="sxs-lookup"><span data-stu-id="95a48-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="95a48-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95a48-110">Example</span></span>

<span data-ttu-id="95a48-111">Este exemplo lista as zonas de Gerenciamento de DNS.</span><span class="sxs-lookup"><span data-stu-id="95a48-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="95a48-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="95a48-112">Samples</span></span>

<span data-ttu-id="95a48-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="95a48-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
