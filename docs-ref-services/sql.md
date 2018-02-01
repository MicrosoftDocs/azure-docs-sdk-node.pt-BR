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
# <a name="azure-sql-modules-for-nodejs"></a>Módulos de SQL do Azure para Node.js

Trabalhe com os dados armazenados no [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) do Node.js.
A biblioteca de gerenciamento fornece uma interface para que seja fácil gerenciar bancos de dados SQL do Microsoft Azure.

## <a name="client-package"></a>Pacote de cliente

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de cliente do SQL Server

```bash
npm install tedious
```

### <a name="example"></a>Exemplo

Este exemplo se conecta a um banco de dados do SQL Server e executa uma consulta simples.

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

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-npm-modules"></a>Instalar módulos npm

Instalar o módulo npm de gerenciamento do SQL Server do Azure

```
npm install azure-arm-sql
```   

### <a name="example"></a>Exemplo

Autenticar, criar um cliente e listar todos os servidores.

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

## <a name="samples"></a>Exemplos

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
