---
title: Criar uma entidade de serviço do Azure com Node.js
description: Saiba como usar a autenticação da entidade de serviço por meio do Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51099015"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="c4636-103">Criar uma entidade de serviço do Azure com Node.js</span><span class="sxs-lookup"><span data-stu-id="c4636-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="c4636-104">Quando um aplicativo precisar acessar recursos, você poderá configurar uma identidade para o aplicativo e autenticá-lo com suas próprias credenciais.</span><span class="sxs-lookup"><span data-stu-id="c4636-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="c4636-105">Essa identidade é conhecida como uma *entidade de serviço*.</span><span class="sxs-lookup"><span data-stu-id="c4636-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="c4636-106">Essencialmente, você deve criar chaves para sua conta do Azure Active Directory fornecidas ao SDK para autenticação em vez de exigir a intervenção do usuário ou o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="c4636-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="c4636-107">A abordagem de entidade de serviço permite que você:</span><span class="sxs-lookup"><span data-stu-id="c4636-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="c4636-108">Atribua permissões à identidade do aplicativo que sejam diferentes das suas próprias permissões.</span><span class="sxs-lookup"><span data-stu-id="c4636-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="c4636-109">Normalmente, essas permissões são restritas a exatamente o que o aplicativo precisa fazer.</span><span class="sxs-lookup"><span data-stu-id="c4636-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="c4636-110">Use um certificado para a autenticação ao executar um script autônomo.</span><span class="sxs-lookup"><span data-stu-id="c4636-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="c4636-111">Este tópico mostra três técnicas para a criação de uma entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4636-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="c4636-112">Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="c4636-112">Azure portal</span></span>
- <span data-ttu-id="c4636-113">CLI do Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="c4636-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="c4636-114">SDK do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="c4636-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="c4636-115">Criar uma entidade de serviço usando o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="c4636-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="c4636-116">Siga as etapas descritas no tópico [Usar o portal para criar um aplicativo e uma entidade de serviço do Azure Active Directory que possa acessar recursos](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) para gerar a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4636-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="c4636-117">Criar uma entidade de serviço usando a CLI do Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="c4636-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="c4636-118">A criação de uma entidade de serviço usando a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) pode ser feita com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c4636-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="c4636-119">Baixe a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="c4636-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="c4636-120">Abra uma janela de terminal.</span><span class="sxs-lookup"><span data-stu-id="c4636-120">Open a terminal window.</span></span>

3. <span data-ttu-id="c4636-121">Digite o seguinte comando para iniciar o processo de logon:</span><span class="sxs-lookup"><span data-stu-id="c4636-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="c4636-122">Chamar `az login` resulta em uma URL e em um código.</span><span class="sxs-lookup"><span data-stu-id="c4636-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="c4636-123">Navegue até a URL especificada, insira o código e faça logon com sua identidade do Azure (isso poderá acontecer automaticamente se você já estiver conectado).</span><span class="sxs-lookup"><span data-stu-id="c4636-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="c4636-124">Em seguida, você poderá acessar sua conta via CLI.</span><span class="sxs-lookup"><span data-stu-id="c4636-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="c4636-125">Obter sua ID da assinatura e locatário:</span><span class="sxs-lookup"><span data-stu-id="c4636-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="c4636-126">O texto a seguir mostra um exemplo da saída:</span><span class="sxs-lookup"><span data-stu-id="c4636-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="c4636-127">**Observe a ID da assinatura, que será usada na Etapa 7.**</span><span class="sxs-lookup"><span data-stu-id="c4636-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="c4636-128">Crie uma entidade de serviço para obter um objeto JSON que contenha as outras informações necessária para você se autenticar no Azure.</span><span class="sxs-lookup"><span data-stu-id="c4636-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="c4636-129">O texto a seguir mostra um exemplo da saída:</span><span class="sxs-lookup"><span data-stu-id="c4636-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="c4636-130">**Observe os valores de locatário, nome e senha que serão usados na Etapa 7.**</span><span class="sxs-lookup"><span data-stu-id="c4636-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="c4636-131">Defina as variáveis de ambiente substituindo os espaços reservados &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> pelos valores obtidos nas etapas 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="c4636-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="c4636-132">**Como usar o Bash**</span><span class="sxs-lookup"><span data-stu-id="c4636-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="c4636-133">**Como usar o PowerShell**</span><span class="sxs-lookup"><span data-stu-id="c4636-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="c4636-134">Criar uma entidade de serviço usando o SDK do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="c4636-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="c4636-135">Para criar programaticamente uma entidade de serviço usando JavaScript, use o [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="c4636-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="c4636-136">Como usar a entidade de serviço</span><span class="sxs-lookup"><span data-stu-id="c4636-136">Using the service principal</span></span>

<span data-ttu-id="c4636-137">Quando você tem uma entidade de serviço, o snippet de código JavaScript a seguir ilustra como usar as chaves de entidade de serviço para se autenticar com o SDK do Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="c4636-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="c4636-138">Modifique estes espaços reservados: &lt;clientId ou appId >, &lt;secret ou password > e &lt;domain ou tenant >,</span><span class="sxs-lookup"><span data-stu-id="c4636-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
