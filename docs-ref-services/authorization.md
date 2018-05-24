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
ms.openlocfilehash: 5be0e069d0acf72de65e891e6304ef1ca78e967a
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>Módulos de Autorização do Azure para Node.js

## <a name="overview"></a>Visão geral

A Autenticação/Autorização do Serviço de Aplicativo do Azure é um recurso que oferece uma maneira para seu aplicativo conectar usuários de forma que o código não precise ser alterado no back-end do aplicativo. A autorização fornece uma maneira fácil de proteger o aplicativo e trabalhar com dados por usuário.

## <a name="management-package"></a>Pacote de gerenciamento

Use npm para instalar os módulos de Autorização do Azure para Node.js

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de autorização do Azure

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Exemplo

Este exemplo lista todas as atribuições de função para o grupo de recursos solicitado.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
