---
title: "Módulos do Azure Active Directory para Node.js"
description: "Referência dos módulos do Azure Active Directory para Node.js"
keywords: Azure, Node, SDK, API, Armazenamento, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="2d5c8-104">Módulos do Azure Active Directory para Node.js</span><span class="sxs-lookup"><span data-stu-id="2d5c8-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2d5c8-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2d5c8-105">Overview</span></span>

<span data-ttu-id="2d5c8-106">A [ADAL (Azure Active Directory Authentication Library) para Node.js](https://www.npmjs.com/package/adal-node) permite que os aplicativos Node.js se autentiquem no AAD para acessarem os recursos Web protegidos pelo AAD.</span><span class="sxs-lookup"><span data-stu-id="2d5c8-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="2d5c8-107">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="2d5c8-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="2d5c8-108">Instalar os módulos npm</span><span class="sxs-lookup"><span data-stu-id="2d5c8-108">Install the npm modules</span></span>

<span data-ttu-id="2d5c8-109">Use npm para instalar os módulos de cliente ou gerenciamento de armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="2d5c8-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="2d5c8-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d5c8-110">Example</span></span>

<span data-ttu-id="2d5c8-111">Este exemplo da [amostra de credenciais de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) ilustra a autenticação de servidor-para-servidor por meio de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="2d5c8-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="2d5c8-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2d5c8-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="2d5c8-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2d5c8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
