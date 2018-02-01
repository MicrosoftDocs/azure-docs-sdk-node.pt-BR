---
title: "Módulos do PostgreSQL do Azure para Node.js"
description: "Referência dos módulos do Azure PostgreSQL para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: d8a2c7fe90746def7e50a7af3a0f470213eed197
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Módulos do PostgreSQL do Azure para Node.js

A biblioteca de cliente recomendada para acessar o banco de dados PostgreSQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para PostgreSQL](https://www.npmjs.com/package/pg), que é um software livre. Essa biblioteca é um cliente PostgreSQL sem bloqueio para Node.js, dando suporte a JavaScript puro e associações libpq nativas opcionais.

Saiba mais sobre o [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>Pacote de cliente

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar o módulo de cliente PostgreSQL.

```bash
npm install pg
```   

### <a name="example"></a>Exemplo

Este exemplo abre uma conexão de cliente e executa uma consulta simples.

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>Exemplos

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
