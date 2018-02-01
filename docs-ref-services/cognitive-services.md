---
title: "Módulos de Serviços Cognitivos do Azure para Node.js"
description: "Referência dos módulos de Serviços cognitivos do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="d5f42-103">Módulos de Serviços Cognitivos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d5f42-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="d5f42-104">Serviços Cognitivos do Azure é um conjunto de APIs, SDKs e serviços disponíveis para desenvolvedores para tornar seus aplicativos mais inteligentes, atraentes e descobríveis.</span><span class="sxs-lookup"><span data-stu-id="d5f42-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="d5f42-105">Os Serviços Cognitivos da Microsoft ampliam o portfólio em evolução da Microsoft de APIs de machine learning e permitem aos desenvolvedores adicionar facilmente recursos inteligentes – como emoção e detecção de vídeo; reconhecimento facial, de fala e de visão, além de compreensão de fala e de idioma – a seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d5f42-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="d5f42-106">Nossa visão se destina a experiências de computação mais pessoais e produtividade aprimorada auxiliadas por sistemas que cada vez mais possam ver, ouvir, falar, compreender e até mesmo começar a raciocinar.</span><span class="sxs-lookup"><span data-stu-id="d5f42-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="d5f42-107">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d5f42-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d5f42-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d5f42-108">Install the npm module</span></span>

<span data-ttu-id="d5f42-109">Instalar o módulo npm de Serviços Cognitivos do Azure</span><span class="sxs-lookup"><span data-stu-id="d5f42-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="d5f42-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5f42-110">Example</span></span>

<span data-ttu-id="d5f42-111">Este exemplo lista todas as contas de serviço cognitivo.</span><span class="sxs-lookup"><span data-stu-id="d5f42-111">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="d5f42-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d5f42-112">Samples</span></span>

<span data-ttu-id="d5f42-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d5f42-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
