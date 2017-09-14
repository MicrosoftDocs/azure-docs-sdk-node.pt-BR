---
title: "Módulos do CDN do Azure para Node.js"
description: "Referência dos módulos de CDN do Azure para Node.js"
keywords: Azure, SDK, API, CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="91c94-104">Módulos do CDN do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="91c94-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="91c94-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="91c94-105">Overview</span></span>

<span data-ttu-id="91c94-106">A CDN (Rede de Distribuição de Conteúdo) do Azure oferece aos desenvolvedores uma solução global de fornecimento de conteúdo de alta largura de banda hospedada no Azure ou em qualquer outro local.</span><span class="sxs-lookup"><span data-stu-id="91c94-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="91c94-107">Com a CDN, você pode armazenar em cache objetos publicamente disponíveis carregados do Armazenamento de Blobs do Azure, de um aplicativo Web, da máquina virtual, de uma pasta de aplicativo ou de outro local HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="91c94-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="91c94-108">O cache da CDN pode ser mantido em locais estratégicos para fornecer a máxima largura de banda para fornecimento de conteúdo aos usuários.</span><span class="sxs-lookup"><span data-stu-id="91c94-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="91c94-109">A CDN normalmente é usada para fornecimento de conteúdo estático, como imagens, folhas de estilo, documentos, arquivos, scripts do lado do cliente e páginas HTML.</span><span class="sxs-lookup"><span data-stu-id="91c94-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="91c94-110">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="91c94-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="91c94-111">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="91c94-111">Install the npm module</span></span>

<span data-ttu-id="91c94-112">Instalar o módulo npm CDN do Azure</span><span class="sxs-lookup"><span data-stu-id="91c94-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="91c94-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91c94-113">Example</span></span>

<span data-ttu-id="91c94-114">Este exemplo lista todos os perfis CDN.</span><span class="sxs-lookup"><span data-stu-id="91c94-114">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="91c94-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91c94-115">Samples</span></span>

<span data-ttu-id="91c94-116">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="91c94-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
