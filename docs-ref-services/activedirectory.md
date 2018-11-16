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
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51419290"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Módulos do Azure Active Directory para Node.js

## <a name="overview"></a>Visão geral

> [!IMPORTANT]
> É altamente recomendável usar o [Microsoft Graph](https://graph.microsoft.io/) em vez da API do Azure AD Graph para acessar recursos do Azure Active Directory. Nossos esforços de desenvolvimento agora estão concentrados no Microsoft Graph e não há planejamento de novas melhorias para a API do Azure AD Graph. Há um número muito limitado de cenários para os quais a API do Azure AD Graph ainda pode ser apropriada; para obter mais informações, consulte a postagem no blog [Microsoft Graph ou o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) no Centro de Desenvolvimento do Office.

A [ADAL (Azure Active Directory Authentication Library) para Node.js](https://www.npmjs.com/package/adal-node) permite que os aplicativos Node.js se autentiquem no AAD para acessarem os recursos Web protegidos pelo AAD.

## <a name="client-package"></a>Pacote de cliente

### <a name="install-the-npm-modules"></a>Instalar os módulos npm

Use npm para instalar os módulos de cliente ou gerenciamento de armazenamento do Azure.

```bash
npm install adal-node
```   

### <a name="example"></a>Exemplo

Este exemplo da [amostra de credenciais de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) ilustra a autenticação de servidor-para-servidor por meio de credenciais do cliente.

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

## <a name="samples"></a>Exemplos

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
