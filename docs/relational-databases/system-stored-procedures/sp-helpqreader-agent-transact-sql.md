---
description: sp_helpqreader_agent (Transact-SQL)
title: sp_helpqreader_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9bdc306ed3622690e97b721f96c99dbc8efe0d1e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89526759"
---
# <a name="sp_helpqreader_agent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает свойства агента чтения очереди. Данная хранимая процедура применяется на распространителе в базе данных распространителя или на издателе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @frompublisher = ] frompublisher` Указывает, вызывается ли хранимая процедура на издателе или на распространителе. *фромпублишер* имеет бит и значение по умолчанию 0. **1** означает, что хранимая процедура вызывается из издателя, а значение **0** означает, что хранимая процедура вызывается из распространителя.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента.|  
|**name**|**nvarchar (100)**|Имя агента.|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания агента.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, с которой запускается агент распространителя, которая возвращается в формате *домен* \\ *имя_пользователя*.|  
|**job_password**|**sysname**|По соображениям безопасности **\*\*\*\*\*\*\*\*\*\*** всегда возвращается значение.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpqreader_agent** используется в репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Если значение *фромпублишер* равно **1**, только члены предопределенной роли сервера **sysadmin** на издателе или члены предопределенной роли базы данных **db_owner** в базе данных публикации могут выполнять **sp_helpqreader_agent**. В противном случае только члены предопределенной роли сервера **sysadmin** на распространителе или члены предопределенной роли базы данных **db_owner** в базе данных распространителя могут выполнять **sp_helpqreader_agent**.  
  
## <a name="see-also"></a>См. также  
 [Включение обновляемых подписок для публикации транзакций](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
