---
title: "Código de exemplo para usar bancos de dados do Azure com o Node.js"
description: "Código de exemplo que ilustra o uso de bancos de dados do Azure com Node.js."
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="02129-103">Código de exemplo para usar bancos de dados do Azure com o Node.js</span><span class="sxs-lookup"><span data-stu-id="02129-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="02129-104">O código de exemplo a seguir ilustra o uso de bancos de dados do Azure com Node.js.</span><span class="sxs-lookup"><span data-stu-id="02129-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="02129-105">Se você precisar de código para outras tarefas, poderá procurar na lista completa de [exemplos do Node.js do Azure](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="02129-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="02129-106">**Banco de Dados Cosmos**</span><span class="sxs-lookup"><span data-stu-id="02129-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="02129-107">Usar o Azure Cosmos DB e a API do Graph</span><span class="sxs-lookup"><span data-stu-id="02129-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="02129-108">Mostra como usar o Azure Cosmos DB com a API do Graph para armazenar e acessar dados de um aplicativo Node.js.</span><span class="sxs-lookup"><span data-stu-id="02129-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="02129-109">Usar a API do Azure Cosmos DB e do Document DB</span><span class="sxs-lookup"><span data-stu-id="02129-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="02129-110">Mostra como usar o Azure Cosmos DB com a API do DocumentDB para armazenar e acessar dados de um aplicativo Node.js.</span><span class="sxs-lookup"><span data-stu-id="02129-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="02129-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="02129-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="02129-112">Desenvolvimento de aplicativo Web com Node.js e Express usando DocumentDB</span><span class="sxs-lookup"><span data-stu-id="02129-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="02129-113">Mostra como usar o Azure DocumentDB para armazenar e acessar dados de um aplicativo Node.js Express no Azure.</span><span class="sxs-lookup"><span data-stu-id="02129-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="02129-114">Desenvolvimento de um aplicativo de console do Node.js usando o DocumentDB</span><span class="sxs-lookup"><span data-stu-id="02129-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="02129-115">Este exemplo mostra como começar a usar rapidamente o serviço Microsoft Azure DocumentDB e o Node.js.</span><span class="sxs-lookup"><span data-stu-id="02129-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="02129-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="02129-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="02129-117">Aplicativo Web Node.js e MongoDB no Azure</span><span class="sxs-lookup"><span data-stu-id="02129-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="02129-118">Aplicativo de exemplo que você pode usar para acompanhar o tutorial, [Compilar um aplicativo Web Node.js e MongoDB no Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span><span class="sxs-lookup"><span data-stu-id="02129-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="02129-119">**Banco de Dados SQL**</span><span class="sxs-lookup"><span data-stu-id="02129-119">**SQL Database**</span></span> ||
| [<span data-ttu-id="02129-120">Banco de Dados SQL do Azure: usar o Node.js para se conectar e consultar dados</span><span class="sxs-lookup"><span data-stu-id="02129-120">Azure SQL Database: Use Node.js to connect and query data</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | <span data-ttu-id="02129-121">Demonstra como se conectar a um banco de dados SQL do Azure usando Node.js; em seguida, use instruções Transact-SQL para consultar, inserir, atualizar e excluir dados no banco de dados por meio das plataformas Windows, Ubuntu Linux e Mac.</span><span class="sxs-lookup"><span data-stu-id="02129-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |