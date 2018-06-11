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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="edc00-103">SDK do Microsoft Azure para Node.js - ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="edc00-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="edc00-104">Este projeto fornece um pacote de Node.js para acessar o Azure.</span><span class="sxs-lookup"><span data-stu-id="edc00-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="edc00-105">Agora, ele oferece suporte a:</span><span class="sxs-lookup"><span data-stu-id="edc00-105">Right now it supports:</span></span>
- <span data-ttu-id="edc00-106">**Node.js versão 6.x.x ou superior**</span><span class="sxs-lookup"><span data-stu-id="edc00-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="edc00-107">Recursos</span><span class="sxs-lookup"><span data-stu-id="edc00-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="edc00-108">Como instalar</span><span class="sxs-lookup"><span data-stu-id="edc00-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="edc00-109">Como usar</span><span class="sxs-lookup"><span data-stu-id="edc00-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="edc00-110">Autenticação, criação de cliente e containerServices de lista como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="edc00-110">Authentication, client creation and list containerServices as an example.</span></span>

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

## <a name="related-projects"></a><span data-ttu-id="edc00-111">Projetos relacionados</span><span class="sxs-lookup"><span data-stu-id="edc00-111">Related projects</span></span>

- [<span data-ttu-id="edc00-112">Microsoft Azure SDK para Node.js</span><span class="sxs-lookup"><span data-stu-id="edc00-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)