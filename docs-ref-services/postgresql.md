---
title: "Módulos do PostgreSQL do Azure para Node.js"
description: "Referência dos módulos do Azure PostgreSQL para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, banco de dados, PostgreSQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Módulos do PostgreSQL do Azure para Node.js

## <a name="overview"></a>Visão geral

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
