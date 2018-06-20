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
ms.openlocfilehash: 81958e3d928eb2fe7d391044e3242492e54a1011
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220538"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Criar uma entidade de serviço do Azure com Node.js 

Quando um aplicativo precisar acessar recursos, você poderá configurar uma identidade para o aplicativo e autenticá-lo com suas próprias credenciais. Essa identidade é conhecida como uma *entidade de serviço*. Essencialmente, você deve criar chaves para sua conta do Azure Active Directory fornecidas ao SDK para autenticação em vez de exigir a intervenção do usuário ou o nome de usuário e a senha.

A abordagem de entidade de serviço permite que você:
- Atribua permissões à identidade do aplicativo que sejam diferentes das suas próprias permissões. Normalmente, essas permissões são restritas a exatamente o que o aplicativo precisa fazer.
- Use um certificado para a autenticação ao executar um script autônomo.

Este tópico mostra três técnicas para a criação de uma entidade de serviço.

- Portal do Azure
- CLI do Azure 2.0
- SDK do Azure para Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Criar uma entidade de serviço usando o portal do Azure

Siga as etapas descritas no tópico [Usar o portal para criar um aplicativo e uma entidade de serviço do Azure Active Directory que possa acessar recursos](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) para gerar a entidade de serviço.

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Criar uma entidade de serviço usando a CLI do Azure 2.0

A criação de uma entidade de serviço usando a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) pode ser feita com as seguintes etapas:

1. Baixe a [CLI do Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

2. Abra uma janela de terminal.

3. Digite o seguinte comando para iniciar o processo de logon:

    ```shell
    $ az login
    ```

4. Chamar `az login` resulta em uma URL e em um código. Navegue até a URL especificada, insira o código e faça logon com sua identidade do Azure (isso poderá acontecer automaticamente se você já estiver conectado). Em seguida, você poderá acessar sua conta via CLI.

5. Obter sua ID da assinatura e locatário:

    ```shell
    $ az account list
    ```

    O texto a seguir mostra um exemplo da saída:

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

    **Observe a ID da assinatura, que será usada na Etapa 7.**

6. Crie uma entidade de serviço para obter um objeto JSON que contenha as outras informações necessária para você se autenticar no Azure.

    ```shell
    $ az ad sp create-for-rbac
    ```

    O texto a seguir mostra um exemplo da saída:

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Observe os valores de locatário, nome e senha que serão usados na Etapa 7.**

7. Defina as variáveis de ambiente substituindo os espaços reservados &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> pelos valores obtidos nas etapas 4 e 5. 

    **Como usar o Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Como usar o PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Criar uma entidade de serviço usando o SDK do Azure para Node.js

Para criar programaticamente uma entidade de serviço usando JavaScript, use o [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Como usar a entidade de serviço

Quando você tem uma entidade de serviço, o trecho de código JavaScript a seguir ilustra como usar as chaves de entidade de serviço para se autenticar com o SDK do Azure para Node.js. Modifique estes espaços reservados: &lt;clientId ou appId >, &lt;secret ou password > e &lt;domain ou tenant >,

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
