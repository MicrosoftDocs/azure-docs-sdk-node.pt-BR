---
title: Módulos do Azure HDInsight para Node.js
description: Referência dos módulos do Azure HDInsight para Node.js
author: mumian
ms.author: jgao
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 311933f619ceab5d679c8b0a767d3b52960c5ce1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Módulos do Azure HDInsight para Node.js

O Azure HDInsight é uma distribuição em nuvem dos componentes do Hadoop da HDP (Hortonworks Data Platform). O Apache Hadoop era a estrutura de código-fonte original para processamento distribuído e análise de grandes conjuntos de dados em clusters de computadores.

O HDInsight facilita o uso de tecnologias Hadoop com:
- Menos instalação e configuração. Veja Provisionar clusters do Hadoop no HDInsight.
- Alta disponibilidade e confiabilidade. Veja Disponibilidade e confiabilidade do HDInsight.
- Segurança e governança por meio da integração com o Active Directory. Veja Clusters ingressados no domínio.
- Dimensionamento dinâmico sem interromper trabalhos
- Atualizações de componentes e versões atuais. Veja Componentes do Hadoop e versões no HDInsight.
- Integração com outros serviços do Azure, incluindo aplicativos Web e Banco de Dados SQL

A pilha de tecnologias do Hadoop inclui software e utilitários relacionados, inclusive Apache Hive, HBase, Spark, Kafka e muitos outros. 

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-modules"></a>Instalar os módulos npm

Usar npm para instalar os módulos do Azure HDInsight para Node.js

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Exemplo 

Este exemplo cria um cliente do HD Insight e então lista todos os grupos disponíveis. 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
