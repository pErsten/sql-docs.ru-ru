---
description: sys.services (Transact-SQL)
title: sys. Services (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.services
- services
- services_TSQL
- sys.services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.services catalog view
ms.assetid: 16d0b0c5-5cce-469b-aa3d-4b9248e0c085
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 27653c3cbc38f8d7cd2bdc46c4800fd3db4067db
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539521"
---
# <a name="sysservices-transact-sql"></a>sys.services (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Это представление каталога содержит строку для каждой службы в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя службы (с учетом регистра), уникальное в пределах базы данных. Не допускает значения NULL.|  
|**service_id**|**int**|Идентификатор службы. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор участника базы данных, владеющего этой службой. Допускает значение NULL.|  
|**service_queue_id**|**int**|Идентификатор объекта для очереди, которую использует эта служба. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
