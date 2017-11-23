---
title: "Módulos de Serviços de Mídia do Azure para Node.js"
description: "Referência dos módulos de Serviços de Mídia do Azure para Node.js"
keywords: "Azure, SDK, API, Serviços de Mídia, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="e1216-104">Módulos de Serviços de Mídia do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="e1216-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e1216-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e1216-105">Overview</span></span>

<span data-ttu-id="e1216-106">Os Serviços de Mídia do Azure são uma plataforma extensível baseada em nuvem que permite aos desenvolvedores compilar aplicativos de gerenciamento e entrega de mídia escalonável.</span><span class="sxs-lookup"><span data-stu-id="e1216-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="e1216-107">Os serviços de mídia se baseiam em APIs REST que permitem que você carregue com segurança, armazene, codifique e empacote o conteúdo de áudio ou vídeo para entrega de streaming sob demanda e ao vivo para vários clientes (por exemplo, TV, PCs e dispositivos móveis).</span><span class="sxs-lookup"><span data-stu-id="e1216-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="e1216-108">Com os Serviços de Mídia do Azure, você pode:</span><span class="sxs-lookup"><span data-stu-id="e1216-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="e1216-109">Compilar fluxos de trabalho de ponta a ponta usando completamente os Serviços de Mídia.</span><span class="sxs-lookup"><span data-stu-id="e1216-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="e1216-110">Use componentes de terceiros para algumas partes do seu fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e1216-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="e1216-111">Por exemplo, codifique usando um codificador de terceiros.</span><span class="sxs-lookup"><span data-stu-id="e1216-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="e1216-112">Em seguida, carregue, proteja, empacote e entregue usando os serviços de mídia.</span><span class="sxs-lookup"><span data-stu-id="e1216-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="e1216-113">Transmita seu conteúdo ao vivo ou forneça conteúdo sob demanda.</span><span class="sxs-lookup"><span data-stu-id="e1216-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="e1216-114">O tópico também está vinculado a outros tópicos relevantes.</span><span class="sxs-lookup"><span data-stu-id="e1216-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="e1216-115">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e1216-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e1216-116">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="e1216-116">Install the npm module</span></span>

<span data-ttu-id="e1216-117">Instalar o módulo npm de serviços de mídia do Azure</span><span class="sxs-lookup"><span data-stu-id="e1216-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="e1216-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1216-118">Example</span></span>

<span data-ttu-id="e1216-119">Este exemplo lista todos os serviços de mídia para um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="e1216-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="e1216-120">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e1216-120">Samples</span></span>

<span data-ttu-id="e1216-121">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e1216-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
