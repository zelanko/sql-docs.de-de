---
description: Error-Objekt
title: Error-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 03f02654e281d052ec8bbb9b8f9df041484cc005
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973661"
---
# <a name="error-object"></a>Error-Objekt
Enthält Details zu Datenzugriffs Fehlern, die sich auf einen einzelnen Vorgang beziehen, der den Anbieter einbezieht.  
  
## <a name="remarks"></a>Bemerkungen  
 Jeder Vorgang, der ADO-Objekte umfasst, kann einen oder mehrere Anbieter Fehler generieren. Wenn jeder Fehler auftritt, werden mindestens ein **Fehler** Objekt in die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung des [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts eingefügt. Wenn ein anderer ADO-Vorgang einen Fehler generiert, wird die **Fehler** Sammlung gelöscht, und der neue Satz von **Fehler** Objekten wird in die **Fehler** Auflistung eingefügt.  
  
> [!NOTE]
>  Jedes **Fehler** Objekt stellt einen bestimmten Anbieter Fehler dar, kein ADO-Fehler. ADO-Fehler werden dem Lauf zeitmechanismus zur Ausnahmebehandlung ausgesetzt. Beispielsweise löst das Auftreten eines ADO-spezifischen Fehlers in Microsoft Visual Basic ein **On Error** -Ereignis aus und wird im **Error** -Objekt angezeigt. Eine umfassende Liste der ADO-Fehler finden Sie im Thema [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) .  
  
 Sie können die Eigenschaften eines **Fehler** Objekts lesen, um bestimmte Details zu den einzelnen Fehlern zu erhalten, einschließlich der folgenden:  
  
-   Die [Description](../../../ado/reference/ado-api/description-property.md) -Eigenschaft, die den Fehlertext enthält. Dies ist die Standard Eigenschaft.  
  
-   Die [Number](../../../ado/reference/ado-api/number-property-ado.md) -Eigenschaft, die den **Long** -ganzzahligen Wert der Fehler Konstante enthält.  
  
-   Die [Source](../../../ado/reference/ado-api/source-property-ado-error.md) -Eigenschaft, die das Objekt identifiziert, das den Fehler ausgelöst hat. Dies ist besonders nützlich, wenn Sie mehrere **Fehler** Objekte in der **Fehler** Sammlung nach einer Anforderung an eine Datenquelle haben.  
  
-   Die [SQLSTATE](../../../ado/reference/ado-api/sqlstate-property.md) -und [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) -Eigenschaften, die Informationen aus SQL-Datenquellen bereitstellen.  
  
 Wenn ein Anbieter Fehler auftritt, wird er in die **Errors** -Auflistung des **Connection** -Objekts eingefügt. ADO unterstützt die Rückgabe von mehreren Fehlern durch einen einzelnen ADO-Vorgang, um für den anbieterspezifische Fehlerinformationen zuzulassen. Wenn Sie diese umfassenden Fehlerinformationen in einem Fehlerhandler abrufen möchten, verwenden Sie die entsprechenden fehlerabfang Funktionen der Sprache oder Umgebung, mit der Sie arbeiten, und verwenden Sie dann geschachtelte Loops, um die Eigenschaften der einzelnen **Fehler** Objekte in der **Fehler** Auflistung aufzulisten.  
  
> [!NOTE]
>  **Benutzer von Microsoft Visual Basic und VBScript** Wenn kein gültiges **Verbindungs** Objekt vorhanden ist, müssen Sie Fehlerinformationen aus dem **Fehler** Objekt abrufen.  
  
 Ebenso wie Anbieter löscht ADO das OLE- **Fehler Info** -Objekt, bevor ein-Befehl aufgerufen wird, der potenziell einen neuen Anbieter Fehler generieren könnte. Allerdings wird die **Fehler** Auflistung für das **Verbindungs** Objekt nur dann gelöscht und aufgefüllt, wenn der Anbieter einen neuen Fehler generiert oder wenn die [Clear](../../../ado/reference/ado-api/clear-method-ado.md) -Methode aufgerufen wird.  
  
 Einige Eigenschaften und Methoden geben Warnungen zurück, die in der **Fehler** Auflistung als **Fehler** Objekte angezeigt werden, aber die Ausführung eines Programms nicht anhalten. Vor dem Aufrufen der Methoden [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode für ein **Verbindungs** Objekt. oder legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für ein **Recordset** -Objekt fest, und nennen Sie die **Clear** -Methode für die **Errors** -Auflistung. Auf diese Weise können Sie die [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft der **Errors** -Auflistung lesen, um die zurückgegebenen Warnungen zu testen.  
  
 Das **Fehler** Objekt ist für die Skripterstellung nicht sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Error-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Fehlersammlung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
