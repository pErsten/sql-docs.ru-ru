---
description: Результаты обработки — обработка результатов
title: Обработка результатов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d61cdfb974a59f61fe53ba65656d49002a816d32
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868862"
---
# <a name="processing-results---process-results"></a>Результаты обработки — обработка результатов
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Обработка результатов в приложении ODBC заключается в том, чтобы сначала определить характеристики результирующего набора, а затем извлечь данные в переменные программы с помощью [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) или [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md).  
  
### <a name="to-process-results"></a>Обработка результатов  
  
1.  Получите сведения о результирующем наборе.  
  
2.  Если используются привязанные столбцы, вызовите функцию [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) для каждого столбца, чтобы привязать буфер программы к столбцу.  
  
3.  Для каждой строки в результирующем наборе сделайте следующее.  
  
    -   Вызовите функцию [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md), чтобы получить следующую строку.  
  
    -   Если используются привязанные столбцы, используйте данные, теперь доступные в привязанных буферах столбцов.  
  
    -   Если используются непривязанные столбцы, вызовите функцию [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) один или несколько раз, чтобы получить данные для непривязанных столбцов после последнего привязанного столбца. Вызовы функции **SQLGetData** должны следовать по возрастанию номера столбца.  
  
    -   Получение данных из столбца типа text или image производится многократным вызовом функции **SQLGetData** .  
  
4.  Когда функция [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md) указывает конец результирующего набора, возвращая SQL_NO_DATA, вызовите функцию [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](../../odbc/reference/syntax/sqlgetdiagrec-function.md) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
         Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра. Кроме того, если используются привязанные параметры, при каждом вызове функции [SQLExecute](../../odbc/reference/syntax/sqlexecute-function.md) или [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) инструкция SQL будет выполняться *S* раз, где *S* — количество элементов в массиве привязанных параметров. Это значит, что придется обработать *S* наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
    > [!NOTE]  
    >  Если результирующий набор содержит вычисляемые строки, каждая вычисляемая строка доступна как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
5.  Можно также вызвать функцию [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
6.  Если есть еще один результирующий набор, перейдите к шагу 1.  

> [!NOTE]  
>  Чтобы отменить обработку результирующего набора прежде, чем функция [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md) вернет значение SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>См. также:  
[Получение сведений о результирующем наборе &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
