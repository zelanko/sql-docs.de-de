---
description: Optimize – dynamische Eigenschaft (ADO)
title: Optimieren von Eigenschaften-Dynamic (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 3393bbfbfbaeb50c6a608db92dae42bb29fb3b1d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990261"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize – dynamische Eigenschaft (ADO)
Gibt an, ob für ein [Feld](./field-object.md)ein Index erstellt werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **booleschen** Wert fest, der angibt, ob ein Index erstellt werden soll, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Index kann die Leistung von Vorgängen verbessern, die Werte in einem [Recordset](./recordset-object-ado.md)suchen oder sortieren. Der Index ist intern für ADO. in Ihrer Anwendung können Sie nicht explizit auf Sie zugreifen oder diese verwenden.  
  
 Um einen Index für ein Feld zu erstellen, legen Sie die Eigenschaft **optimieren** auf **true**fest. Legen Sie diese Eigenschaft auf " **false**" fest, um den Index zu löschen.  
  
 **Optimieren** ist eine dynamische Eigenschaft, die an die Auflistung der [Feld](./field-object.md) Objekt [Eigenschaften](./properties-collection-ado.md) angehängt wird, wenn die [Cursor Location](./cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
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
 [Field-Objekt](./field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Optimierungs Eigenschaft (VB)](./optimize-property-example-vb.md)   
 [Beispiel für eine Optimierungs Eigenschaft (VC + +)](./optimize-property-example-vc.md)   
 [Filter-Eigenschaft](./filter-property.md)   
 [Find-Methode (ADO)](./find-method-ado.md)   
 [Sort-Eigenschaft](./sort-property.md)