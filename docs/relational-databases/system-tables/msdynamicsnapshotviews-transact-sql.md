---
description: MSdynamicsnapshotviews (Transact-SQL)
title: Мсдинамикснапшотвиевс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotviews_TSQL
- MSdynamicsnapshotviews
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotviews system table
ms.assetid: 4fc1822a-5d6e-4034-a2e2-363210232d3b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6a89b139970822482e8b0745d9ceeefe8bba3f94
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538276"
---
# <a name="msdynamicsnapshotviews-transact-sql"></a>MSdynamicsnapshotviews (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **мсдинамикснапшотвиевс** отслеживает все временные представления моментальных снимков отфильтрованных данных, созданные агентом моментальных снимков, и используется системой для очистки представлений в случае аварийного завершения работы агент SQL Server или агент моментальных снимков. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dynamic_snapshot_view_name**|**sysname**|Имя временного представления моментального снимка отфильтрованных данных.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
