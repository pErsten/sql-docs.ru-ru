---
description: sys.dm_repl_tranhash (Transact-SQL)
title: sys. dm_repl_tranhash (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 35bb540ff2b73a44de324a51937552ae7cc3ec56
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536907"
---
# <a name="sysdm_repl_tranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о транзакции, реплицируемой в публикации транзакций.  
  
|column_name|Тип данных|description|  
|------------------|----------------|-----------------|  
|**контейнеры**|**bigint**|Количество сегментов в хэш-таблице.|  
|**hashed_trans**|**bigint**|Количество зафиксированных транзакций, реплицированных в текущем пакете.|  
|**completed_trans**|**bigint**|Количество транзакций, выполненных до настоящего момента.|  
|**compensated_trans**|**bigint**|Количество транзакций, содержащих частичный откат.|  
|**first_begin_lsn**|**nvarchar (64)**|Самый ранний начальный регистрационный номер транзакции в журнале (LSN) в текущем пакете.|  
|**last_commit_lsn**|**nvarchar (64)**|Последняя фиксация номера LSN в текущем пакете.|  
  
## <a name="permissions"></a>Разрешения  
 Для вызова **dm_repl_tranhash**требуется разрешение на просмотр состояния базы данных публикации.  
  
## <a name="remarks"></a>Примечания  
 Возвращаются сведения только по реплицируемым объектам базы данных, которые загружены в кэш статей репликации.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с репликацией &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
