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
author: rothja
ms.author: jroth
ms.openlocfilehash: 187000a648ca2e5e28ba09f10e3dfe55fea51b1d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763131"
---
# <a name="clear-method-ado"></a>Clear-Methode (ADO)
Entfernt alle [Fehler](../../../ado/reference/ado-api/error-object.md) Objekte aus der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Clear** -Methode für die [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) -Auflistung, um alle vorhandenen [Fehler](../../../ado/reference/ado-api/error-object.md) Objekte aus der Auflistung zu entfernen. Wenn ein Fehler auftritt, löscht ADO automatisch die **Fehler** Auflistung und füllt sie mit **Fehler** Objekten auf der Grundlage des neuen Fehlers auf.  
  
 Einige Eigenschaften und Methoden geben Warnungen zurück, die in der **Fehler** Auflistung als **Fehler** Objekte angezeigt werden, aber die Ausführung eines Programms nicht anhalten. Vor dem Aufrufen der Methoden [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode für ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. oder legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für ein **Recordset** -Objekt fest, und nennen Sie die **Clear** -Methode für die **Errors** -Auflistung. Auf diese Weise können Sie die [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft der **Errors** -Auflistung lesen, um die zurückgegebenen Warnungen zu testen.  
  
## <a name="applies-to"></a>Gilt für  
 [Errors-Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Execute, Requery und Clear Methods (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Beispiel für Execute, Requery und Clear Methods (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Beispiel für Execute, Requery und Clear Methods (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Delete-Methode (ADO Fields-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)   
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
