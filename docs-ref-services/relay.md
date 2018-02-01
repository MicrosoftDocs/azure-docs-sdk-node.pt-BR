---
title: "Módulos de Retransmissão do Azure para Node.js"
description: "Referência dos módulos da Retransmissão do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 632e17f9169353ad9348b3b098b4a3e8d873238a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="a6e1a-103">Módulos de Retransmissão do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="a6e1a-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="a6e1a-104">O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="a6e1a-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="a6e1a-105">A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.</span><span class="sxs-lookup"><span data-stu-id="a6e1a-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="a6e1a-106">Saiba mais sobre [Retransmissão do Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="a6e1a-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="a6e1a-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="a6e1a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a6e1a-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="a6e1a-108">Install the npm module</span></span>

<span data-ttu-id="a6e1a-109">Instalar o módulo npm de Retransmissão do Azure</span><span class="sxs-lookup"><span data-stu-id="a6e1a-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="a6e1a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6e1a-110">Example</span></span>

<span data-ttu-id="a6e1a-111">Este exemplo lista os namespaces para um cliente da Retransmissão.</span><span class="sxs-lookup"><span data-stu-id="a6e1a-111">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a6e1a-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a6e1a-112">Samples</span></span>

<span data-ttu-id="a6e1a-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a6e1a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
