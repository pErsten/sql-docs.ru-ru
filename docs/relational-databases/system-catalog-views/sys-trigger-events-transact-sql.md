---
description: sys.trigger_events (Transact-SQL)
title: sys. trigger_events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_events_TSQL
- trigger_events
- sys.trigger_events
- sys.trigger_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_events catalog view
ms.assetid: 92540447-131c-491c-b033-c064c7d950e1
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ead6f918e85c73d344924bfe1bc7c878bf4d44c6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537989"
---
# <a name="systrigger_events-transact-sql"></a>sys.trigger_events (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Содержит по одной строке для каждого события, в связи с которым срабатывает триггер.  
  
> [!NOTE]  
>  **sys. trigger_events** не применяется к уведомлениям о событиях.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.events>**|Не применяются|Наследует **object_id**, **тип**, **type_desc** столбцы из представления [sys. Events](../../relational-databases/system-catalog-views/sys-events-transact-sql.md).|  
|**is_first**|**bit**|Триггер помечен как первый срабатывающий триггер для этого события.|  
|**is_last**|**bit**|Триггер помечен как последний срабатывающий триггер для этого события.|  
|**event_group_type**|**int**|Группа событий, для которой создается триггер, или значение NULL, если триггер для группы событий не создается.|  
|**event_group_type_desc**|**nvarchar(60)**|Описание группы событий, для которой создается триггер, или значение NULL, если триггер для группы событий не создается.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
