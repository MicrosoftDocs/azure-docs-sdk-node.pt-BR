---
title: Módulos do Azure Active Directory para Node.js
description: Referência dos módulos do Azure Active Directory para Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c356801500aa3ef9038fc27634c8a95debf152b3
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="79bef-103">Módulos do Azure Active Directory para Node.js</span><span class="sxs-lookup"><span data-stu-id="79bef-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="79bef-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="79bef-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79bef-105">É altamente recomendável usar o [Microsoft Graph](https://graph.microsoft.io/) em vez da API do Azure AD Graph para acessar recursos do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="79bef-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="79bef-106">Nossos esforços de desenvolvimento agora estão concentrados no Microsoft Graph e não há planejamento de novas melhorias para a API do Azure AD Graph.</span><span class="sxs-lookup"><span data-stu-id="79bef-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="79bef-107">Há um número muito limitado de cenários para os quais a API do Azure AD Graph ainda pode ser apropriada; para obter mais informações, consulte a postagem no blog [Microsoft Graph ou o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) no Centro de Desenvolvimento do Office.</span><span class="sxs-lookup"><span data-stu-id="79bef-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="79bef-108">A [ADAL (Azure Active Directory Authentication Library) para Node.js](https://www.npmjs.com/package/adal-node) permite que os aplicativos Node.js se autentiquem no AAD para acessarem os recursos Web protegidos pelo AAD.</span><span class="sxs-lookup"><span data-stu-id="79bef-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="79bef-109">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="79bef-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="79bef-110">Instalar os módulos npm</span><span class="sxs-lookup"><span data-stu-id="79bef-110">Install the npm modules</span></span>

<span data-ttu-id="79bef-111">Use npm para instalar os módulos de cliente ou gerenciamento de armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="79bef-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="79bef-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79bef-112">Example</span></span>

<span data-ttu-id="79bef-113">Este exemplo da [amostra de credenciais de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) ilustra a autenticação de servidor-para-servidor por meio de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="79bef-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="79bef-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="79bef-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="79bef-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="79bef-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
