---
description: MSrepl_commands (Transact-SQL)
title: MSrepl_commands (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c8596aefdaecce0e7d39033b2a484ebfe6a4f46b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540292"
---
# <a name="msrepl_commands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSrepl_commands** содержит строки реплицированных команд. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**xact_seqno**|**varbinary (16)**|Номер последовательности транзакции.|  
|**type**|**int**|Тип команды.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**originator_id**|**int**|Идентификатор инициатора.|  
|**command_id**|**int**|Идентификатор команды.|  
|**partial_command**|**bit**|Показывает, частичная эта команда или нет.|  
|**command**|**varbinary (1024)**|Значение команды.|  
|**hashkey**|**int**|Только для внутреннего использования.|  
|**originator_lsn**|**varbinary (16)**|Определяет номер LSN для команды в порождающей публикации. Используется для одноранговой репликации транзакций.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
