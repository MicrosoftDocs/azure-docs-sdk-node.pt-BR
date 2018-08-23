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
ms.sourcegitcommit: 286f52ea38c9eff2ec9d4f8cabeb86f62fd9c406
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2018
ms.locfileid: "41691766"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="62a00-103">Módulos MySQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="62a00-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="62a00-104">A biblioteca de cliente recomendada para acessar o banco de dados MySQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para MySQL](https://github.com/sidorares/node-mysql2), que é um software livre.</span><span class="sxs-lookup"><span data-stu-id="62a00-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="62a00-105">Saiba mais sobre o [Banco de Dados do Azure para MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="62a00-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="62a00-106">Pacote de Cliente</span><span class="sxs-lookup"><span data-stu-id="62a00-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="62a00-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="62a00-107">Install the npm module</span></span>

<span data-ttu-id="62a00-108">Use npm para instalar o módulo de cliente do MySQL.</span><span class="sxs-lookup"><span data-stu-id="62a00-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="62a00-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62a00-109">Example</span></span>

<span data-ttu-id="62a00-110">Este exemplo se conecta a um banco de dados MySQL e executa uma consulta simples para recuperar todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="62a00-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="62a00-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="62a00-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="62a00-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="62a00-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
