---
title: Módulos do Serviço de Contêiner do Azure para Node.js
description: Referência dos Módulos do Serviço de Contêiner do Azure para Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689819"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>SDK do Microsoft Azure para Node.js - ContainerServiceClient
Este projeto fornece um pacote de Node.js para acessar o Azure. Agora, ele oferece suporte a:
- **Node.js versão 6.x.x ou superior**

## <a name="features"></a>Recursos


## <a name="how-to-install"></a>Como instalar

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Como usar

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Autenticação, criação de cliente e containerServices de lista como um exemplo.

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a>Projetos relacionados

- [Microsoft Azure SDK para Node.js](https://github.com/Azure/azure-sdk-for-node)