---
description: Пример формирования данных
title: Пример формирования данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], about data shaping
ms.assetid: 1bfdcad4-52e1-45bc-ad21-783657ef0a44
author: rothja
ms.author: jroth
ms.openlocfilehash: b6d6310e27db65576aac3ed79e699200dfa31c18
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991445"
---
# <a name="data-shaping-example"></a>Пример формирования данных
Следующая команда формирования данных показывает, как создать иерархический **набор записей** из таблиц **Customers** и **Orders** в базе данных Northwind.  
  
```  
SHAPE {SELECT CustomerID, ContactName FROM Customers}   
APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} AS chapOrders   
RELATE customerID TO customerID)   
```  
  
 Если эта команда используется для открытия объекта **Recordset** (как показано в [Visual Basic примере формирования данных](./visual-basic-example-of-data-shaping.md)), он создает главу (**чапордерс**) для каждой записи, возвращенной из таблицы **Customers** . Эта глава состоит из подмножества **набора записей** , возвращаемого из таблицы **Orders** . В главе **чапордерс** содержатся все запрошенные сведения о заказах, размещенных данным клиентом. В этом примере глава состоит из трех столбцов: **OrderID**, **OrderDate**и **CustomerID**.  
  
 Первые две записи результирующего **набора записей** выглядят следующим образом:  
  
|CustomerID|ContactName|OrderID|OrderDate|CustomerID|  
|----------------|-----------------|-------------|---------------|----------------|  
|ALFKI|Мария андер|10643<br /><br /> 10692<br /><br /> 10702<br /><br /> 10835<br /><br /> 10952<br /><br /> 11011|1997-08-25<br /><br /> 1997-10-03<br /><br /> 1997-10-13<br /><br /> 1998-01-15<br /><br /> 1998-03-16<br /><br /> 1998-04-09|ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI|  
|ANATR|Ана Trujillo|10308<br /><br /> 10625<br /><br /> 10759<br /><br /> 10926|1996-09-18<br /><br /> 1997-08-08<br /><br /> 1997-11-28<br /><br /> 1998-03-04|ANATR<br /><br /> ANATR<br /><br /> ANATR<br /><br /> ANATR|  
  
 В команде SHAPE команда APPEND используется для создания дочернего **набора записей** , связанного с родительским **набором записей** (как возвращаемое из команды, зависящей от поставщика, непосредственно после ключевого слова Shape, которое было рассмотрено ранее) предложением Relate. Родительский и дочерний, как правило, имеют по крайней мере один столбец: значение столбца в строке родителя совпадает со значением столбца во всех строках дочернего элемента.  
  
 Существует второй способ использования команд SHAPE: а — для создания родительского **набора записей** из дочернего **набора записей**. Записи в дочернем **наборе записей** группируются, обычно с помощью предложения by, и одна строка добавляется к родительскому **набору записей** для каждой результирующей группы в дочернем объекте. Если предложение BY опущено, то дочерний **набор записей** будет формировать одну группу, а родительский **набор записей** будет содержать ровно одну строку. Это полезно для вычисления статистических выражений "общие итоги" по всему дочернему **набору записей**.  
  
 Конструкция команды SHAPE также позволяет программно создавать **набор записей**в форме формы. Затем можно получить доступ к компонентам **набора записей** программным способом или с помощью соответствующего визуального элемента управления. Команда Shape выдается как любой другой текст команды ADO. Дополнительные сведения см. [в разделе Общие команды формы](./shape-commands-in-general.md).  
  
 Независимо от способа формирования родительского **набора записей** он будет содержать столбец глав, который используется для связи его с дочерним **набором записей**. При необходимости родительский **набор записей** может также содержать столбцы, содержащие статистические выражения (SUM, min, Max и т. д.) над дочерними строками. Как родительский, так и дочерний **набор записей** могут содержать столбцы, содержащие выражение в строке **набора записей**, а также столбцы, которые являются новыми и изначально пустыми.  
  
 Этот раздел продолжится в следующем разделе.  
  
-   [Пример формирования данных (Visual Basic)](./visual-basic-example-of-data-shaping.md)