---
description: Привязка параметров по имени (именованные параметры)
title: Привязка параметров по имени (именованные параметры) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 75227b26b5f9f060089e6568e233d327e3f7faa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476846"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Привязка параметров по имени (именованные параметры)
Некоторые СУБД позволяют приложению указывать параметры хранимой процедуры по имени, а не по положению в вызове процедуры. Такие параметры называются *именованными параметрами*. ODBC поддерживает использование именованных параметров. В ODBC именованные параметры используются только в вызовах хранимых процедур и не могут использоваться в других инструкциях SQL.  
  
 Драйвер проверяет значение поля SQL_DESC_UNNAMED IPD, чтобы определить, используются ли именованные параметры. Если SQL_DESC_UNNAMED не имеет значение SQL_UNNAMED, драйвер использует имя в поле SQL_DESC_NAME IPD для обнаружения параметра. Чтобы привязать параметр, приложение может вызвать **SQLBindParameter** , чтобы указать сведения о параметре, а затем вызвать **SQLSetDescField** , чтобы задать поле SQL_DESC_NAME метода IPD. При использовании именованных параметров порядок параметра в вызове процедуры не важен, а номер записи параметра игнорируется.  
  
 Различие между неименованными параметрами и именованными параметрами заключается в связи между номером записи дескриптора и номером параметра в процедуре. Если используются неименованные параметры, первый маркер параметра связан с первой записью в дескрипторе параметра, которая, в свою очередь, связана с первым параметром (в порядке создания) в вызове процедуры. При использовании именованных параметров первый маркер параметра по-прежнему связан с первой записью дескриптора параметра, но связь между номером записи дескриптора и номером параметра в процедуре больше не существует. Именованные параметры не используют сопоставление номера записи дескриптора с позицией параметра процедуры; Вместо этого имя записи дескриптора сопоставляется с именем параметра процедуры.  
  
> [!NOTE]  
>  Если включено автоматическое заполнение IPD, драйвер заполнит дескриптор таким образом, чтобы порядок записей дескрипторов совпадал с порядком параметров в определении процедуры, даже если используются именованные параметры.  
  
 Если используется именованный параметр, все параметры должны быть именованными параметрами. Если какой-либо параметр не является именованным параметром, то ни один из параметров CA не будет иметь именованных параметров. Если существовало сочетание именованных параметров и неименованных параметров, поведение будет зависеть от драйвера.  
  
 В качестве примера именованных параметров Предположим, что SQL Server хранимая процедура была определена следующим образом:  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 В этой процедуре первый параметр, @title_id имеет значение по умолчанию, равное 1. Приложение может использовать следующий код для вызова этой процедуры, чтобы указать только один динамический параметр. Этот параметр представляет собой именованный параметр с именем " \@ Quote".  
  
```  
// Prepare the procedure invocation statement.  
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);  
  
// Populate record 1 of ipd.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                  30, 0, szQuote, 0, &cbValue);  
  
// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields  
// for record #1.  
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
// Assuming that szQuote has been appropriately initialized,  
// execute.  
SQLExecute(hstmt);  
```
