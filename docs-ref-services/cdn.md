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
ms.openlocfilehash: b330eeedc178f20064b4a6b1c3f4f7d266590f11
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
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
