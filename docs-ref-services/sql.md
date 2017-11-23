---
title: "Módulos de SQL do Azure para Node.js"
description: "Referência dos módulos do SQL do Azure para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="37483-104">Módulos de SQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="37483-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="37483-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="37483-105">Overview</span></span>

<span data-ttu-id="37483-106">Trabalhe com os dados armazenados no [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) do Node.js.</span><span class="sxs-lookup"><span data-stu-id="37483-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="37483-107">A biblioteca de gerenciamento fornece uma interface para que seja fácil gerenciar bancos de dados SQL do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="37483-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="37483-108">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="37483-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="37483-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="37483-109">Install the npm module</span></span>

<span data-ttu-id="37483-110">Instalar o módulo npm de cliente do SQL Server</span><span class="sxs-lookup"><span data-stu-id="37483-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="37483-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37483-111">Example</span></span>

<span data-ttu-id="37483-112">Este exemplo se conecta a um banco de dados do SQL Server e executa uma consulta simples.</span><span class="sxs-lookup"><span data-stu-id="37483-112">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="37483-113">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="37483-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="37483-114">Instalar módulos npm</span><span class="sxs-lookup"><span data-stu-id="37483-114">Install npm modules</span></span>

<span data-ttu-id="37483-115">Instalar o módulo npm de gerenciamento do SQL Server do Azure</span><span class="sxs-lookup"><span data-stu-id="37483-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="37483-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37483-116">Example</span></span>

<span data-ttu-id="37483-117">Autenticar, criar um cliente e listar todos os servidores.</span><span class="sxs-lookup"><span data-stu-id="37483-117">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="37483-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="37483-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="37483-119">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="37483-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
