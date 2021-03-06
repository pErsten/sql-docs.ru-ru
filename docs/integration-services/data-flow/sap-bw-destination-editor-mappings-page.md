---
description: Редактор назначений SAP BW (страница «Сопоставления»)
title: Редактор назначения SAP BW (страница "Сопоставления") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwdestination.columns.f1
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f1c92a8976e22648768c3f4986d9c1ff13a35f55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430806"
---
# <a name="sap-bw-destination-editor-mappings-page"></a>Редактор назначений SAP BW (страница «Сопоставления»)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Страница **Сопоставления** диалогового окна **Редактор назначений SAP BW** используется для сопоставления входных столбцов с целевыми столбцами.  
  
 Для получения дополнительных сведений о назначении SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Назначение SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие страницы «Сопоставления»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В окне **Редактор назначений SAP BW**щелкните **Сопоставления** , чтобы открыть страницу редактора **Сопоставления** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки назначения, может потребоваться связаться с администратором SAP.  
  
 Страница **Сопоставления** **Редактора назначения SAP BW** состоит из двух разделов.  
  
-   Верхняя часть содержит доступные входные столбцы и целевые столбцы и используется для создания сопоставлений между этими двумя типами столбцов.  
  
-   Нижний раздел представляет собой таблицу, в которой указывается, какие входные столбцы были сопоставлены с какими целевыми столбцами.  
  
### <a name="upper-section-options"></a>Параметры в верхней области  
 Верхняя область содержит следующие параметры:  
  
 **Доступные входные столбцы**  
 Просмотрите список доступных входных столбцов.  
  
 Чтобы сопоставить входной столбец с целевым столбцом, перетащите столбец из списка **Доступные входные столбцы** и поместите этот столбец в столбец в списке **Доступные целевые столбцы** .  
  
 **Доступные целевые столбцы**  
 Просмотрите список доступных целевых столбцов.  
  
 Чтобы сопоставить входной столбец с целевым столбцом, перетащите столбец из списка **Доступные входные столбцы** и поместите этот столбец в столбец в списке **Доступные целевые столбцы** .  
  
 Верхний раздел также содержит контекстное меню, которое открывается при щелчке правой кнопкой мыши по фону. Это контекстное меню содержит следующие параметры.  
  
-   **Выбрать все сопоставления**  
  
-   **Удалить выбранные сопоставления**  
  
-   **Сопоставлять элементы по совпадению имен**  
  
### <a name="lower-section-columns"></a>Столбцы в нижнем разделе  
 Нижний раздел представляет собой таблицу сопоставлений и содержит следующие столбцы:  
  
 **Входной столбец**  
 Позволяет просматривать выбранные входные столбцы.  
  
 Для сопоставления другого входного столбца с тем же целевым столбцом выберите другой входной столбец в списке. Для удаления сопоставления выберите команду **\<ignore>** , чтобы исключить входной столбец из выходных данных.  
  
 **Целевой столбец**  
 Позволяет просмотреть каждый из доступных целевых столбцов без учета наличия или отсутствия сопоставления.  
  
## <a name="see-also"></a>См. также:  
 [Редактор назначений SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Редактор назначений SAP BW (страница "Вывод ошибок")](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [Редактор назначений SAP BW (страница "Дополнительно")](../../integration-services/data-flow/sap-bw-destination-editor-advanced-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
