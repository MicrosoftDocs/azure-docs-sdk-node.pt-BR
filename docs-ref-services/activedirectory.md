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
# <a name="azure-active-directory-modules-for-nodejs"></a>Módulos do Azure Active Directory para Node.js

## <a name="overview"></a>Visão geral

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
