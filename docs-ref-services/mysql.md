---
title: "Módulos MySQL do Azure para Node.js"
description: "Referência dos módulos do MySQL do Azure para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, banco de dados, MySQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="620ce-104">Módulos MySQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="620ce-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="620ce-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="620ce-105">Overview</span></span>

<span data-ttu-id="620ce-106">A biblioteca de cliente recomendada para acessar o banco de dados MySQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para MySQL](https://github.com/sidorares/node-mysql2), que é um software livre.</span><span class="sxs-lookup"><span data-stu-id="620ce-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="620ce-107">Saiba mais sobre o [Banco de Dados do Azure para MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="620ce-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="620ce-108">Pacote de Cliente</span><span class="sxs-lookup"><span data-stu-id="620ce-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="620ce-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="620ce-109">Install the npm module</span></span>

<span data-ttu-id="620ce-110">Use npm para instalar o módulo de cliente do MySQL.</span><span class="sxs-lookup"><span data-stu-id="620ce-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="620ce-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="620ce-111">Example</span></span>

<span data-ttu-id="620ce-112">Este exemplo se conecta a um banco de dados MySQL e executa uma consulta simples para recuperar todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="620ce-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="620ce-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="620ce-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="620ce-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="620ce-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
