---
title: Autenticar com os módulos do Gerenciamento do Azure para Node.js
description: Autenticar com uma entidade de serviço para os módulos de gerenciamento do Azure para Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="cae9c-103">Autenticar com os módulos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="cae9c-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="cae9c-104">Todas as APIs de serviço exigem autenticação por meio de um objeto `credentials` durante a instanciação.</span><span class="sxs-lookup"><span data-stu-id="cae9c-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="cae9c-105">Há três maneiras de autenticar e criar as credenciais necessárias por meio do SDK do Azure para Node.js:</span><span class="sxs-lookup"><span data-stu-id="cae9c-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="cae9c-106">Autenticação básica</span><span class="sxs-lookup"><span data-stu-id="cae9c-106">Basic authentication</span></span>
- <span data-ttu-id="cae9c-107">Logon interativo</span><span class="sxs-lookup"><span data-stu-id="cae9c-107">Interactive login</span></span>
- <span data-ttu-id="cae9c-108">Autenticação de entidade de serviço</span><span class="sxs-lookup"><span data-stu-id="cae9c-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="cae9c-109">Autenticação básica</span><span class="sxs-lookup"><span data-stu-id="cae9c-109">Basic authentication</span></span>

<span data-ttu-id="cae9c-110">Para autenticar programaticamente usando as credenciais da sua conta do Azure, use a função `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="cae9c-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="cae9c-111">O trecho de código JavaScript a seguir ilustra como usar a autenticação básica usando as credenciais armazenadas como variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="cae9c-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="cae9c-112">Logon interativo</span><span class="sxs-lookup"><span data-stu-id="cae9c-112">Interactive login</span></span>

<span data-ttu-id="cae9c-113">O logon interativo fornece um link e um código que permitem que o usuário se autentique de um navegador.</span><span class="sxs-lookup"><span data-stu-id="cae9c-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="cae9c-114">Use esse método quando várias contas forem usadas pelo mesmo script ou quando a intervenção do usuário for preferencial.</span><span class="sxs-lookup"><span data-stu-id="cae9c-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="cae9c-115">Autenticação de entidade de serviço</span><span class="sxs-lookup"><span data-stu-id="cae9c-115">Service principal authentication</span></span>

<span data-ttu-id="cae9c-116">[Logon interativo](#interactive-login) é a maneira mais fácil de autenticar.</span><span class="sxs-lookup"><span data-stu-id="cae9c-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="cae9c-117">No entanto, ao usar o SDK do Node.js, convém usar a autenticação da entidade de serviço em vez de fornecer suas credenciais de conta.</span><span class="sxs-lookup"><span data-stu-id="cae9c-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="cae9c-118">O tópico [Criar uma entidade de serviço do Azure com Node.js](./node-sdk-azure-authenticate-principal.md) explica várias técnicas para criar (e usar) uma entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="cae9c-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 