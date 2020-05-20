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
author: rothja
ms.author: jroth
ms.openlocfilehash: fd92fc3d88372047262b91378341bc9aadcb35ef
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761868"
---
# <a name="recordset-object-ado"></a>Recordset-Objekt (ADO)
Stellt den gesamten Satz von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Das **Recordset** -Objekt bezieht sich jederzeit auf einen einzelnen Datensatz innerhalb des Satzes als aktuellen Datensatz.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie verwenden **Recordset** -Objekte, um Daten von einem Anbieter zu bearbeiten. Wenn Sie ADO verwenden, bearbeiten Sie Daten fast vollständig mithilfe von **Recordset** -Objekten. Alle **Recordset** -Objekte bestehen aus Datensätzen (Zeilen) und Feldern (Spalten). Abhängig von der vom Anbieter unterstützten Funktionalität sind einige **Recordset** -Methoden oder-Eigenschaften möglicherweise nicht verfügbar.  
  
 ADODB. Recordset ist die ProgID, die zum Erstellen eines **Recordset** -Objekts verwendet werden soll. Vorhandene Anwendungen, die auf den veralteten Ador verweisen. Recordset ProgID funktioniert weiterhin ohne Neukompilieren, aber die neue Entwicklung sollte auf ADODB verweisen. Recordset.  
  
 Es gibt vier verschiedene Cursor Typen, die in ADO definiert sind:  
  
-   **Dynamischer Cursor** Ermöglicht das Anzeigen von Ergänzungen, Änderungen und Löschungen durch andere Benutzer. ermöglicht alle Arten von Verschiebungen durch das **Recordset** , das nicht auf Lesezeichen angewiesen ist. und erlaubt Lesezeichen, wenn Sie vom Anbieter unterstützt werden.  
  
-   **Keysetcursor** Verhält sich wie ein dynamischer Cursor, mit der Ausnahme, dass Sie keine Datensätze anzeigen können, die andere Benutzer hinzufügen, und den Zugriff auf Datensätze, die andere Benutzer löschen, verhindern. Datenänderungen von anderen Benutzern bleiben weiterhin sichtbar. Er unterstützt immer Lesezeichen und ermöglicht daher alle Arten von Verschiebungen durch das **Recordset**.  
  
-   **Statischer Cursor** Bietet eine statische Kopie eines Satzes von Datensätzen, die Sie zum Suchen von Daten oder Generieren von Berichten verwenden können. erlaubt Lesezeichen immer und ermöglicht daher alle Arten von Verschiebungen durch das **Recordset**. Ergänzungen, Änderungen oder Löschungen anderer Benutzer sind nicht sichtbar. Dies ist der einzige Typ von Cursor, der zulässig ist, wenn Sie ein **Recordset** Client seitiges Recordsetobjekt öffnen.  
  
-   **Vorwärts Cursor** Ermöglicht Ihnen nur den Bildlauf vorwärts durch das **Recordset**. Ergänzungen, Änderungen oder Löschungen anderer Benutzer sind nicht sichtbar. Dies verbessert die Leistung in Situationen, in denen Sie nur einen einzigen Durchlauf durch ein **Recordset**machen müssen.  
  
 Legen Sie die [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) -Eigenschaft vor dem Öffnen des **Recordsets** fest, um den Cursortyp auszuwählen, oder übergeben Sie ein *CursorType* -Argument mit der [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode. Einige Anbieter unterstützen nicht alle Cursor Typen. Überprüfen Sie die Dokumentation für den Anbieter. Wenn Sie keinen Cursortyp angeben, öffnet ADO standardmäßig einen Vorwärts Cursor.  
  
 Wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient** festgelegt ist, um ein **Recordset**zu öffnen, ist die **UnderlyingValue** -Eigenschaft für [Feld](../../../ado/reference/ado-api/field-object.md) Objekte im zurückgegebenen **Recordset** -Objekt nicht verfügbar. Wenn Sie mit einigen Anbietern (z. b. dem Microsoft ODBC-Anbieter für OLE DB in Verbindung mit Microsoft SQL Server) verwendet werden, können Sie Recordset-Objekte unabhängig von einem zuvor definierten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt erstellen, indem Sie eine Verbindungs **Zeichenfolge** mit der **Open** -Methode übergeben. ADO erstellt weiterhin ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, weist dieses Objekt jedoch nicht einer Objektvariablen zu. Wenn Sie jedoch mehrere **Recordset** -Objekte über die gleiche Verbindung öffnen, sollten Sie explizit ein **Verbindungs** Objekt erstellen und öffnen. Dadurch wird das **Verbindungs** Objekt einer Objektvariablen zugewiesen. Wenn Sie diese Objekt Variable beim Öffnen der **Recordset** -Objekte nicht verwenden, erstellt ADO ein neues **Verbindungs** Objekt für jedes neue Recordset, auch wenn Sie dieselbe Verbindungs **Zeichenfolge**übergeben.  
  
 Sie können beliebig viele **Recordset** -Objekte erstellen.  
  
 Wenn Sie ein **Recordset**öffnen, wird der aktuelle Datensatz auf den ersten Datensatz (sofern vorhanden) und die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaften auf **false**festgelegt. Wenn keine Datensätze vorhanden sind, sind die **BOF** -und **EOF** -Eigenschafts Einstellungen **true**.  
  
 Sie können die Methoden " [muvefirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)", " **muvelast**", " **muvenext**" und " **muveprevious** " verwenden; die [Move](../../../ado/reference/ado-api/move-method-ado.md) -Methode. und die Eigenschaften [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)und [Filter](../../../ado/reference/ado-api/filter-property.md) zum Neupositionieren des aktuellen Datensatzes, vorausgesetzt, der Anbieter unterstützt die relevante Funktionalität. Forward-Only- **Recordsetobjekte** unterstützen [nur die-](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) Methode von "". Wenn Sie die **Move** -Methoden verwenden, um jeden Datensatz zu besuchen (oder das **Recordset**aufzulisten), können Sie die Eigenschaften **BOF** und **EOF** verwenden, um zu bestimmen, ob Sie über den Anfang oder das Ende des **Recordsets**hinaus verschoben haben.  
  
 Bevor Sie eine Funktion eines **Recordset** -Objekts verwenden, müssen Sie die **unter** stützte Methode für das-Objekt verwenden, um zu überprüfen, ob die Funktionalität unterstützt wird oder verfügbar ist. Die-Funktion darf nicht verwendet werden, wenn die **unterstützte** Methode false zurückgibt. Beispielsweise können Sie die Methode " **muveprevious** " nur verwenden, wenn " `Recordset.Supports(adMovePrevious)` **true**" zurückgibt. Andernfalls erhalten Sie eine Fehlermeldung, da das **Recordset** -Objekt möglicherweise geschlossen wurde und die Funktionalität auf der-Instanz nicht verfügbar gemacht wurde. Wenn eine Funktion, an der Sie interessiert sind, nicht unterstützt wird, wird von **unterstützt** auch false zurückgegeben. In diesem Fall sollten Sie den Aufruf der entsprechenden Eigenschaft oder Methode für das **Recordset** -Objekt vermeiden.  
  
 **Recordset** -Objekte können zwei Aktualisierungs Typen unterstützen: direkt und im Batch Modus. Beim sofortigen Aktualisieren werden alle Änderungen an den Daten sofort in die zugrunde liegende Datenquelle geschrieben, sobald Sie die [Update](../../../ado/reference/ado-api/update-method.md) -Methode aufgerufen haben. Sie können auch Arrays von Werten als Parameter mit den [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) -und **Update** -Methoden übergeben und mehrere Felder in einem Datensatz gleichzeitig aktualisieren.  
  
 Wenn ein Anbieter die Batch Aktualisierung unterstützt, können Sie den Anbieter Cache an mehr als einem Datensatz ändern und ihn dann mithilfe der [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode in einem einzigen Daten Bank aufrufsvorgang übertragen. Dies gilt für Änderungen, die mit den **AddNew**-, **Update**-und [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) -Methoden vorgenommen wurden. Nachdem Sie die **UpdateBatch** -Methode aufgerufen haben, können Sie die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) -Eigenschaft verwenden, um Daten Konflikte zu überprüfen, um Sie zu beheben.  
  
> [!NOTE]
>  Wenn Sie eine Abfrage ohne ein [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt ausführen möchten, übergeben Sie eine Abfrage **Zeichenfolge** an die **Open** -Methode eines Recordset-Objekts. Ein **Command** -Objekt ist jedoch erforderlich, wenn Sie den Befehls Text persistent speichern und erneut ausführen oder Abfrage Parameter verwenden möchten.  
  
 Die [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft steuert die Zugriffsberechtigungen.  
  
 Die **Fields** -Auflistung ist das Standardmember des **Recordset** -Objekts. Folglich sind die folgenden zwei Code Anweisungen Äquivalent.  
  
```  
Debug.Print objRs.Fields.Item(0)  ' Both statements print   
Debug.Print objRs(0)              '  the Value of Item(0).  
```  
  
 Wenn ein **Recordset** Recordsetobjekt über Prozesse hinweg übermittelt wird, werden nur die **rowsetwerte** gemarshallt, und die Eigenschaften des **Recordset** -Objekts werden ignoriert. Beim Unmarshalling wird das **Rowset** in ein neu erstelltes Recordsetobjekt entpackt, das auch seine Eigenschaften auf die Standardwerte festlegt. **Recordset**  
  
 Das **Recordset** -Objekt ist für die Skripterstellung sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Recordset-Objekteigenschaften,-Methoden und-Ereignisse](../../../ado/reference/ado-api/recordset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
