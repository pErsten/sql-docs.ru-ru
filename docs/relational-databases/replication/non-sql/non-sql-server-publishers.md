---
description: издатели, отличные от издателей SQL Server
title: Издатели, отличные от издателей SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9560875e4db3a644644238b0140fadb33cf1877d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420448"
---
# <a name="non-sql-server-publishers"></a>издатели, отличные от издателей SQL Server  
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Публикация данных из источников, отличных от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], позволяет консолидировать данные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может использовать подписку на моментальные снимки или транзакционные данные, публикуемые из базы данных Oracle. Дополнительные сведения о публикациях из Oracle см. в статье [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает следующие разнородные сценарии для репликации транзакций и репликации моментальных снимков.  
  
-   Публикация данных с подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на подписчики, отличные от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   Публикация данных в Oracle и из Oracle имеет следующие ограничения:  

  |Репликация |2016 или более ранние версии |2017 или более поздние версии |
  |:-----------|:---------------|:-------------|
  |Репликация из Oracle |Поддержка только Oracle 10g или более ранних версий |Поддержка только Oracle 10g или более ранних версий |
  |Репликация в Oracle |Версии до Oracle 12c |Не поддерживается |
  | &nbsp; | &nbsp; | &nbsp; |


 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Публикация из баз данных, отличных от баз данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], прекрасно подходит для следующих сценариев:  
  
|Сценарий|Описание|  
|--------------|-----------------|  
|Развертывание приложений на платформе[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Ведите разработку с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Серверы промежуточного хранения данных|Поддерживайте синхронизацию промежуточных баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с базой данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
