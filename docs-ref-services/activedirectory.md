---
title: "Módulos do Azure Active Directory para Node.js"
description: "Referência dos módulos do Azure Active Directory para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="b3092-103">Módulos do Azure Active Directory para Node.js</span><span class="sxs-lookup"><span data-stu-id="b3092-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b3092-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b3092-104">Overview</span></span>

<span data-ttu-id="b3092-105">A [ADAL (Azure Active Directory Authentication Library) para Node.js](https://www.npmjs.com/package/adal-node) permite que os aplicativos Node.js se autentiquem no AAD para acessarem os recursos Web protegidos pelo AAD.</span><span class="sxs-lookup"><span data-stu-id="b3092-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="b3092-106">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="b3092-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="b3092-107">Instalar os módulos npm</span><span class="sxs-lookup"><span data-stu-id="b3092-107">Install the npm modules</span></span>

<span data-ttu-id="b3092-108">Use npm para instalar os módulos de cliente ou gerenciamento de armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="b3092-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="b3092-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3092-109">Example</span></span>

<span data-ttu-id="b3092-110">Este exemplo da [amostra de credenciais de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) ilustra a autenticação de servidor-para-servidor por meio de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="b3092-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b3092-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b3092-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="b3092-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b3092-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
