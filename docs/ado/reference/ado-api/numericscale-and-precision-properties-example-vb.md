---
description: Пример кода ADO свойства NumericScale и Precision (Visual Basic)
title: Пример кода ADO для свойств NumericScale и Precision (VB) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- NumericScale property [ADO], Visual Basic example
- Precision property [ADO], Visual Basic example
ms.assetid: 9c1e2322-c225-49d1-a120-a343f23cea73
author: rothja
ms.author: jroth
ms.openlocfilehash: ed3e4337c38ac11966e261b993beaef0f7f3113f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990425"
---
# <a name="numericscale-and-precision-properties-example-vb"></a>Примеры свойств NumericScale и Precision (VB)
В этом примере используются свойства [NumericScale](./numericscale-property-ado.md) и [Precision](./precision-property-ado.md) для просмотра числа и точности полей в таблице ***скидок*** базы данных ***pubs*** .  
  
```  
'BeginNumericScaleVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub NumericScaleX()  
  
    ' connection and recordset variables  
   Dim rstDiscounts As ADODB.Recordset  
   Dim Cnxn As ADODB.Connection  
   Dim fldTemp As ADODB.Field  
   Dim strCnxn As String  
   Dim strSQLDiscounts As String  
  
   ' Open connection  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "Provider='sqloledb';Data Source='MySqlServer';Initial Catalog='Pubs';Integrated Security='SSPI';"  
  
   Cnxn.Open strCnxn  
  
   ' Open recordset  
   Set rstDiscounts = New ADODB.Recordset  
   strSQLDiscounts = "Discounts"  
   rstDiscounts.Open strSQLDiscounts, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable  
  
   ' Display numeric scale and precision of  
   ' numeric and small integer fields  
   For Each fldTemp In rstDiscounts.Fields  
      If fldTemp.Type = adNumeric Or fldTemp.Type = adSmallInt Then  
         MsgBox "Field: " & fldTemp.Name & vbCr & _  
            "Numeric scale: " & _  
               fldTemp.NumericScale & vbCr & _  
            "Precision: " & fldTemp.Precision  
      End If  
   Next fldTemp  
  
    ' clean up  
   rstDiscounts.Close  
   Cnxn.Close  
   Set rstDiscounts = Nothing  
   Set Cnxn = Nothing  
  
End Sub  
'EndNumericScaleVB  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Field](./field-object.md)   
 [Свойство NumericScale (ADO)](./numericscale-property-ado.md)   
 [Объект Parameter](./parameter-object.md)   
 [Свойство Precision (ADO)](./precision-property-ado.md)