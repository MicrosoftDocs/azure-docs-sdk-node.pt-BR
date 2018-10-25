---
title: Módulos de Autorização do Azure para Node.js
description: Referência dos módulos da Autorização do Azure para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49735061"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="e1894-103">Módulos de Autorização do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="e1894-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e1894-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e1894-104">Overview</span></span>

<span data-ttu-id="e1894-105">A Autenticação/Autorização do Serviço de Aplicativo do Azure é um recurso que oferece uma maneira para seu aplicativo conectar usuários de forma que o código não precise ser alterado no back-end do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1894-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="e1894-106">A autorização fornece uma maneira fácil de proteger o aplicativo e trabalhar com dados por usuário.</span><span class="sxs-lookup"><span data-stu-id="e1894-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="e1894-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e1894-107">Management package</span></span>

<span data-ttu-id="e1894-108">Use npm para instalar os módulos de Autorização do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="e1894-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e1894-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="e1894-109">Install the npm module</span></span>

<span data-ttu-id="e1894-110">Instalar o módulo npm de autorização do Azure</span><span class="sxs-lookup"><span data-stu-id="e1894-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="e1894-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1894-111">Example</span></span>

<span data-ttu-id="e1894-112">Este exemplo lista todas as atribuições de função para o grupo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="e1894-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e1894-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e1894-113">Samples</span></span>

<span data-ttu-id="e1894-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e1894-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
