---
description: Members (набор) (многомерные выражения)
title: Members (Set) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0358f20d0aeba0e4d455fabadb6dc1e4361081e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341400"
---
# <a name="members-set-mdx"></a>Members (набор) (многомерные выражения)


  Возвращает набор элементов в измерении, уровне или иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Remarks  
 Если указано выражение иерархии, функция **Members (Set)** возвращает набор всех элементов в указанной иерархии, не включая вычисляемые элементы. Чтобы получить набор всех элементов, вычисляемых или иным образом, в иерархии используется функция [&#41;AllMembers &#40;многомерных выражений](../mdx/allmembers-mdx.md)  
  
 Если выражение уровня задано, функция **Members (Set)** возвращает набор всех элементов на указанном уровне.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения в этом случае разрешается в единственную видимую иерархию. Например, многомерное выражение Measures.Members является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все элементы иерархии Calendar Year в кубе Adventure Works.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 В следующем примере возвращается количество заказов за 2003 год для каждого элемента уровня `[Product].[Products].[Product Line]`. Функция **Members** возвращает набор, представляющий все элементы уровня.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
