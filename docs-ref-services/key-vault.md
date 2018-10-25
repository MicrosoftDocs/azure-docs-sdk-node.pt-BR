---
title: Módulos de Azure Key Vault para Node.js
description: Referência dos módulos do Azure Key Vault para Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49804416"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="f9f88-103">Módulos de Azure Key Vault para Node.js</span><span class="sxs-lookup"><span data-stu-id="f9f88-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="f9f88-104">O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem.</span><span class="sxs-lookup"><span data-stu-id="f9f88-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="f9f88-105">Usando o Cofre de Chaves, você pode criptografar chaves e segredos (como chaves de autenticação, chaves de conta de armazenamento, chaves de criptografia de dados, arquivos .PFX e senhas) usando chaves que são protegidas por HSMs (módulos de segurança de hardware).</span><span class="sxs-lookup"><span data-stu-id="f9f88-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="f9f88-106">Para garantia extra, você pode importar ou gerar chaves em HSMs.</span><span class="sxs-lookup"><span data-stu-id="f9f88-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="f9f88-107">Se você optar por fazer isso, a Microsoft processará suas chaves em HSMs FIPS 140-2 Nível 2 validados (hardware e firmware).</span><span class="sxs-lookup"><span data-stu-id="f9f88-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="f9f88-108">O Cofre da Chave simplifica o processo de gerenciamento de chaves e permite que você tenha controle das chaves que acessam e criptografam seus dados.</span><span class="sxs-lookup"><span data-stu-id="f9f88-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="f9f88-109">Desenvolvedores podem criar chaves para desenvolvimento e teste em minutos e depois migrá-las diretamente para chaves de produção.</span><span class="sxs-lookup"><span data-stu-id="f9f88-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="f9f88-110">Administradores de segurança podem conceder (e revogar) permissão a chaves conforme for necessário.</span><span class="sxs-lookup"><span data-stu-id="f9f88-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="f9f88-111">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f9f88-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f9f88-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="f9f88-112">Install the npm module</span></span> 

<span data-ttu-id="f9f88-113">Instalar o módulo npm do Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="f9f88-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="f9f88-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9f88-114">Example</span></span>

<span data-ttu-id="f9f88-115">Este exemplo cria um novo serviço do Key Vault no Azure.</span><span class="sxs-lookup"><span data-stu-id="f9f88-115">This example creates a new Key Vault service in Azure.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a><span data-ttu-id="f9f88-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f9f88-116">Samples</span></span>

- [<span data-ttu-id="f9f88-117">Introdução ao Key Vault em Node.js</span><span class="sxs-lookup"><span data-stu-id="f9f88-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="f9f88-118">Gerenciar recursos e grupos de recursos do Azure com Node.js</span><span class="sxs-lookup"><span data-stu-id="f9f88-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="f9f88-119">Integração do Azure AD a um aplicativo Web NodeJS</span><span class="sxs-lookup"><span data-stu-id="f9f88-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="f9f88-120">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f9f88-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
