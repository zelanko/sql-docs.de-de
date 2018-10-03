---
title: Clear-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e69e7d2d2a66ccb9df0e03f6f77849c502f3bf2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753218"
---
# <a name="clear-method-ado"></a>Clear-Methode (ADO)
Entfernt alle der [Fehler](../../../ado/reference/ado-api/error-object.md) Objekte aus der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **löschen** Methode für die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung So entfernen Sie alle vorhandenen [Fehler](../../../ado/reference/ado-api/error-object.md) Objekte aus der Auflistung. Wenn ein Fehler auftritt, ADO automatisch löscht die **Fehler** Auflistung und füllt es mit **Fehler** -Objekten auf Grundlage der neuen Fehler.  
  
 Einige Eigenschaften und Methoden zurück Warnungen, als angezeigt **Fehler** Objekte in der **Fehler** Auflistung jedoch nicht die Ausführung eines Programms an. Vor dem Aufruf der [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methoden für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt; die [Öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode für eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, oder legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft für eine **Recordset** Objekt, rufen Sie die **Löschen**Methode für die **Fehler** Auflistung. Auf diese Weise können Sie lesen die [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft der **Fehler** zurückgegebene Auflistung zum Prüfen auf-Warnungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Errors-Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Execute, Requery und Clear-Methode – Beispiel (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Delete-Methode (Fields-Collection – ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)   
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
