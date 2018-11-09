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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121845"
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Módulos de Azure Key Vault para Node.js

O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem. Usando o Cofre de Chaves, você pode criptografar chaves e segredos (como chaves de autenticação, chaves de conta de armazenamento, chaves de criptografia de dados, arquivos .PFX e senhas) usando chaves que são protegidas por HSMs (módulos de segurança de hardware). Para garantia extra, você pode importar ou gerar chaves em HSMs. Se você optar por fazer isso, a Microsoft processará suas chaves em HSMs FIPS 140-2 Nível 2 validados (hardware e firmware).

O Cofre da Chave simplifica o processo de gerenciamento de chaves e permite que você tenha controle das chaves que acessam e criptografam seus dados. Desenvolvedores podem criar chaves para desenvolvimento e teste em minutos e depois migrá-las diretamente para chaves de produção. Administradores de segurança podem conceder (e revogar) permissão a chaves conforme for necessário.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm 

Instalar o módulo npm do Azure Key Vault

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Exemplo

Este exemplo cria um novo serviço do Key Vault no Azure.

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

## <a name="samples"></a>Exemplos

- [Introdução ao Key Vault em Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Gerenciar recursos e grupos de recursos do Azure com Node.js](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Integração do Azure AD a um aplicativo Web NodeJS](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
