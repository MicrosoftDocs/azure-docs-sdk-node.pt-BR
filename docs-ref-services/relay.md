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
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="14fa1-104">Módulos de Retransmissão do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="14fa1-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="14fa1-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="14fa1-105">Overview</span></span>

<span data-ttu-id="14fa1-106">O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="14fa1-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="14fa1-107">A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.</span><span class="sxs-lookup"><span data-stu-id="14fa1-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="14fa1-108">Saiba mais sobre [Retransmissão do Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="14fa1-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="14fa1-109">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="14fa1-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="14fa1-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="14fa1-110">Install the npm module</span></span>

<span data-ttu-id="14fa1-111">Instalar o módulo npm de Retransmissão do Azure</span><span class="sxs-lookup"><span data-stu-id="14fa1-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="14fa1-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14fa1-112">Example</span></span>

<span data-ttu-id="14fa1-113">Este exemplo lista os namespaces para um cliente da Retransmissão.</span><span class="sxs-lookup"><span data-stu-id="14fa1-113">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="14fa1-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="14fa1-114">Samples</span></span>

<span data-ttu-id="14fa1-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="14fa1-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
