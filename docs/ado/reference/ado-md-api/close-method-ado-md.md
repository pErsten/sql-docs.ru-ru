---
description: Метод Close (многомерные объекты ADO)
title: Метод Close (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f4f0c1613b1ca0e33a4f325dbe3e326d56f76e6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987115"
---
# <a name="close-method-ado-md"></a>Метод Close (многомерные объекты ADO)
Закрывает открытый набор ячеек.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Remarks  
 Использование метода **Close** для закрытия объекта набора [ячеек](./cellset-object-ado-md.md) приведет к освобождению связанных данных, включая данные во всех связанных [ячейках](./cell-object-ado-md.md), [осях](./axis-object-ado-md.md), [Position](./position-object-ado-md.md)координатах или объектах- [элементах](./member-object-ado-md.md) . Закрытие набора **ячеек** не приводит к его удалению из памяти. можно изменить параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, присвойте переменной объекта значение **Nothing**.  
  
 Позже можно вызвать метод [Open](./open-method-ado-md.md) , чтобы повторно открыть набор **ячеек** с помощью той же или другой исходной строки. Пока объект набора **ячеек** закрыт, получение любых свойств или вызов методов, ссылающихся на базовые данные или метаданные, выдает ошибку.  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (объекты данных ActiveX (MD))](./axis-object-ado-md.md)   
 [Объект Cell (объекты данных ActiveX (MD))](./cell-object-ado-md.md)   
 [Объект Member (объекты данных ActiveX (MD))](./member-object-ado-md.md)   
 [Метод Open (объекты данных ActiveX (MD))](./open-method-ado-md.md)   
 [Объект «позиционирование» (объекты данных ActiveX (MD))](./position-object-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](./state-property-ado-md.md)