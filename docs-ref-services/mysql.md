---
title: Módulos MySQL do Azure para Node.js
description: Referência dos módulos do MySQL do Azure para Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 21b98aeba1e21ec1d9f7da4a115110fffe05b2b8
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="ba057-103">Módulos MySQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="ba057-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="ba057-104">A biblioteca de cliente recomendada para acessar o banco de dados MySQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para MySQL](https://github.com/sidorares/node-mysql2), que é um software livre.</span><span class="sxs-lookup"><span data-stu-id="ba057-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="ba057-105">Saiba mais sobre o [Banco de Dados do Azure para MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="ba057-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="ba057-106">Pacote de Cliente</span><span class="sxs-lookup"><span data-stu-id="ba057-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ba057-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="ba057-107">Install the npm module</span></span>

<span data-ttu-id="ba057-108">Use npm para instalar o módulo de cliente do MySQL.</span><span class="sxs-lookup"><span data-stu-id="ba057-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="ba057-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba057-109">Example</span></span>

<span data-ttu-id="ba057-110">Este exemplo se conecta a um banco de dados MySQL e executa uma consulta simples para recuperar todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="ba057-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ba057-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ba057-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="ba057-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ba057-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
