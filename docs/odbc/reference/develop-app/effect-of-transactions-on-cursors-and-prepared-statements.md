---
description: Влияние транзакций на курсоры и подготовленные инструкции
title: Воздействие транзакций на курсоры и подготовленные инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 495bb8455c3e13b88d2d3ae6b400c5c0f2167604
ms.sourcegitcommit: 0f484f32709a414f05562bbaafeca9a9fc57c9ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631680"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Влияние транзакций на курсоры и подготовленные инструкции
Фиксация или откат транзакции имеет одно из следующих последствий для курсоров и планов доступа:  
  
-   Все курсоры закрыты, и планы доступа для подготовленных инструкций в этом соединении удаляются или  
  
-   Все курсоры закрыты, и планы доступа для подготовленных инструкций в этом соединении остаются без изменений или 
  
-   Все курсоры остаются открытыми, и планы доступа для подготовленных инструкций для этого соединения остаются без изменений.  
  
 Например, предположим, что источник данных приводит к первому поведению в этом списке, что является наиболее узким из этих поведений. Теперь предположим, что приложение выполняет следующие действия:  
  
1.  Задает режим фиксации для фиксации вручную.  
  
2.  Создает результирующий набор заказов на продажу для инструкции 1.  
  
3.  Создает результирующий набор строк в заказе на продажу с инструкцией 2, когда пользователь выделяет этот заказ.  
  
4.  Вызывает **SQLExecute** для выполнения инструкции позиционированного обновления, подготовленной в инструкции 3, когда пользователь обновляет строку.  
  
5.  Вызывает **SQLEndTran** для фиксации инструкции позиционированного обновления.  
  
 Из-за поведения источника данных вызов **SQLEndTran** на шаге 5 приводит к тому, что он закрывает курсоры в инструкциях 1 и 2, а также удаляет план доступа для всех инструкций. Приложение должно повторно выполнить инструкции 1 и 2, чтобы создать результирующие наборы и заново подготовить инструкцию к оператору 3.  
  
 В режиме автоматической фиксации функции, отличные от **SQLEndTran** Commit Transactions:  
  
-   **SQLExecute** или **SQLExecDirect** в предыдущем примере, вызов **SQLExecute** на шаге 4 фиксирует транзакцию. В результате источник данных закрывает курсоры в инструкциях 1 и 2 и удаляет план доступа для всех инструкций этого соединения.  
  
-   **SQLBulkOperations** или **SQLSetPos** в предыдущем примере предположим, что на шаге 4 приложение вызывает функцию **SQLSetPos** с параметром SQL_UPDATE в инструкции 2, вместо выполнения инструкции позиционированного обновления в инструкции 3. Это фиксирует транзакцию и заставляет источник данных закрывать курсоры в инструкциях 1 и 2, а также отменять все планы доступа к этому соединению.  
  
-   **SQLCloseCursor** В предыдущем примере предположим, что когда пользователь выделяет другой заказ на продажу, приложение вызывает **SQLCloseCursor** в инструкции 2 перед созданием результатов строк для нового заказа на продажу. Вызов **SQLCloseCursor** фиксирует инструкцию **SELECT** , которая создала результирующий набор строк, и заставляет источник данных закрыть курсор в инструкции 1, а затем отклоняет все планы доступа к этому соединению.  
  
 Приложения, особенно приложения на основе экрана, в которых пользователь прокручивается по результирующему набору и обновляет или удаляет строки, должны быть внимательны к кодированию этого поведения.  
  
 Чтобы определить, как работает источник данных при фиксации или откате транзакции, приложение вызывает **SQLGetInfo** с параметрами SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR.
