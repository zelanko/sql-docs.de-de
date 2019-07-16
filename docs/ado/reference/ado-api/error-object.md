---
title: Error-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5018dc921267663d64037024ef21c82ac6e3f7c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932965"
---
# <a name="error-object"></a>Error-Objekt
Enthält Details über den Datenzugriff, die auf einem einzigen Vorgang im Zusammenhang mit der Anbieter beziehen.  
  
## <a name="remarks"></a>Hinweise  
 Alle Vorgänge im Zusammenhang mit ADO-Objekte kann ein oder mehrere Anbieterfehler generieren. Sobald ein Fehler auftritt, eine oder mehrere **Fehler** Objekte befinden sich der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung von der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Wenn ein anderer ADO-Vorgang einen Fehler generiert die **Fehler** Auflistung deaktiviert ist, und der neue Satz von **Fehler** Objekte befindet sich der **Fehler** Auflistung.  
  
> [!NOTE]
>  Jede **Fehler** Objekt stellt einen bestimmten Anbieterfehler, nicht für einen ADO-Fehler dar. ADO-Fehler werden Verfahren zur Ausnahmebehandlung der Laufzeit verfügbar gemacht. Z. B. in Microsoft Visual Basic, das Vorhandensein einer ADO-spezifischer Fehler löst ein **On Error** Ereignis und angezeigt werden, der **Fehler** Objekt. Eine vollständige Liste der ADO-Fehler, finden Sie unter den [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) Thema.  
  
 Sie erhalten eine **Fehler** Eigenschaften des Objekts, um spezifische Details zu den einzelnen Fehlern, einschließlich der folgenden erhalten:  
  
-   Die [Beschreibung](../../../ado/reference/ado-api/description-property.md) -Eigenschaft, die den Text des Fehlers enthält. Dies ist die Standardeigenschaft.  
  
-   Die [Anzahl](../../../ado/reference/ado-api/number-property-ado.md) -Eigenschaft, die enthält die **lange** Integer-Wert, der der Fehlerkonstante.  
  
-   Die [Quelle](../../../ado/reference/ado-api/source-property-ado-error.md) -Eigenschaft, die das Objekt identifiziert, die den Fehler ausgelöst. Dies ist besonders nützlich, wenn es mehrere **Fehler** Objekte in der **Fehler** Auflistung, die nach der eine Anforderung an eine Datenquelle.  
  
-   Die [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) und [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) Eigenschaften, die Informationen von SQL-Datenquellen bereitstellen.  
  
 Tritt ein Fehler auf, es befindet sich der **Fehler** Auflistung von der **Verbindung** Objekt. ADO unterstützt die Rückgabe von mehreren Fehlern durch einen einzelnen ADO-Vorgang, um Fehlerinformationen für den Anbieter spezifisch zu ermöglichen. Um diese umfassende Fehlerinformationen, die in einem Fehlerhandler zu erhalten, die entsprechenden Fehlerbehebung Funktionen der Sprache oder Umgebung, die mit dem Sie arbeiten, verwenden und geschachtelte Schleifen auflisten die Eigenschaften der einzelnen **Fehler** -Objekt in der **Fehler** Auflistung.  
  
> [!NOTE]
>  **Microsoft Visual Basic und VBScript Benutzer** , wenn keine gültige **Verbindung** Objekt ist, müssen Sie zum Abrufen von Fehlerinformationen von der **Fehler** Objekt.  
  
 Als Anbieter nur tun, ADO-löscht die **OLE-Fehlerinformationen** -Objekt, bevor Sie einen neuen Anbieterfehler durch einen Aufruf, der möglicherweise generieren konnte. Jedoch die **Fehler** Auflistung auf der **Verbindung** Objekt wird deaktiviert und aufgefüllt werden, nur, wenn der Anbieter einen neuen Fehler generiert, oder wenn der [deaktivieren](../../../ado/reference/ado-api/clear-method-ado.md) Methode wird aufgerufen.  
  
 Einige Eigenschaften und Methoden zurück Warnungen, als angezeigt **Fehler** Objekte in der **Fehler** Auflistung jedoch nicht die Ausführung eines Programms an. Vor dem Aufruf der [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methoden für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt; die [Öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode für eine **Verbindung** Objekt, oder legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft für eine **Recordset** Objekt, rufen Sie die **Löschen**Methode für die **Fehler** Auflistung. Auf diese Weise können Sie lesen die [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft der **Fehler** zurückgegebene Auflistung zum Prüfen auf-Warnungen.  
  
 Die **Fehler** Objekt ist nicht sicher für Skripting.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Error-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Errors-Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
