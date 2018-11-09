---
title: Módulos do CDN do Azure para Node.js
description: Referência dos módulos de CDN do Azure para Node.js
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51178875"
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="9fd8d-103">Módulos do CDN do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="9fd8d-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9fd8d-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9fd8d-104">Overview</span></span>

<span data-ttu-id="9fd8d-105">A CDN (Rede de Distribuição de Conteúdo) do Azure oferece aos desenvolvedores uma solução global de fornecimento de conteúdo de alta largura de banda hospedada no Azure ou em qualquer outro local.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="9fd8d-106">Com a CDN, você pode armazenar em cache objetos publicamente disponíveis carregados do Armazenamento de Blobs do Azure, de um aplicativo Web, da máquina virtual, de uma pasta de aplicativo ou de outro local HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="9fd8d-107">O cache da CDN pode ser mantido em locais estratégicos para fornecer a máxima largura de banda para fornecimento de conteúdo aos usuários.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="9fd8d-108">A CDN normalmente é usada para fornecimento de conteúdo estático, como imagens, folhas de estilo, documentos, arquivos, scripts do lado do cliente e páginas HTML.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="9fd8d-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9fd8d-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9fd8d-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="9fd8d-110">Install the npm module</span></span>

<span data-ttu-id="9fd8d-111">Instalar o módulo npm CDN do Azure</span><span class="sxs-lookup"><span data-stu-id="9fd8d-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="9fd8d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fd8d-112">Example</span></span>

<span data-ttu-id="9fd8d-113">Este exemplo lista todos os perfis CDN.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-113">This example lists all of the CDN profiles.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9fd8d-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9fd8d-114">Samples</span></span>

<span data-ttu-id="9fd8d-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9fd8d-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
