---
title: Módulos do Azure para Node.js
description: Visão geral dos módulos de serviço e gerenciamento do Azure para Node.js
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220528"
---
# <a name="azure-modules-for-nodejs"></a>Módulos do Azure para Node.js

Gerencie recursos do Azure e conecte-se aos serviços de aplicativos Node.js com os módulos do Azure para Node.js. O código está disponível como [módulos npm](node-sdk-azure-install.md) para uso em seus projetos. 

## <a name="manage-azure-resources"></a>Gerenciar recursos do Azure

Use os módulos de gerenciamento para criar e consultar os recursos de seus aplicativos ou para criar suas próprias ferramentas de automação do Azure. 

Por exemplo, para criar uma VM do Linux usando uma interface de rede existente, você deverá escrever o código a seguir:

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

Examine as [instruções de instalação](node-sdk-azure-install.md) para obter uma lista completa dos módulos e o [artigo de introdução](node-sdk-azure-get-started.md) para configurar a autenticação e executar o código de exemplo para criar e atualizar recursos em sua própria assinatura do Azure . 

## <a name="connect-to-azure-services"></a>Conectar-se aos serviços do Azure

Além de usar os módulos do Azure para criar e gerenciar recursos no Azure, você também pode usar pacotes para se conectar e usar os serviços de nuvem do Azure em seus aplicativos. Por exemplo, você pode atualizar um Banco de Dados SQL de tabela ou carregar arquivos no Armazenamento do Azure. Selecione o pacote necessário para um serviço específico na [lista completa](node-sdk-azure-install.md) e visite a [central de desenvolvedores do Node.js](https://azure.microsoft.com/develop/nodejs/) para obter tutoriais e códigos de exemplo para aprender a usar os módulos em seus aplicativos.

Por exemplo, para imprimir o conteúdo de cada blob em um contêiner de armazenamento do Azure:

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>Referência e código de exemplo

Os exemplos a seguir abordam tarefas comuns com os módulos de gerenciamento do Azure para Java e possuem códigos prontos para uso em seus próprios aplicativos:

- [Máquinas virtuais](node-samples-services-compute.md)
- [Aplicativos Web](node-samples-services-web-and-mobile.md)
- [Banco de Dados SQL](node-samples-services-database.md)
   
Uma [referência](https://docs.microsoft.com/javascript/api) está disponível para todos os módulos nos módulos de serviço e de gerenciamento. Novos recursos, alterações significativas, e instruções de migração de versões anteriores estão disponíveis nas [notas de versão](https://github.com/Azure/azure-sdk-for-node/releases).