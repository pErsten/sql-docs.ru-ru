---
description: Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных
title: Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 242e86a0ac74dacd8682825f25adab4a847a82e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500796"
---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  В [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] можно использовать прогнозирующий запрос в расширениях интеллектуального анализа данных (DMX) для прогнозирования неизвестных значений столбцов в новом наборе данных на основе результатов модели интеллектуального анализа данных.  
  
 Тип используемого запроса зависит от того, какие данные необходимо получить от модели. Если требуется создавать простые прогнозы в режиме реального времени, например соответствует ли потенциальный заказчик на веб-сайте «портрету» покупателя велосипеда, то следует использовать одноэлементный запрос. Если необходимо создать пакет прогнозов из набора вариантов, содержащихся в источнике данных, нужно использовать нормальный прогнозирующий запрос.  
  
## <a name="prediction-types"></a>Типы прогнозов  
 С помощью расширений интеллектуального анализа данных можно создавать следующие типы прогнозов.  
  
 Прогнозируемое соединение  
 Используется для создания прогнозов по входным данным на основе существующих шаблонов модели интеллектуального анализа данных. За этой инструкцией запроса должно следовать предложение **On** , которое предоставляет условия объединения между столбцами модели интеллектуального анализа данных и входными столбцами.  
  
 Естественное прогнозируемое соединение  
 Используется для создания прогнозов на основе имен столбцов модели интеллектуального анализа данных, точно совпадающих с именами столбцов таблицы, по которой выполняется запрос. В этой инструкции запроса не требуется предложение **On** , так как условие объединения создается автоматически на основе совпадающих имен между столбцами модели интеллектуального анализа данных и входными столбцами.  
  
 Пустое прогнозируемое соединение  
 Используется для получения наиболее вероятного прогноза без необходимости указания входных данных. При этом возвращается прогноз на основе исключительно содержимого модели интеллектуального анализа данных.  
  
 Одноэлементный запрос  
 Используется для создания прогноза путем указания данных запросу. Это полезная инструкция, так как она позволяет указать запросу единственный вариант и быстро получить результат. Например, с помощью запроса можно спрогнозировать вероятность покупки велосипеда лицом женского пола в возрасте 35 лет, состоящем в браке. Этому запросу не требуется внешний источник данных.  
  
## <a name="query-structure"></a>Структура запроса  
 Для построения прогнозирующего запроса в расширениях интеллектуального анализа данных используется комбинация следующих элементов:  
  
-   **ВЫБЕРИТЕ [ПЛОСКИЕ]**  
  
-   **Вверх**  
  
-   **Из** *\<model>* **прогнозируемое соединение**      
  
-   **ON**  
  
-   **WHERE**  
  
-   **ORDER BY**  
  
 Элемент **SELECT** прогнозирующего запроса определяет столбцы и выражения, которые будут отображаться в результирующем наборе, и может включать следующие данные:  
  
-   **Прогнозирование** или **PredictOnly** столбцов из модели интеллектуального анализа данных.  
  
-   Любой столбец входных данных, используемый при создании прогнозов.  
  
-   Функции, возвращающие столбец данных.  
  
 Элемент **из** *\<model>* **прогнозируемого объединения** определяет исходные данные, которые будут использоваться для создания прогноза. Для одноэлементного запроса — это последовательность значений, назначенных столбцам. Для пустого прогнозируемого соединения оставляется пустое значение.  
  
 Элемент **On** сопоставляет столбцы, определенные в модели интеллектуального анализа данных, со столбцами во внешнем наборе данных. При создании запроса пустого прогнозируемого соединения или естественного прогнозируемого соединения этот элемент включать не требуется.  
  
 Для фильтрации результатов прогнозирующего запроса можно использовать предложение **WHERE** . Для выбора наиболее вероятных прогнозов можно использовать предложение **Top** или **ORDER BY** . Дополнительные сведения об использовании этих предложений см. в разделе [SELECT &#40;DMX&#41;](../dmx/select-dmx.md).  
  
 Дополнительные сведения о синтаксисе инструкции PREDICTION см. в разделе [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-from-model-prediction-join-dmx.md) и [выберите &#60;модель&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
  
