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
# <a name="azure-cdn-modules-for-nodejs"></a>Módulos do CDN do Azure para Node.js

## <a name="overview"></a>Visão geral

A CDN (Rede de Distribuição de Conteúdo) do Azure oferece aos desenvolvedores uma solução global de fornecimento de conteúdo de alta largura de banda hospedada no Azure ou em qualquer outro local. Com a CDN, você pode armazenar em cache objetos publicamente disponíveis carregados do Armazenamento de Blobs do Azure, de um aplicativo Web, da máquina virtual, de uma pasta de aplicativo ou de outro local HTTP/HTTPS. O cache da CDN pode ser mantido em locais estratégicos para fornecer a máxima largura de banda para fornecimento de conteúdo aos usuários. A CDN normalmente é usada para fornecimento de conteúdo estático, como imagens, folhas de estilo, documentos, arquivos, scripts do lado do cliente e páginas HTML.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm CDN do Azure

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os perfis CDN.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
