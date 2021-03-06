---
title: sys.dm_pdw_nodes_exec_query_plan (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее инструкцию Showplan в формате XML для пакета, указанного в маркере плана. План, указанный в дескрипторе плана может быть кэширован или выполняться в данный момент.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 06c5acb9480f52d0cadf84c54aa39bbc9bae12d9
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2020
ms.locfileid: "94584941"
---
# <a name="syspdw_nodes_dm_exec_query_plan-transact-sql"></a>sys.pdw_nodes_dm_exec_query_plan (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Возвращает события инструкции Showplan в XML-формате для пакета, указанного в дескрипторе плана. План, указанный в дескрипторе плана может быть кэширован или выполняться в данный момент.  

> [!note] 
> В синапсе SQL добавление пробелов в запросе является изменением запроса, которое приводит к повторному вычислению хэша запроса, а предыдущий кэшированный план выполнения не используется заново.


## <a name="table-returned"></a>Таблица возвращена  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Уникальный числовой идентификатор, связанный с узлом.| 
|**DBID**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для незапланированных и подготовленных инструкций SQL — идентификатор базы данных, в которой были скомпилированы инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.|  
|**number**|**smallint**|Целое число нумерованных хранимых процедур. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.| 
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**xml**|Содержит представление Showplan времени компиляции для плана выполнения запроса, указанного в *plan_handle*. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.|  
  
## <a name="remarks"></a>Комментарии  
Те же примечания в [sys.dm_exec_query_plan](./sys-dm-exec-query-plan-transact-sql.md?view=sql-server-ver15) применяются.  
  
## <a name="permissions"></a>Разрешения  
 Требуется роль сервера **sysadmin** или `VIEW SERVER STATE` разрешение на сервере.  
  
## <a name="see-also"></a>См. также статью  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные советы по разработке см. в статье [Общие сведения о разработке для Azure синапсе Analytics](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).
