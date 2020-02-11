---
title: Fehlersammlung (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3c8f981d4dc40a4a6f618f3cca387379d51def9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932976"
---
# <a name="errors-collection-ado"></a>Errors-Collection (ADO)
Enthält alle Fehler Objekte, die als Reaktion auf einen einzelnen Anbieter [Fehler](../../../ado/reference/ado-api/error-object.md) erstellt wurden.  
  
## <a name="remarks"></a>Bemerkungen  
 Jeder Vorgang, der ADO-Objekte umfasst, kann einen oder mehrere Anbieter Fehler generieren. Bei jedem Fehler können mindestens ein **Fehler** Objekt in die **Fehler** Auflistung des [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts eingefügt werden. Wenn ein anderer ADO-Vorgang einen Fehler generiert, wird die **Fehler** Auflistung gelöscht, und der neue Satz von **Fehler** Objekten kann in der **Fehler** Auflistung abgelegt werden.  
  
 Jedes **Fehler** Objekt stellt einen bestimmten Anbieter Fehler dar, kein ADO-Fehler. ADO-Fehler werden dem Lauf zeitmechanismus zur Ausnahmebehandlung ausgesetzt. Beispielsweise löst das Auftreten eines ADO-spezifischen Fehlers in Microsoft Visual Basic ein [OnError](../../../ado/reference/rds-api/onerror-event-rds.md) -Ereignis aus und wird im **Err** -Objekt angezeigt.  
  
 ADO-Vorgänge, für die kein Fehler generiert wird, haben keine Auswirkung auf die **Fehler** Auflistung. Verwenden Sie die [Clear](../../../ado/reference/ado-api/clear-method-ado.md) -Methode, um die **Fehler** Auflistung manuell zu löschen.  
  
 Der Satz von **Fehler** Objekten in der **Fehler** Auflistung beschreibt alle Fehler, die als Reaktion auf eine einzelne Anweisung aufgetreten sind. Durch das Auflisten der spezifischen Fehler in der **Fehler** Auflistung können Ihre Fehlerbehandlungsroutinen die Ursache und den Ursprung eines Fehlers genauer ermitteln und die entsprechenden Schritte für die Wiederherstellung ausführen.  
  
 Einige Eigenschaften und Methoden geben Warnungen zurück, die in der **Fehler** Auflistung als **Fehler** Objekte angezeigt werden, aber die Ausführung eines Programms nicht anhalten. Bevor Sie die Methoden [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aufrufen, die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode für ein **Verbindungs** Objekt oder die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für ein **Recordset** -Objekt festlegen, wird die **Clear** -Methode für die **Errors** -Auflistung aufgerufen. Auf diese Weise können Sie die [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft der **Errors** -Auflistung lesen, um die zurückgegebenen Warnungen zu testen.  
  
> [!NOTE]
>  Eine ausführlichere Erläuterung der Art und Weise, wie ein einzelner ADO-Vorgang mehrere Fehler generieren kann, finden Sie im Thema **Fehler** Objekt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse der Fehlersammlung](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
