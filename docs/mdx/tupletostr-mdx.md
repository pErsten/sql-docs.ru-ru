---
description: TupleToStr (многомерные выражения)
title: TupleToStr (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 69e81156b26d4becb05390c8684b433584793697
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487627"
---
# <a name="tupletostr-mdx"></a>TupleToStr (многомерные выражения)


  Возвращает строку в формате МНОГОМЕРных выражений, соответствующую указанному кортежу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
## <a name="remarks"></a>Комментарии  
 Эта функция используется для передачи строкового представления кортежа внешней функции для дальнейшего анализа. Возвращаемая строка заключается в фигурные скобки {} и каждый элемент, если несколько явно определены в кортеже, разделяются запятыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается строка ([DATE]. [ Календарный год]. & [2001], [Geography]. [Geography]. [Country]. & [США]):  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 Следующий пример возвращает точно такую же строку, как и предыдущий пример.  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
