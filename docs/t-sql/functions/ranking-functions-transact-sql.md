---
description: Ранжирующие функции (Transact-SQL)
title: Ранжирующая функция (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ranking functions
- row ranking [SQL Server]
- functions [SQL Server], ranking
- ranking rows
ms.assetid: e7f917ba-bf4a-4fe0-b342-a91bcf88a71b
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cf854b2edac064596bcce2ff417a6151f8bb170c
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380667"
---
# <a name="ranking-functions-transact-sql"></a>Ранжирующие функции (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Ранжирующие функции возвращают ранжирующее значение для каждой строки в секции. В зависимости от используемой функции значения некоторых строк могут совпадать. Ранжирующие функции являются недетерминированными.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит следующие ранжирующие функции:  

:::row:::
    :::column:::
        [RANK](../../t-sql/functions/rank-transact-sql.md)
    :::column-end:::
    :::column:::
        [NTILE](../../t-sql/functions/ntile-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [DENSE_RANK](../../t-sql/functions/dense-rank-transact-sql.md)
    :::column-end:::
    :::column:::
        [ROW_NUMBER](../../t-sql/functions/row-number-transact-sql.md)
    :::column-end:::
:::row-end:::
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование четырех ранжирующих функций в одном запросе. Примеры по каждой ранжирующей функции см. в посвященных им статьях.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,ROW_NUMBER() OVER (ORDER BY a.PostalCode) AS "Row Number"  
    ,RANK() OVER (ORDER BY a.PostalCode) AS Rank  
    ,DENSE_RANK() OVER (ORDER BY a.PostalCode) AS "Dense Rank"  
    ,NTILE(4) OVER (ORDER BY a.PostalCode) AS Quartile  
    ,s.SalesYTD  
    ,a.PostalCode  
FROM Sales.SalesPerson AS s   
    INNER JOIN Person.Person AS p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address AS a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL AND SalesYTD <> 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|FirstName|LastName|Row Number|Rank|Dense Rank|Quartile|SalesYTD|PostalCode|  
|---------------|--------------|----------------|----------|----------------|--------------|--------------|----------------|  
|Michael|Blythe|1|1|1|1|4557045,0459|98027|  
|Linda|Mitchell|2|1|1|1|5200475,2313|98027|  
|Jillian|Carson|3|1|1|1|3857163,6332|98027|  
|Garrett|Vargas|4|1|1|1|1764938,9859|98027|  
|Tsvi|Reiter|5|1|1|2|2811012,7151|98027|  
|Shu|Ito|6|6|2|2|3018725,4858|98055|  
|Josй|Saraiva|7|6|2|2|3189356,2465|98055|  
|David|Campbell|8|6|2|3|3587378,4257|98055|  
|Tete|Mensa-Annan|9|6|2|3|1931620,1835|98055|  
|Lynn|Tsoflias|10|6|2|3|1758385,926|98055|  
|Rachel|Valdez|11|6|2|4|2241204,0424|98055|  
|Jae|Pak|12|6|2|4|5015682,3752|98055|  
|Ranjit|Varkey Chudukatil|13|6|2|4|3827950,238|98055|  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
