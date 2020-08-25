---
description: Clear-Methode (ADO)
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
ms.openlocfilehash: 8b7ed940248230d1c7b74f6782abcb555a538021
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776269"
---
# <a name="clear-method-ado"></a>Clear-Methode (ADO)
Entfernt alle [Fehler](./error-object.md) Objekte aus der [Fehler](./errors-collection-ado.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Clear** -Methode für die [Errors](./errors-collection-ado.md) -Auflistung, um alle vorhandenen [Fehler](./error-object.md) Objekte aus der Auflistung zu entfernen. Wenn ein Fehler auftritt, löscht ADO automatisch die **Fehler** Auflistung und füllt sie mit **Fehler** Objekten auf der Grundlage des neuen Fehlers auf.  
  
 Einige Eigenschaften und Methoden geben Warnungen zurück, die in der **Fehler** Auflistung als **Fehler** Objekte angezeigt werden, aber die Ausführung eines Programms nicht anhalten. Vor dem Aufrufen der Methoden [Resync](./resync-method.md), [UpdateBatch](./updatebatch-method.md)oder [CancelBatch](./cancelbatch-method-ado.md) für ein [Recordset](./recordset-object-ado.md) -Objekt die [Open](./open-method-ado-connection.md) -Methode für ein [Verbindungs](./connection-object-ado.md) Objekt. oder legen Sie die [Filter](./filter-property.md) -Eigenschaft für ein **Recordset** -Objekt fest, und nennen Sie die **Clear** -Methode für die **Errors** -Auflistung. Auf diese Weise können Sie die [count](./count-property-ado.md) -Eigenschaft der **Errors** -Auflistung lesen, um die zurückgegebenen Warnungen zu testen.  
  
## <a name="applies-to"></a>Gilt für  
 [Errors-Collection (ADO)](./errors-collection-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Execute, Requery und Clear Methods (VB)](./execute-requery-and-clear-methods-example-vb.md)   
 [Beispiel für Execute, Requery und Clear Methods (VBScript)](./execute-requery-and-clear-methods-example-vbscript.md)   
 [Beispiel für Execute, Requery und Clear Methods (VC + +)](./execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch-Methode (ADO)](./cancelbatch-method-ado.md)   
 [Delete-Methode (ADO Fields-Auflistung)](./delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO Parameters-Sammlung)](./delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO-Recordset)](./delete-method-ado-recordset.md)   
 [Filter-Eigenschaft](./filter-property.md)   
 [Resync-Methode](./resync-method.md)   
 [UpdateBatch-Methode](./updatebatch-method.md)