---
title: Das Field-Objekt | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fc75b9a7ab93e3157d6594be15c0b2cc36456415
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726158"
---
# <a name="the-field-object"></a>Das Field-Objekt
Jede **Feld** Objekt in der Regel entspricht einer Spalte in einer Datenbanktabelle. Allerdings eine **Feld** können auch einen Zeiger auf einen anderen darstellen **Recordset**, als Kapitel bezeichnet. Ausnahmen, z. B. die Kapitelspalten, werden weiter unten in diesem Handbuch behandelt.  
  
 Verwenden der **Wert** Eigenschaft **Feld** Objekte festlegen oder Zurückgeben von Daten für den aktuellen Datensatz. Abhängig von den Funktionen der Anbieter verfügbar macht, einige Auflistungen, Methoden oder Eigenschaften eine **Feld** Objekt möglicherweise nicht zur Verfügung.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Feld** -Objekts können Sie folgende Möglichkeiten:  
  
-   Geben Sie den Namen eines Felds zurück, mit der **Namen** Eigenschaft.  
  
-   Anzeigen oder ändern Sie die Daten in das Feld mit dem **Wert** Eigenschaft. **Wert** ist die Standardeigenschaft der **Feld** Objekt.  
  
-   Zurückgeben von der grundlegenden Merkmale eines Felds mithilfe der **Typ**, **Genauigkeit**, und **NumericScale** Eigenschaften.  
  
-   Die deklarierte Größe eines Felds zurückgeben, indem die **DefinedSize** Eigenschaft.  
  
-   Zurückgeben von der tatsächlichen Größe der Daten in einem bestimmten Feld mithilfe der **ActualSize** Eigenschaft.  
  
-   Bestimmen, welche Arten von Funktionen für ein bestimmtes Feld unterstützt werden, mithilfe der **Attribute** Eigenschaft und **Eigenschaften** Auflistung.  
  
-   Bearbeiten Sie die Werte der Felder, die lange Binär- oder Zeichendaten Daten enthält, mithilfe der **AppendChunk** und **GetChunk** Methoden.  
  
 Beheben von Diskrepanzen bei Feldwerten während des BatchUpdates mithilfe der **OriginalValue** und **UnderlyingValue** Eigenschaften, wenn der Anbieter Batchaktualisierungen unterstützt.  
  
## <a name="describing-a-field"></a>Beschreibt ein Feld  
 Besprechen Sie den folgenden Themen werden Eigenschaften der [Feld](../../../ado/reference/ado-api/field-object.md) -Objekt, das Informationen darstellen, die beschreibt, die **Feld** Objekt selbst – d. h. Metadaten über das Feld. Diese Informationen können verwendet werden, um zu bestimmen, viel über das Schema der der **Recordset**. Zu diesen Eigenschaften zählen **Typ**, **DefinedSize** und **ActualSize**, **Namen**, und **NumericScale**und **Genauigkeit**.  
  
### <a name="discovering-the-data-type"></a>Ermitteln des Datentyps  
 Die **Typ** Eigenschaft gibt den Datentyp des Felds an. Der Datentyp, Enumerationskonstanten, die von ADO unterstützten finden Sie unter [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) in die *ADO Programmer's Reference*.  
  
 Für numerische Typen, z. B. Gleitkomma **Type**, erhalten Sie weitere Informationen. Die **NumericScale** Eigenschaft gibt an, wie viele Ziffern rechts vom Dezimaltrennzeichen verwendet werden, zur Darstellung von Werten für die **Feld**. Die **Genauigkeit** Eigenschaft gibt die maximale Anzahl von Ziffern für die Darstellung von Werten für die **Feld**.  
  
### <a name="determining-field-size"></a>Bestimmen die Größe des Felds  
 Verwenden der **DefinedSize** Eigenschaft zum Ermitteln der Datenkapazität von einem **Feld** Objekt.  
  
 Verwenden der **ActualSize** zurückzugebende die tatsächliche Länge der Eigenschaft ein **Feld** Wert des Objekts. Für alle Felder der **ActualSize** Eigenschaft ist schreibgeschützt. Wenn die Länge des ADO ermittelt werden kann die **Feld** Wert des Objekts, das **ActualSize** -Eigenschaft gibt **ActualSize**.  
  
 Die **DefinedSize** und **ActualSize** Eigenschaften haben unterschiedliche Zwecke. Betrachten Sie beispielsweise eine **Feld** Objekt mit dem deklarierten Typ **AdVarChar** und **DefinedSize** Eigenschaftswert von 50 enthält ein einzelnes Zeichen. Die **ActualSize** Eigenschaftswert zurückgegeben wird, die Länge in Bytes des einzelnen Zeichens.  
  
### <a name="determining-field-contents"></a>Bestimmen der Inhalt des Felds  
 Der Bezeichner der Spalte aus der Datenquelle wird dargestellt, indem der **Name** Eigenschaft der **Feld**. Die **Wert** Eigenschaft der **Feld** Objekt gibt, oder legt den tatsächlichen Dateninhalt des Felds fest. Dies ist die Standardeigenschaft.  
  
 Um die Daten in einem Feld zu ändern, legen die **Wert** -Eigenschaft auf einen neuen Wert des richtigen Typs. Cursortyp muss es sich um Updates, um den Inhalt eines Felds ändern, unterstützen. Datenbank-Überprüfung erfolgt nicht hier im Modus "Batch", daher müssen Sie auf Fehler überprüft beim Aufrufen **UpdateBatch** in einem solchen Fall. Einige Anbieter unterstützen außerdem das ADO **Feld** des Objekts **UnderlyingValue** und **OriginalValue** Eigenschaften bieten Unterstützung beim Beheben von Konflikten, wenn Sie versuchen Führen Sie die Batch-Updates. Informationen dazu, wie Sie solche Konflikte zu lösen, finden Sie unter [Bearbeiten von Daten](../../../ado/guide/data/editing-data.md).  
  
> [!NOTE]
>  **Recordset Field** Werte können nicht festgelegt werden, wenn Sie neue Anfügen **Felder** zu einem **Recordset**. Stattdessen neue **Felder** können angehängt werden, um ein geschlossenes **Recordset**. Die **Recordset** muss geöffnet und nur dann können Werte zugewiesen werden, diese **Felder**.  
  
### <a name="getting-more-field-information"></a>Weitere Informationen zu Feldern abrufen  
 ADO-Objekte verfügen über zwei Typen von Eigenschaften: integrierte und dynamische. An diesem Punkt ist nur die integrierten Eigenschaften der **Feld** Objekt haben bereits besprochen wurde.  
  
 Integrierte Eigenschaften sind diese Eigenschaften in ADO implementiert und kann sofort auf eine neue Objekt mithilfe der `MyObject.Property` Syntax. Sie werden nicht angezeigt, als **Eigenschaft** Objekte in ein Objekt des **Eigenschaften** Auflistung.  
  
 Dynamische Eigenschaften werden von den zugrunde liegenden Datenanbieter definiert und werden in der **Eigenschaften** Auflistung für den entsprechenden ADO-Objekts. Beispielsweise kann eine Eigenschaft, die für den Anbieter spezifisch angibt, ob eine **Recordset** Objekt unterstützt, Transaktionen oder aktualisieren. Diese zusätzlichen Eigenschaften werden angezeigt, als **Eigenschaft** Objekte in diesem **Recordset** des Objekts **Eigenschaften** Auflistung. Dynamische Eigenschaften verwiesen werden können, nur über die Auflistung, die mit der Syntax `MyObject.Properties(0)` oder `MyObject.Properties("Name")`.  
  
 Beide Arten der Eigenschaft kann nicht gelöscht werden.  
  
 Eine dynamische **Eigenschaft** Objekt verfügt über vier integrierte Eigenschaften selbst:  
  
-   Die **Namen** Eigenschaft ist eine Zeichenfolge, die die Eigenschaft identifiziert.  
  
-   Die **Typ** -Eigenschaft ist eine ganze Zahl, die den Datentyp der Eigenschaft angibt.  
  
-   Die **Wert** -Eigenschaft ist eine Variante, die die Einstellung der Eigenschaft enthält. **Wert** ist die Standardeigenschaft für eine **Eigenschaft** Objekt.  
  
-   Die **Attribute** -Eigenschaft ist eine **lange** -Wert, der die Merkmale der Eigenschaft für den Anbieter spezifisch angibt.  
  
 Die **Eigenschaften** Sammlung für die **Feld** Objekt enthält zusätzliche Metadaten über das Feld. Der Inhalt dieser Auflistung hängt von den Anbieter ab. Im folgenden Codebeispiel wird untersucht die **Eigenschaften** Auflistung des Beispiels **Recordset** eingeführt, die am Anfang dieses Abschnitts. Es sucht zuerst den Inhalt der Auflistung. Dieser Code verwendet die [OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), sodass die **Eigenschaften** Sammlung enthält Informationen, die für diesen Anbieter relevant.  
  
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
  
### <a name="dealing-with-binary-data"></a>Arbeiten mit Binärdaten  
 Verwenden der [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) Methode für eine **Feld** Objekt, das mit dem lange Binär-oder Zeichendatentypen zu füllen. In Situationen, in dem Systemspeicher beschränkt ist, können Sie die **AppendChunk** Methode, um lange Werte in Teilen und nicht in ihrer Gesamtheit zu bearbeiten.  
  
 Wenn die **AdFldLong** bit im der **Attribute** Eigenschaft eine **Feld** Objekt nastaven NA hodnotu **"true"**, können Sie die  **AppendChunk** Methode für dieses Feld.  
  
 Die erste **AppendChunk** rufen Sie für eine **Feld** Objekt schreibt Daten in das Feld, dass alle vorhandenen Daten. Nachfolgende **AppendChunk** Aufrufe an die vorhandenen Daten hinzufügen. Wenn von Daten auf ein Feld anfügen sind, und klicken Sie dann festlegen oder Lesen Sie den Wert eines anderen Felds im aktuellen Datensatz, wird das ADO davon ausgegangen, dass Sie die Daten an das erste Feld anfügen abgeschlossen haben. Aufrufen der **AppendChunk** Methode für das erste Feld in diesem Fall ADO interpretiert den Aufruf als eine neue **AppendChunk** Vorgang und die vorhandenen Daten überschrieben. Beim Zugriff auf Felder in anderen **Recordset** Objekte, die nicht Klonen des ersten **Recordset** Objekt wird nicht unterbrochen. **AppendChunk** Vorgänge.  
  
 Verwenden der **GetChunk** Methode für eine **Feld** Teils oder aller Daten lange Binär- oder Zeichendatentypen abzurufenden Objekts. In Situationen, in dem Systemspeicher beschränkt ist, können Sie die **GetChunk** Methode, um lange Werte in Teile, sondern in ihrer Gesamtheit zu bearbeiten.  
  
 Die Daten, die eine **GetChunk** Aufruf gibt zugewiesen *Variable*. Wenn *Größe* ist größer als die übrigen Daten, die **GetChunk** Methode gibt nur die verbleibenden Daten ohne Auffüllung *Variable* mit Leerzeichen. Wenn das Feld leer ist, ist die **GetChunk** Methode gibt einen null-Wert zurück.  
  
 Jeder nachfolgende **GetChunk** Aufruf ruft Daten ab, wo die vorherige **GetChunk** Aufruf beendet wurde. Allerdings rufen Daten aus einem Feld und klicken Sie dann festlegen oder lesen den Wert eines anderen Felds im aktuellen Datensatz, wird davon ausgegangen ADO, dass Sie das Abrufen von Daten aus dem ersten Feld abgeschlossen haben. Aufrufen der **GetChunk** Methode für das erste Feld in diesem Fall ADO interpretiert den Aufruf als eine neue **GetChunk** Vorgang und Lesen am Anfang der das beginnt. Beim Zugriff auf Felder in anderen **Recordset** Objekte, die nicht Klonen des ersten **Recordset** Objekt wird nicht unterbrochen. **GetChunk** Vorgänge.  
  
 Wenn die **AdFldLong** bit im der **Attribute** Eigenschaft eine **Feld** Objekt nastaven NA hodnotu **"true"**, können Sie die **GetChunk**  Methode für dieses Feld.  
  
 Wenn es kein aktueller Datensatz, ist bei der Verwendung der **GetChunk** oder **AppendChunk** Methode für eine **Feld** Objekt Fehler 3021 (kein aktueller Datensatz).  
  
 Ein Beispiel für die Verwendung dieser Methoden zum Bearbeiten von Binärdaten, finden Sie unter den [AppendChunk-Methode](../../../ado/reference/ado-api/appendchunk-method-ado.md) und [GetChunk-Methode](../../../ado/reference/ado-api/getchunk-method-ado.md) Beispiele in den *ADO Programmer's Reference*.
