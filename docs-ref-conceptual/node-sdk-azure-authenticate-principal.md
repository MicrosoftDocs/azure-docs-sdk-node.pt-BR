---
title: "Criar uma entidade de serviço do Azure com Node.js"
description: "Saiba como usar a autenticação da entidade de serviço por meio do Node.js"
keywords: "Azure, Node, SDK, API, autenticação, active directory, entidade de serviço"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="18648-104">Criar uma entidade de serviço do Azure com Node.js</span><span class="sxs-lookup"><span data-stu-id="18648-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="18648-105">Quando um aplicativo precisar acessar recursos, você poderá configurar uma identidade para o aplicativo e autenticá-lo com suas próprias credenciais.</span><span class="sxs-lookup"><span data-stu-id="18648-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="18648-106">Essa identidade é conhecida como uma *entidade de serviço*.</span><span class="sxs-lookup"><span data-stu-id="18648-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="18648-107">Essencialmente, você deve criar chaves para sua conta do Azure Active Directory fornecidas ao SDK para autenticação em vez de exigir a intervenção do usuário ou o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="18648-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="18648-108">A abordagem de entidade de serviço permite que você:</span><span class="sxs-lookup"><span data-stu-id="18648-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="18648-109">Atribuir permissões à identidade do aplicativo que são diferentes de suas próprias permissões.</span><span class="sxs-lookup"><span data-stu-id="18648-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="18648-110">Normalmente, essas permissões são restritas a exatamente o que o aplicativo precisa fazer.</span><span class="sxs-lookup"><span data-stu-id="18648-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="18648-111">Use um certificado para a autenticação ao executar um script autônomo.</span><span class="sxs-lookup"><span data-stu-id="18648-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="18648-112">Este tópico mostra três técnicas para a criação de uma entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="18648-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="18648-113">Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="18648-113">Azure portal</span></span>
- <span data-ttu-id="18648-114">CLI do Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="18648-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="18648-115">SDK do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="18648-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="18648-116">Criar uma entidade de serviço usando o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="18648-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="18648-117">Siga as etapas descritas no tópico [Usar o portal para criar um aplicativo e uma entidade de serviço do Azure Active Directory que possa acessar recursos](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) para gerar a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="18648-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="18648-118">Criar uma entidade de serviço usando a CLI do Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="18648-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="18648-119">A criação de uma entidade de serviço usando a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) pode ser feita com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="18648-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="18648-120">Baixe a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="18648-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="18648-121">Abra uma janela de terminal.</span><span class="sxs-lookup"><span data-stu-id="18648-121">Open a terminal window.</span></span>

3. <span data-ttu-id="18648-122">Digite o seguinte comando para iniciar o processo de logon:</span><span class="sxs-lookup"><span data-stu-id="18648-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="18648-123">Chamar `az login` resulta em uma URL e em um código.</span><span class="sxs-lookup"><span data-stu-id="18648-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="18648-124">Navegue até a URL especificada, insira o código e faça logon com sua identidade do Azure (isso poderá acontecer automaticamente se você já estiver conectado).</span><span class="sxs-lookup"><span data-stu-id="18648-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="18648-125">Em seguida, você poderá acessar sua conta via CLI.</span><span class="sxs-lookup"><span data-stu-id="18648-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="18648-126">Obter sua id da assinatura e locatário:</span><span class="sxs-lookup"><span data-stu-id="18648-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="18648-127">O texto a seguir mostra um exemplo da saída:</span><span class="sxs-lookup"><span data-stu-id="18648-127">The following shows an example of the output:</span></span>

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

    <span data-ttu-id="18648-128">**Observe a ID da assinatura, que será usada na Etapa 7.**</span><span class="sxs-lookup"><span data-stu-id="18648-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="18648-129">Crie uma entidade de serviço para obter um objeto JSON que contenha as outras informações de que você precisa para se autenticar no Azure.</span><span class="sxs-lookup"><span data-stu-id="18648-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="18648-130">O texto a seguir mostra um exemplo da saída:</span><span class="sxs-lookup"><span data-stu-id="18648-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="18648-131">**Observe os valores de locatário, nome e senha que serão usados na Etapa 7.**</span><span class="sxs-lookup"><span data-stu-id="18648-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="18648-132">Defina as variáveis de ambiente - substituindo os espaços reservados &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> pelos valores obtidos nas etapas 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="18648-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="18648-133">**Como usar o Bash**</span><span class="sxs-lookup"><span data-stu-id="18648-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="18648-134">**Usando o PowerShell**</span><span class="sxs-lookup"><span data-stu-id="18648-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="18648-135">Criar uma entidade de serviço usando o SDK do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="18648-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="18648-136">Para criar programaticamente uma entidade de serviço usando JavaScript, use o [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="18648-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="18648-137">Como usar a entidade de serviço</span><span class="sxs-lookup"><span data-stu-id="18648-137">Using the service principal</span></span>

<span data-ttu-id="18648-138">Quando você tiver uma entidade de serviço, o trecho de código JavaScript a seguir ilustra como usar as chaves de entidade de serviço para se autenticar com o SDK do Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="18648-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="18648-139">Modifique estes espaços reservados: &lt;clientId ou appId >, &lt;secret ou password > e &lt;domain ou tenant >,</span><span class="sxs-lookup"><span data-stu-id="18648-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

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
