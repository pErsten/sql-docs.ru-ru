---
description: Пространства имен
title: Пространства имен | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
author: rothja
ms.author: jroth
ms.openlocfilehash: 03d70d1e5df026e13e23c9759462f53114f4d2af
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980265"
---
# <a name="namespaces"></a>Пространства имен
Формат сохраняемости XML в ADO использует следующие четыре пространства имен.  
  
## <a name="remarks"></a>Remarks  
 Формат сохраняемости XML в ADO использует следующие четыре пространства имен.  
  
|Prefix|Описание|  
|------------|-----------------|  
|s|Ссылается на пространство имен XML-Data, содержащее элементы и атрибуты, определяющие схему текущего набора записей.|  
|dt|Ссылается на спецификацию определений типов данных.|  
|rs|Относится к пространству имен, содержащему элементы и атрибуты, относящиеся к свойствам и атрибутам набора записей ADO.|  
|з|Ссылается на схему текущего набора строк.|  
  
 Клиент не должен добавлять собственные теги к этим пространствам имен, как определено спецификацией. Например, клиент не должен определять пространство имен как "urn: schemas-microsoft-com: RowSet", а затем записывать что-то вроде "RS: Мйовнтаг". Дополнительные сведения о пространствах имен см. в статье [рекомендации по пространствам имен W3C в XML](http://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  ИДЕНТИФИКАТОР тега схемы должен быть "Ровсетсчема", а пространство имен, используемое для ссылки на схему текущего набора строк, должно указывать на "#RowsetSchema".  
  
 Обратите внимание, что префикс пространства имен — часть между двоеточием и знаком равенства — произвольная.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 Пользователь может определить его как любое имя, если это имя постоянно используется во всем документе XML. ADO всегда записывает "s", "RS", "DT" и "z", но эти имена префиксов не жестко закодированы в компоненте загрузки.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](./persisting-records-in-xml-format.md)