---
title: Das Feld Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Field object [ADO]
ms.assetid: 7d1c4ad5-4be3-42ab-b516-e7133ca300bc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80e6576b236db44452c4e89b1d8f3bb8976ab120
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923987"
---
# <a name="the-field-object"></a>Das Field-Objekt
Jedes **Feld** Objekt entspricht in der Regel einer Spalte in einer Datenbanktabelle. Ein **Feld** kann jedoch auch einen Zeiger auf ein anderes **Recordset**darstellen, das als Kapitel bezeichnet wird. Ausnahmen, wie z. b. Kapitel Spalten, werden später in diesem Handbuch behandelt.  
  
 Verwenden Sie die **value** -Eigenschaft von **Feld** Objekten, um Daten für den aktuellen Datensatz festzulegen oder zurückzugeben. Abhängig von der vom Anbieter verfügbar gemachten Funktionalität sind einige Auflistungen, Methoden oder Eigenschaften eines **Feld** Objekts möglicherweise nicht verfügbar.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Feld** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Gibt den Namen eines Felds zurück, indem die **Name** -Eigenschaft verwendet wird.  
  
-   Anzeigen oder Ändern der Daten im Feld mithilfe der **value** -Eigenschaft. **Value** ist die Standard Eigenschaft des **Field** -Objekts.  
  
-   Gibt die grundlegenden Eigenschaften eines Felds zurück, indem die Eigenschaften **Type**, **Precision**und **NumericScale** verwendet werden.  
  
-   Gibt die deklarierte Größe eines Felds mithilfe der **DefinedSize** -Eigenschaft zurück.  
  
-   Gibt die tatsächliche Größe der Daten in einem bestimmten Feld zurück, indem die **ActualSize** -Eigenschaft verwendet wird.  
  
-   Bestimmen Sie mithilfe der **Attribute** -Eigenschaft und der **Properties** -Auflistung, welche Funktionstypen für ein bestimmtes Feld unterstützt werden.  
  
-   Bearbeiten Sie die Werte von Feldern mit langen Binär-oder Long-Zeichendaten mithilfe der **AppendChunk** -Methode und der **GetChunk** -Methode.  
  
 Auflösen von Abweichungen in Feldwerten beim Aktualisieren von Batches mithilfe der Eigenschaften **OriginalValue** und **UnderlyingValue** , wenn der Anbieter Batch Updates unterstützt.  
  
## <a name="describing-a-field"></a>Beschreiben eines Felds  
 In den folgenden Themen werden die Eigenschaften des [Field](../../../ado/reference/ado-api/field-object.md) -Objekts erläutert, die Informationen darstellen, die das **Feld** Objekt selbst beschreiben, d. h. Metadaten zu dem Feld. Diese Informationen können verwendet werden, um viel über das Schema des **Recordsets**zu bestimmen. Zu diesen Eigenschaften zählen **Type**, **DefinedSize** und **ActualSize**, **Name**und **NumericScale** und **Precision**.  
  
### <a name="discovering-the-data-type"></a>Ermitteln des Datentyps  
 Die **Type** -Eigenschaft gibt den Datentyp des Felds an. Die von ADO unterstützten Enumerationskonstanten des Datentyps werden in der *ADO-Programmier Referenz*unter " [datatypeer](../../../ado/reference/ado-api/datatypeenum.md) Enumeration" beschrieben.  
  
 Für numerische Gleit Komma Typen, z. b. **adNumeric**, können Sie weitere Informationen abrufen. Die **NumericScale** -Eigenschaft gibt an, wie viele Ziffern rechts vom Dezimaltrennzeichen verwendet werden, um Werte für das **Feld**darzustellen. Die **Precision** -Eigenschaft gibt die maximale Anzahl von Ziffern an, die zum Darstellen von Werten für das **Feld**verwendet werden.  
  
### <a name="determining-field-size"></a>Festlegen der Feldgröße  
 Verwenden Sie die **DefinedSize** -Eigenschaft, um die Datenkapazität eines **Feld** Objekts zu bestimmen.  
  
 Verwenden Sie die **ActualSize** -Eigenschaft, um die tatsächliche Länge des Werts eines **Feld** Objekts zurückzugeben. Die **ActualSize** -Eigenschaft ist für alle Felder schreibgeschützt. Wenn ADO die Länge des **Feld** Objekt Werts nicht ermitteln kann, gibt die **ActualSize** -Eigenschaft **adunknown**zurück.  
  
 Die **DefinedSize-Eigenschaft** und die **ActualSize** -Eigenschaft haben unterschiedliche Zwecke. Nehmen Sie beispielsweise ein **Feld** Objekt mit einem deklarierten Typ von **adVarChar** und einen **DefinedSize** -Eigenschafts Wert von 50, der ein einzelnes Zeichen enthält. Der Wert der **ActualSize** -Eigenschaft, der zurückgegeben wird, ist die Länge des einzelnen Zeichens in Byte.  
  
### <a name="determining-field-contents"></a>Bestimmen von Feldinhalten  
 Der Bezeichner der Spalte aus der Datenquelle wird durch die **Name** -Eigenschaft des **Felds**dargestellt. Die **value** -Eigenschaft des **Field** -Objekts gibt den tatsächlichen Dateninhalt des Felds zurück oder legt ihn fest. Dies ist die Standard Eigenschaft.  
  
 Um die Daten in einem Feld zu ändern, legen Sie die **value** -Eigenschaft auf einen neuen Wert des richtigen Typs fest. Der Cursortyp muss Aktualisierungen unterstützen, um den Inhalt eines Felds zu ändern. Die Daten Bank Überprüfung wird hier nicht im Batch Modus durchgeführt. Daher müssen Sie beim Aufrufen von **UpdateBatch** in einem solchen Fall nach Fehlern suchen. Einige Anbieter unterstützen auch die Eigenschaften **UnderlyingValue** und **OriginalValue** des ADO- **Feld** Objekts, um Sie bei der Behebung von Konflikten bei der Ausführung von Batch Updates zu unterstützen. Ausführliche Informationen zum Beheben solcher Konflikte finden Sie unter [Bearbeiten von Daten](../../../ado/guide/data/editing-data.md).  
  
> [!NOTE]
>  **Recordset-Feldwerte** können nicht festgelegt werden, wenn neue **Felder** an ein **Recordset**angehängt werden. Stattdessen können neue **Felder** an ein geschlossenes **Recordset**angehängt werden. Anschließend muss das **Recordset** geöffnet werden, und nur dann können diesen **Feldern**Werte zugewiesen werden.  
  
### <a name="getting-more-field-information"></a>Weitere Feldinformationen  
 ADO-Objekte verfügen über zwei Arten von Eigenschaften: integrierte und dynamische Eigenschaften. Bis zu diesem Punkt wurden nur die integrierten Eigenschaften des **Field** -Objekts erläutert.  
  
 Integrierte Eigenschaften sind die Eigenschaften, die in ADO implementiert werden und für jedes neue Objekt sofort verfügbar sind. `MyObject.Property` dabei wird die-Syntax verwendet. Sie werden in der **Properties** -Auflistung eines Objekts nicht als **Eigenschafts** Objekte angezeigt.  
  
 Dynamische Eigenschaften werden vom zugrunde liegenden Datenanbieter definiert und in der **Properties** -Auflistung für das entsprechende ADO-Objekt angezeigt. Beispielsweise kann eine spezifische Eigenschaft für den Anbieter angeben, ob ein **Recordset** -Objekt Transaktionen oder Aktualisierungen unterstützt. Diese zusätzlichen Eigenschaften werden in der **Properties** -Auflistung des **Recordset** -Objekts als **Eigenschafts** Objekte angezeigt. Auf dynamische Eigenschaften kann nur mithilfe der-Syntax `MyObject.Properties(0)` oder `MyObject.Properties("Name")`über die-Auflistung verwiesen werden.  
  
 Beide Arten von Eigenschaften können nicht gelöscht werden.  
  
 Ein dynamisches **Eigenschafts** Objekt verfügt über vier eigenständig integrierte Eigenschaften:  
  
-   Die **Name** -Eigenschaft ist eine Zeichenfolge, die die-Eigenschaft bezeichnet.  
  
-   Die **Type** -Eigenschaft ist eine ganze Zahl, die den Eigenschafts Datentyp angibt.  
  
-   Die **value** -Eigenschaft ist eine Variante, die die Eigenschafts Einstellung enthält. **Value** ist die Standard Eigenschaft für ein **Property** -Objekt.  
  
-   Die **Attribute** -Eigenschaft ist ein **langer** Wert, der die Merkmale der Eigenschaft angibt, die für den Anbieter spezifisch sind.  
  
 Die **Properties** -Auflistung für das **Field** -Objekt enthält zusätzliche Metadaten für das Feld. Der Inhalt dieser Sammlung variiert je nach Anbieter. Im folgenden Codebeispiel wird die **Properties** -Auflistung des Beispiel- **Recordsets** untersucht, das am Anfang dieses Abschnitts vorgestellt wurde. Zuerst wird der Inhalt der Auflistung untersucht. In diesem Code wird der [OLE DB Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)verwendet, sodass die **Properties** -Auflistung Informationen enthält, die für diesen Anbieter relevant sind.  
  
```  
'BeginFieldProps  
    Dim objProp As ADODB.Property  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
  
        For Each objProp In objFields(intLoop).Properties  
            Debug.Print vbTab & objProp.Name & " = " & objProp.Value  
        Next objProp  
    Next intLoop  
'EndFieldProps  
```  
  
### <a name="dealing-with-binary-data"></a>Umgang mit Binärdaten  
 Verwenden Sie die [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) -Methode für ein **Field** -Objekt, um Sie mit langen Binär-oder Zeichendaten auszufüllen. In Situationen, in denen der System Arbeitsspeicher eingeschränkt ist, können Sie die **AppendChunk** -Methode verwenden, um lange Werte in Teilen zu bearbeiten, anstatt sie vollständig zu verarbeiten.  
  
 Wenn das **adfldlong** -Bit in der **Attribute** -Eigenschaft eines **Feld** Objekts auf " **true**" festgelegt ist, können Sie die **AppendChunk** -Methode für dieses Feld verwenden.  
  
 Der erste **AppendChunk** -Befehl für ein **Field** -Objekt schreibt Daten in das-Feld, wobei alle vorhandenen Daten überschrieben werden. Nachfolgende **AppendChunk** -Aufrufe fügen vorhandenen Daten hinzu. Wenn Sie Daten an ein Feld Anfügen und dann den Wert eines anderen Felds im aktuellen Datensatz festlegen oder lesen, geht ADO davon aus, dass Sie mit dem Anfügen von Daten an das erste Feld fertig sind. Wenn Sie die **AppendChunk** -Methode erneut für das erste Feld aufzurufen, interpretiert ADO den-Befehl als neuen **AppendChunk** -Vorgang und überschreibt die vorhandenen Daten. Durch den Zugriff auf Felder in anderen **Recordset** -Objekten, die keine Klone des ersten **Recordset** -Objekts sind, werden **AppendChunk** -Vorgänge nicht gestört.  
  
 Verwenden Sie die **GetChunk** -Methode für ein **Field** -Objekt, um einen Teil oder alle langen Binär-oder Zeichendaten abzurufen. In Situationen, in denen der System Arbeitsspeicher eingeschränkt ist, können Sie die **GetChunk** -Methode verwenden, um lange Werte in Teilen zu bearbeiten, anstatt sie vollständig zu verwenden.  
  
 Die Daten, die von einem **GetChunk** -Rückruf zurückgegeben werden, werden einer *Variablen*zugewiesen. Wenn die *Größe* größer ist als die verbleibenden Daten, gibt die **GetChunk** -Methode nur die verbleibenden Daten ohne Auffüll *Variable* mit leeren Leerzeichen zurück. Wenn das Feld leer ist, gibt die **GetChunk** -Methode einen NULL-Wert zurück.  
  
 Jeder nachfolgende **GetChunk** -Befehl ruft Daten ab, von denen der vorherige **GetChunk** -Rückruf unterbrochen wurde. Wenn Sie jedoch Daten aus einem Feld abrufen und dann den Wert eines anderen Felds im aktuellen Datensatz festlegen oder lesen, geht ADO davon aus, dass Sie das Abrufen von Daten aus dem ersten Feld abgeschlossen haben. Wenn Sie die **GetChunk** -Methode erneut für das erste Feld aufrufen, interpretiert ADO den-Befehl als neuen **GetChunk** -Vorgang und beginnt mit dem Lesen vom Anfang der Daten. Durch den Zugriff auf Felder in anderen **Recordset** -Objekten, die keine Klone des ersten **Recordset** -Objekts sind, werden keine **GetChunk** -Vorgänge unterbrochen.  
  
 Wenn das **adfldlong** -Bit in der **Attribute** -Eigenschaft eines **Feld** Objekts auf " **true**" festgelegt ist, können Sie die **GetChunk** -Methode für dieses Feld verwenden.  
  
 Wenn bei Verwendung der **GetChunk** -Methode oder der **AppendChunk** -Methode für ein **Feld** Objekt kein aktueller Datensatz vorhanden ist, tritt der Fehler 3021 (kein aktueller Datensatz) auf.  
  
 Ein Beispiel für die Verwendung dieser Methoden zum Bearbeiten von Binärdaten finden Sie in den Beispielen für die [AppendChunk-Methode](../../../ado/reference/ado-api/appendchunk-method-ado.md) und die [GetChunk-Methode](../../../ado/reference/ado-api/getchunk-method-ado.md) in der *ADO-Programmier Referenz*.
