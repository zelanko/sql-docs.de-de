---
description: Optimize – dynamische Eigenschaft (ADO)
title: Optimieren von Eigenschaften-Dynamic (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ce2367d550cc8e420c4a1a9bf9fd10fff9e94e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442912"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize – dynamische Eigenschaft (ADO)
Gibt an, ob für ein [Feld](../../../ado/reference/ado-api/field-object.md)ein Index erstellt werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **booleschen** Wert fest, der angibt, ob ein Index erstellt werden soll, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Index kann die Leistung von Vorgängen verbessern, die Werte in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)suchen oder sortieren. Der Index ist intern für ADO. in Ihrer Anwendung können Sie nicht explizit auf Sie zugreifen oder diese verwenden.  
  
 Um einen Index für ein Feld zu erstellen, legen Sie die Eigenschaft **optimieren** auf **true**fest. Legen Sie diese Eigenschaft auf " **false**" fest, um den Index zu löschen.  
  
 **Optimieren** ist eine dynamische Eigenschaft, die an die Auflistung der [Feld](../../../ado/reference/ado-api/field-object.md) Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) angehängt wird, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Optimierungs Eigenschaft (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Beispiel für eine Optimierungs Eigenschaft (VC + +)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)   
 [Find-Methode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort-Eigenschaft](../../../ado/reference/ado-api/sort-property.md)
