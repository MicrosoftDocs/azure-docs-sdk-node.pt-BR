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
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Módulos de Serviços Cognitivos do Azure para Node.js

Serviços Cognitivos do Azure é um conjunto de APIs, SDKs e serviços disponíveis para desenvolvedores para tornar seus aplicativos mais inteligentes, atraentes e descobríveis. Os Serviços Cognitivos da Microsoft ampliam o portfólio em evolução da Microsoft de APIs de machine learning e permitem aos desenvolvedores adicionar facilmente recursos inteligentes – como emoção e detecção de vídeo; reconhecimento facial, de fala e de visão, além de compreensão de fala e de idioma – a seus aplicativos. Nossa visão se destina a experiências de computação mais pessoais e produtividade aprimorada auxiliadas por sistemas que cada vez mais possam ver, ouvir, falar, compreender e até mesmo começar a raciocinar.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de Serviços Cognitivos do Azure

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Exemplo

Este exemplo lista todas as contas de serviço cognitivo.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
