---
title: Optimieren Sie die dynamische Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d461d0fad834dfc3c3c6f22ec64cc4987eca6fa5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240043"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize – dynamische Eigenschaft (ADO)
Gibt an, ob ein Index erstellt werden soll, auf eine [Feld](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **booleschen** Wert, der angibt, ob ein Index erstellt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Ein Index kann steigern die Leistung von Vorgängen, die suchen oder Sortieren der Werte in einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Der Index ist für ADO intern. Sie können nicht explizit Zugriff auf oder verwenden es in Ihrer Anwendung.  
  
 Um einen Index auf ein Feld erstellen, legen die **optimieren** Eigenschaft **"true"**. Um den Index zu löschen, legen Sie diese Eigenschaft auf **"false"**.  
  
 **Optimieren** wird eine dynamische Eigenschaft angefügt der [Feld](../../../ado/reference/ado-api/field-object.md) Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung bei der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**.  
  
## <a name="usage"></a>Verwendung  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Optimize-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimieren Sie die Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)   
 [Find-Methode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort-Eigenschaft](../../../ado/reference/ado-api/sort-property.md)
