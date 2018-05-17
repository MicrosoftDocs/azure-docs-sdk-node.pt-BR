---
title: Introdução aos módulos do Azure para Node.js
description: Introdução à autenticação e ao gerenciamento de recursos com módulos do Azure para Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="305b0-103">Introdução aos módulos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="305b0-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="305b0-104">Este guia demonstra a instalação de módulos Node.js do Azure, a autenticação no Azure com uma entidade de serviço e a execução do código de exemplo que cria recursos na sua assinatura do Azure e se conecta aos serviços de nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="305b0-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="305b0-105">pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="305b0-105">Prerequisites</span></span>

- <span data-ttu-id="305b0-106">Uma conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="305b0-106">An Azure account.</span></span> <span data-ttu-id="305b0-107">Se você não tiver uma, [obtenha uma avaliação gratuita](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="305b0-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="305b0-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="305b0-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="305b0-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) ou [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="305b0-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="305b0-110">Prepare o seu ambiente</span><span class="sxs-lookup"><span data-stu-id="305b0-110">Prepare your environment</span></span>

<span data-ttu-id="305b0-111">Crie um novo projeto em um diretório vazio e instale os seguintes módulos npm:</span><span class="sxs-lookup"><span data-stu-id="305b0-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="305b0-112">Configurar a autenticação</span><span class="sxs-lookup"><span data-stu-id="305b0-112">Set up authentication</span></span>

<span data-ttu-id="305b0-113">Seu aplicativo Node.js precisa ler e criar permissões em sua assinatura do Azure para executar o exemplo de código neste guia.</span><span class="sxs-lookup"><span data-stu-id="305b0-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="305b0-114">Criar uma entidade de serviço e configurar seu aplicativo para ser executado com suas credenciais.</span><span class="sxs-lookup"><span data-stu-id="305b0-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="305b0-115">As entidades de serviço são uma conta não interativa associada à sua identidade para a qual você concede apenas os privilégios de que seu aplicativo precisa para ser executado.</span><span class="sxs-lookup"><span data-stu-id="305b0-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="305b0-116">[Criar uma entidade de serviço usando a CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) e capturar a saída.</span><span class="sxs-lookup"><span data-stu-id="305b0-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="305b0-117">Você precisará fornecer uma [senha segura](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) no argumento de senha, em vez de `MY_SECURE_PASSWORD`.</span><span class="sxs-lookup"><span data-stu-id="305b0-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="305b0-118">Exporte os valores para *appId*, *password* e *tenant* como variáveis de ambiente:</span><span class="sxs-lookup"><span data-stu-id="305b0-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="305b0-119">Obter a ID da assinatura com [az account show](https://docs.microsoft.com/cli/azure/account#show)</span><span class="sxs-lookup"><span data-stu-id="305b0-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="305b0-120">Exportar a ID da assinatura como uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="305b0-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="305b0-121">Criar uma máquina virtual Linux</span><span class="sxs-lookup"><span data-stu-id="305b0-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="305b0-122">Crie um novo arquivo *createVM.js* no diretório atual com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="305b0-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="305b0-123">Atualize o valor de `adminPass` com uma senha válida.</span><span class="sxs-lookup"><span data-stu-id="305b0-123">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
                        primary: true
                    }
                ]
            },
            storageProfile: {
                imageReference: {
                    publisher: 'Canonical',
                    offer: 'UbuntuServer',
                    sku: '16.04-LTS',
                    version: 'latest'
                },
            }
        };

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="305b0-124">Execute o exemplo da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="305b0-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="305b0-125">Quando o código for concluído, obtenha o IP de sua nova máquina virtual e faça logon com SSH usando o valor de `adminPass` do seu código.</span><span class="sxs-lookup"><span data-stu-id="305b0-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="305b0-126">Gravar um blob no Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="305b0-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="305b0-127">Crie um novo arquivo *uploadFile.js* no diretório atual com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="305b0-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="305b0-128">Execute o comando e então copie e cole a URL da saída no seu navegador da Web para exibir o arquivo no Armazenamento do Azure:</span><span class="sxs-lookup"><span data-stu-id="305b0-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="305b0-129">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="305b0-129">Clean up resources</span></span>

<span data-ttu-id="305b0-130">Exclua o grupo de recursos para remover os recursos criados neste guia.</span><span class="sxs-lookup"><span data-stu-id="305b0-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="305b0-131">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="305b0-131">Next steps</span></span>

<span data-ttu-id="305b0-132">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="305b0-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="305b0-133">Referência</span><span class="sxs-lookup"><span data-stu-id="305b0-133">Reference</span></span> 

<span data-ttu-id="305b0-134">Uma [referência](/javascript/api/overview/azure/) está disponível para todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="305b0-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="305b0-135">Obter ajuda e fazer comentários</span><span class="sxs-lookup"><span data-stu-id="305b0-135">Get help and give feedback</span></span>

<span data-ttu-id="305b0-136">Poste perguntas para a comunidade no [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span><span class="sxs-lookup"><span data-stu-id="305b0-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="305b0-137">Relate bugs e problemas não resolvidos com os módulos do Azure para Node.js no [GitHub do projeto](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="305b0-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

