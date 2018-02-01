---
title: "Módulos de SQL do Azure para Node.js"
description: "Referência dos módulos do SQL do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 8ebcfbcbf39def1774a702c9f18a4e3f5ab86931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="09b0c-103">Módulos de SQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="09b0c-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="09b0c-104">Trabalhe com os dados armazenados no [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) do Node.js.</span><span class="sxs-lookup"><span data-stu-id="09b0c-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="09b0c-105">A biblioteca de gerenciamento fornece uma interface para que seja fácil gerenciar bancos de dados SQL do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="09b0c-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="09b0c-106">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="09b0c-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="09b0c-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="09b0c-107">Install the npm module</span></span>

<span data-ttu-id="09b0c-108">Instalar o módulo npm de cliente do SQL Server</span><span class="sxs-lookup"><span data-stu-id="09b0c-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="09b0c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b0c-109">Example</span></span>

<span data-ttu-id="09b0c-110">Este exemplo se conecta a um banco de dados do SQL Server e executa uma consulta simples.</span><span class="sxs-lookup"><span data-stu-id="09b0c-110">This example connects to a SQL Server database and perform a simple query.</span></span>

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a><span data-ttu-id="09b0c-111">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="09b0c-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="09b0c-112">Instalar módulos npm</span><span class="sxs-lookup"><span data-stu-id="09b0c-112">Install npm modules</span></span>

<span data-ttu-id="09b0c-113">Instalar o módulo npm de gerenciamento do SQL Server do Azure</span><span class="sxs-lookup"><span data-stu-id="09b0c-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="09b0c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b0c-114">Example</span></span>

<span data-ttu-id="09b0c-115">Autenticar, criar um cliente e listar todos os servidores.</span><span class="sxs-lookup"><span data-stu-id="09b0c-115">Authenticate, create a client, and list all servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="09b0c-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="09b0c-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="09b0c-117">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="09b0c-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
