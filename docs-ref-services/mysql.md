---
title: Módulos MySQL do Azure para Node.js
description: Referência dos módulos do MySQL do Azure para Node.js
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51354140"
---
# <a name="azure-mysql-modules-for-nodejs"></a>Módulos MySQL do Azure para Node.js

A biblioteca de cliente recomendada para acessar o banco de dados MySQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para MySQL](https://github.com/sidorares/node-mysql2), que é um software livre. 

Saiba mais sobre o [Banco de Dados do Azure para MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Pacote de Cliente

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Use npm para instalar o módulo de cliente do MySQL.

```bash
npm install mysql2
```   

### <a name="example"></a>Exemplo

Este exemplo se conecta a um banco de dados MySQL e executa uma consulta simples para recuperar todos os clientes.

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>Exemplos

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
