---
title: Módulos do Azure para JavaScript
description: Visão geral dos módulos de serviço e gerenciamento do Azure para JavaScript
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49672991"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="c560b-103">Módulos do Azure para JavaScript</span><span class="sxs-lookup"><span data-stu-id="c560b-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="c560b-104">Gerencie recursos do Azure e conecte-se aos serviços de aplicativos JavaScript com os módulos do Azure para JavaScript.</span><span class="sxs-lookup"><span data-stu-id="c560b-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="c560b-105">O código está disponível como [módulos npm](node-sdk-azure-install.md) para uso em seus projetos.</span><span class="sxs-lookup"><span data-stu-id="c560b-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="c560b-106">Gerenciar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="c560b-106">Manage Azure resources</span></span>

<span data-ttu-id="c560b-107">Use os módulos de gerenciamento para criar e consultar os recursos de seus aplicativos ou para criar suas próprias ferramentas de automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="c560b-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="c560b-108">Por exemplo, para criar uma VM do Linux usando uma interface de rede existente, você deverá escrever o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c560b-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
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
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="c560b-109">Examine as [instruções de instalação](node-sdk-azure-install.md) para obter uma lista completa dos módulos e o [artigo de introdução](node-sdk-azure-get-started.md) para configurar a autenticação e executar o código de exemplo para criar e atualizar recursos em sua própria assinatura do Azure .</span><span class="sxs-lookup"><span data-stu-id="c560b-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="c560b-110">Conectar-se aos serviços do Azure</span><span class="sxs-lookup"><span data-stu-id="c560b-110">Connect to Azure services</span></span>

<span data-ttu-id="c560b-111">Além de usar os módulos do Azure para criar e gerenciar recursos no Azure, você também pode usar pacotes para se conectar e usar os serviços de nuvem do Azure em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c560b-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="c560b-112">Por exemplo, você pode atualizar um Banco de Dados SQL de tabela ou carregar arquivos no Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="c560b-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="c560b-113">Selecione o pacote necessário para um serviço específico na [lista completa](node-sdk-azure-install.md) e visite a [central de desenvolvedores do JavaScript](https://azure.microsoft.com/develop/nodejs/) para obter tutoriais e códigos de exemplo para aprender a usar os módulos em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c560b-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="c560b-114">Por exemplo, para imprimir o conteúdo de cada blob em um contêiner de armazenamento do Azure:</span><span class="sxs-lookup"><span data-stu-id="c560b-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="c560b-115">Referência e código de exemplo</span><span class="sxs-lookup"><span data-stu-id="c560b-115">Sample code and reference</span></span>

<span data-ttu-id="c560b-116">Os exemplos a seguir abordam tarefas comuns com os módulos de gerenciamento do Azure para Java e possuem códigos prontos para uso em seus próprios aplicativos:</span><span class="sxs-lookup"><span data-stu-id="c560b-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="c560b-117">Máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="c560b-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="c560b-118">Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="c560b-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="c560b-119">Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="c560b-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="c560b-120">Uma [referência](https://docs.microsoft.com/javascript/api) está disponível para todos os módulos nos módulos de serviço e de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="c560b-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="c560b-121">Novos recursos, alterações significativas, e instruções de migração de versões anteriores estão disponíveis nas [notas de versão](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="c560b-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>