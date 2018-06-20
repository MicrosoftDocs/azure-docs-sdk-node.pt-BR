---
title: Módulos de Serviços de Mídia do Azure para Node.js
description: Referência dos módulos de Serviços de Mídia do Azure para Node.js
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: e8b2b4b994c25fadda7a37d05a12778d8c9970d8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261988"
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="fc7b4-103">Módulos de Serviços de Mídia do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="fc7b4-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="fc7b4-104">Os Serviços de Mídia do Azure são uma plataforma extensível baseada em nuvem que permite aos desenvolvedores compilar aplicativos de gerenciamento e entrega de mídia escalonável.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="fc7b4-105">Os serviços de mídia se baseiam em APIs REST que permitem que você carregue com segurança, armazene, codifique e empacote o conteúdo de áudio ou vídeo para entrega de streaming sob demanda e ao vivo para vários clientes (por exemplo, TV, PCs e dispositivos móveis).</span><span class="sxs-lookup"><span data-stu-id="fc7b4-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="fc7b4-106">Com os Serviços de Mídia do Azure, você pode:</span><span class="sxs-lookup"><span data-stu-id="fc7b4-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="fc7b4-107">Compilar fluxos de trabalho de ponta a ponta usando completamente os Serviços de Mídia.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="fc7b4-108">Use componentes de terceiros para algumas partes do seu fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="fc7b4-109">Por exemplo, codifique usando um codificador de terceiros.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="fc7b4-110">Em seguida, carregue, proteja, empacote e entregue usando os serviços de mídia.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="fc7b4-111">Transmita seu conteúdo ao vivo ou forneça conteúdo sob demanda.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="fc7b4-112">O tópico também está vinculado a outros tópicos relevantes.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="fc7b4-113">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="fc7b4-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fc7b4-114">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="fc7b4-114">Install the npm module</span></span>

<span data-ttu-id="fc7b4-115">Instalar o módulo npm de serviços de mídia do Azure</span><span class="sxs-lookup"><span data-stu-id="fc7b4-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="fc7b4-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc7b4-116">Example</span></span>

<span data-ttu-id="fc7b4-117">Este exemplo lista todos os serviços de mídia para um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fc7b4-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fc7b4-118">Samples</span></span>

<span data-ttu-id="fc7b4-119">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fc7b4-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
