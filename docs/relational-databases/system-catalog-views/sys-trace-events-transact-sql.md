---
description: sys.trace_events (Transact-SQL)
title: sys. trace_events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0b83821952fb9b7aa96a1c5c1da4033da1e750aa
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544967"
---
# <a name="systrace_events-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Представление каталога **sys. trace_events** содержит список всех событий трассировки SQL. Эти события трассировки не изменились в данной версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> **ВАЖНО!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте представления каталога расширенных событий.  
  
 Дополнительные сведения об этих событиях трассировки см. в разделе [SQL Server ссылка на класс событий](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|Уникальный идентификатор события. Этот столбец также находится в представлениях каталога **sys. trace_event_bindings** и **sys. trace_subclass_values** .|  
|**category_id**|**smallint**|Идентификатор категории события. Этот столбец также находится в представлении каталога **sys. trace_categories** .|  
|**name**|**nvarchar(128)**|Уникальное имя события. Этот аргумент не локализуется.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. traces &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
