---
title: "Módulos de Autorização do Azure para Node.js"
description: "Referência dos módulos da Autorização do Azure para Node.js"
keywords: "Azure, SDK, API, Autorização, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="80be9-104">Módulos de Autorização do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="80be9-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="80be9-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="80be9-105">Overview</span></span>

<span data-ttu-id="80be9-106">A Autenticação/Autorização do Serviço de Aplicativo do Azure é um recurso que oferece uma maneira para seu aplicativo conectar usuários de forma que o código não precise ser alterado no back-end do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80be9-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="80be9-107">A autorização fornece uma maneira fácil de proteger o aplicativo e trabalhar com dados por usuário.</span><span class="sxs-lookup"><span data-stu-id="80be9-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="80be9-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="80be9-108">Management package</span></span>

<span data-ttu-id="80be9-109">Use npm para instalar os módulos de Autorização do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="80be9-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="80be9-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="80be9-110">Install the npm module</span></span>

<span data-ttu-id="80be9-111">Instalar o módulo npm de autorização do Azure</span><span class="sxs-lookup"><span data-stu-id="80be9-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="80be9-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80be9-112">Example</span></span>

<span data-ttu-id="80be9-113">Este exemplo lista todas as atribuições de função para o grupo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="80be9-113">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="80be9-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="80be9-114">Samples</span></span>

<span data-ttu-id="80be9-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="80be9-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
