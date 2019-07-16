---
title: Recordset-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: ede1415f-c3df-4cc5-a05b-2576b2b84b60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e76bc993b6f3fed781b8458bc7cf4a70081cd167
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931364"
---
# <a name="recordset-object-ado"></a>Recordset-Objekt (ADO)
Stellt die gesamte Gruppe von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Zu jedem Zeitpunkt den **Recordset** -Objekt verweist auf nur einen einzelnen Datensatz in der Gruppe als aktuellen Datensatz.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie **Recordset** Objekte zum Bearbeiten von Daten von einem Anbieter. Wenn Sie ADO verwenden, bearbeiten Sie Daten mithilfe von fast ausschließlich **Recordset** Objekte. Alle **Recordset** Objekte bestehen aus Datensätzen (Zeilen) und Feldern (Spalten). Abhängig von den Funktionen, die vom Anbieter unterstützt einige **Recordset** Methoden oder Eigenschaften möglicherweise nicht zur Verfügung.  
  
 ADODB. Recordset ist die ProgID, die verwendet werden soll, zum Erstellen einer **Recordset** Objekt. Vorhandene Anwendungen, die veraltete ADOR zu verweisen. Recordset ProgID ohne erneute Kompilierung funktioniert weiterhin, aber neue Entwicklungen sollten ADODB verweisen. Recordset.  
  
 Es gibt vier verschiedenen Cursortypen, die in ADO definiert:  
  
-   **Dynamische Cursor** können Sie Ergänzungen, Änderungen und löschungen von anderen Benutzern, anzeigen, können alle Arten von Verkehr über den **Recordset** , die Lesezeichen ermöglicht, wenn der Anbieter unterstützt und nicht abhängig von Lesezeichen. Diese.  
  
-   **Keyset-Cursor** Behaves wie einen dynamischen Cursor, mit dem Unterschied, dass die It Sie verhindert, dass Datensätze angezeigt, dass andere Benutzer hinzufügen und verhindert den Zugriff auf Datensätze, die andere Benutzer zu löschen. Datenänderungen durch andere Benutzer werden weiterhin angezeigt. Es unterstützt immer das Lesezeichen und ermöglicht daher alle Arten von Verkehr über den **Recordset**.  
  
-   **Static-Cursor** stellt eine statische Kopie einer Gruppe von Datensätzen, die Sie zum Suchen von Daten oder zum Generieren von Berichten; Cursortyp bietet eine und aus diesem Grund können alle Arten von Verkehr über den **Recordset**. Ergänzungen, Änderungen oder löschungen durch andere Benutzer werden nicht angezeigt. Dies ist die einzige Art von Cursor zulässig, wenn Sie eine clientseitige öffnen **Recordset** Objekt.  
  
-   **Vorwärtscursor** ermöglicht es Ihnen, nur vorwärts durch die **Recordset**. Ergänzungen, Änderungen oder löschungen durch andere Benutzer werden nicht angezeigt. Dies verbessert die Leistung in Situationen, in denen müssen Sie nur einen einzelnen Durchlauf durch, eine **Recordset**.  
  
 Festlegen der [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) Eigenschaft vor dem Öffnen der **Recordset** , wählen Sie den Cursor, oder übergeben Sie einen *CursorType* Argument mit der [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)Methode. Einige Anbieter unterstützen nicht alle Cursortypen. Überprüfen Sie die Dokumentation für den Anbieter. Wenn Sie nicht, dass einen anderer Cursortyp angeben, ADO einen Vorwärtscursor wird standardmäßig geöffnet.  
  
 Wenn die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient** zu öffnen eine **Recordset**, **UnderlyingValue** Eigenschaft [Feld](../../../ado/reference/ado-api/field-object.md) Objekte ist nicht verfügbar, in der zurückgegebenen **Recordset** Objekt. Wenn Sie mit einigen Anbietern (z. B. den Microsoft ODBC-Datenanbieter für OLE DB in Verbindung mit Microsoft SQL Server) verwendet wird, können Sie erstellen **Recordset** Objekte unabhängig von einem zuvor definierten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md)-Objekts durch Übergeben einer Verbindungszeichenfolge mit den **öffnen** Methode. ADO erstellt dennoch eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt, aber nicht das Objekt einer Objektvariablen zugewiesen. Aber wenn Sie mehrere öffnen **Recordset** Objekte über die gleiche Verbindung verwenden, sollten Sie explizit erstellen und öffnen Sie eine **Verbindung** Objekt; dieser weist die **Verbindung**Objekt einer Objektvariablen. Wenn Sie beim Öffnen nicht diese Objektvariable verwenden Ihre **Recordset** Objekten, die ADO erstellt ein neues **Verbindung** Objekt für jede neue **Recordset**, auch wenn Sie die gleichen übergeben die Verbindungszeichenfolge.  
  
 Sie können so viele erstellen **Recordset** Objekte nach Bedarf.  
  
 Beim Öffnen einer **Recordset**, der aktuelle Datensatz auf den ersten Datensatz positioniert ist (sofern vorhanden) und die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) Eigenschaften festgelegt werden, um **"false"** . Es sind keine Datensätze, die **BOF** und **EOF** eigenschafteneinstellungen werden **"true"** .  
  
 Können Sie die [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), **MoveLast**, **MoveNext**, und **MovePrevious** Methoden, die [verschieben](../../../ado/reference/ado-api/move-method-ado.md) Methode. und die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md), und [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaften, die Position des aktuellen Datensatzes an, wenn der Anbieter unterstützt das entsprechende die Funktionalität. Vorwärts gerichtete **Recordset** Objekte unterstützen nur die [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) Methode. Bei Verwendung der **verschieben** Methoden, um jeden Datensatz finden Sie unter (oder die Auflistung der **Recordset**), können Sie der **BOF** und **EOF** Eigenschaften bestimmen, ob Sie über den Anfang oder Ende des verschoben haben die **Recordset**.  
  
 Bevor die Funktionen von einer **Recordset** Objekt, rufen Sie die **unterstützt** Methode für das Objekt, um sicherzustellen, dass die Funktionalität unterstützt oder verfügbar ist. Verwenden Sie nicht die Funktionalität bei der **unterstützt** Methode gibt false zurück. Beispielsweise können Sie die **MovePrevious** Methode nur, wenn `Recordset.Supports(adMovePrevious)` gibt **"true"** . Andernfalls erhalten Sie einen Fehler, da die **Recordset** -Objekt wurde geschlossen, und die Funktionalität gerendert für die Instanz nicht verfügbar. Wenn eine Funktion, die Sie interessiert sind, nicht unterstützt wird, **unterstützt** wird ebenfalls "false" zurückgegeben. In diesem Fall sollten Sie die entsprechende Eigenschaft oder Methode aufrufen, für die **Recordset** Objekt.  
  
 **Recordset** Objekte unterstützen zwei Arten von aktualisieren: unmittelbare und als Batch. Beim sofortigen Update, alle Änderungen an Daten werden geschrieben, sofort an die zugrunde liegenden Datenquelle Wenn Sie rufen die [Update](../../../ado/reference/ado-api/update-method.md) Methode. Sie können auch Arrays Werte übergeben, als Parameter mit der [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) und **aktualisieren** Methoden und gleichzeitig mehrere Felder in einem Datensatz aktualisieren.  
  
 Wenn ein Anbieter unterstützt die Batch zu aktualisieren, müssen Sie können den Anbieter, Änderungen an mehr als einem Datensatz Zwischenspeichern und übertragen sie dann in einem einzigen Aufruf für die Datenbank mit der [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode. Dies gilt für Änderungen, die mithilfe der **AddNew**, **Update**, und [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md) Methoden. Nach dem Aufrufen der **UpdateBatch** -Methode, die Sie verwenden die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft für alle Datenkonflikte überprüfen, um deren Behebung.  
  
> [!NOTE]
>  Zum Ausführen einer Abfrage ohne eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt, und übergeben Sie eine Abfragezeichenfolge enthält, die die **öffnen** Methode eine **Recordset** Objekt. Allerdings eine **Befehl** Objekt ist erforderlich, wenn den Befehlstext beibehalten und erneut ausführen oder Verwenden von Abfrageparametern werden sollen.  
  
 Die [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft steuert die Zugriffsberechtigungen.  
  
 Die **Felder** Auflistung ist das Standardelement der **Recordset** Objekt. Daher sind der Code für die folgenden beiden Anweisungen äquivalent.  
  
```  
Debug.Print objRs.Fields.Item(0)  ' Both statements print   
Debug.Print objRs(0)              '  the Value of Item(0).  
```  
  
 Wenn eine **Recordset** -Objekt übergeben wird, über Prozesse, die nur der **Rowset** Werte sind gemarshallt, und die Eigenschaften des der **Recordset** Objekt werden ignoriert. Während der unmarshalling, die **Rowset** ist in einer neu erstellten entpackten **Recordset** Objekt, das auch die Eigenschaften auf die Standardwerte festlegt.  
  
 Die **Recordset** Objekt für die Skripterstellung sicher ist.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Recordset-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/recordset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
