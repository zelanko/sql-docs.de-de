---
title: Microsoft Cursor Service für OLE DB (ADO-Dienstkomponente) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d8b52f2cf665232c5e16677a257465d020c227c1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702737"
---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Microsoft Cursor Service für OLE DB-Übersicht
Der Microsoft Cursor Service für OLE DB ergänzt die Cursorfunktionen der Unterstützung von Datenanbietern. Daher nimmt der Benutzer die relativ einheitliche Funktionalität von allen Datenanbietern.

 Der Cursor-Dienst stellt dynamische Eigenschaften zur Verfügung und verbessert das Verhalten bestimmter Methoden. Z. B. die [optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) dynamische Eigenschaft ermöglicht das Erstellen temporärer Indizes, um bestimmte Vorgänge, z. B. erleichtern die [finden](../../../ado/reference/ado-api/find-method-ado.md) Methode.

 Der Cursor-Dienst ermöglicht die Unterstützung für Batchaktualisierungen in allen Fällen. Es simuliert auch noch leistungsfähigere Cursortypen, z. B. dynamic-Cursor, wenn ein Datenanbieter nur weniger leistungsfähige Cursor, wie z. B. statische Cursor angeben kann.

## <a name="keyword"></a>Schlüsselwort
 Legen Sie zum Aufrufen dieser Komponente Service die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) des Objekts [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**.

```vb
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Wenn der Cursor Service für OLE DB aufgerufen wird, werden die folgenden dynamischen Eigenschaften hinzugefügt, um die **Recordset** des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung. Die vollständige Liste der **Verbindung** und **Recordset** dynamische Objekteigenschaften finden Sie der [ADO dynamische Property-Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md). Die verknüpften Namen der OLE DB-Eigenschaft, sind ggf. in Klammern nach dem Namen des ADO-Eigenschaft enthalten.

 Änderungen an einigen dynamischen Eigenschaften sind nicht mit der zugrunde liegenden Datenquelle sichtbar, nachdem der Cursor Service aufgerufen wurde. Z. B. die *Befehlstimeout* Eigenschaft für eine **Recordset** werden nicht angezeigt, auf den zugrunde liegenden Datenanbieter.

```vb

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Wenn Ihre Anwendung der Cursor-Dienst muss, aber müssen Sie die dynamischen Eigenschaften für den zugrunde liegenden Anbieter festlegen, legen Sie die Eigenschaften vor dem Aufrufen der Cursor-Diensts. Befehl Objekt eigenschafteneinstellungen werden immer an den zugrunde liegenden Datenanbieter unabhängig von der Cursorposition übergeben. Aus diesem Grund können Sie auch ein Command-Objekt zum Festlegen der Eigenschaften zu einem beliebigen Zeitpunkt verwenden.

> [!NOTE]
>  Die dynamische Eigenschaft DBPROP_SERVERDATAONINSERT wird durch den Cursordienst nicht unterstützt, auch wenn sie von den zugrunde liegenden Datenanbieter unterstützt wird.

|Eigenschaftenname|Description|
|-------------------|-----------------|
|Auto Recalc (DBPROP_ADC_AUTORECALC)|Für Recordsets erstellt mit dem Data Shaping Service, dieser Wert gibt an, wie oft werden berechnete und aggregierte Spalten berechnet. Der Standardwert (Wert = 1) besteht darin, neu berechnen, wenn die Data Shaping Service bestimmt, dass die Werte geändert haben. Wenn der Wert 0 ist, werden nur die berechneten oder aggregierten Spalten berechnet, wenn die Hierarchie anfänglich erstellt wird.|
|Batchgröße (DBPROP_ADC_BATCHSIZE)|Gibt die Anzahl der updateanweisungen, die zusammengefasst werden können, bevor Sie mit dem Datenspeicher gesendet werden. Die weitere Anweisungen in einem Batch aus, die weniger Roundtrips an den Daten zu speichern.|
|Zwischenspeichern von untergeordneten Zeilen (DBPROP_ADC_CACHECHILDROWS)|Für Recordsets mit den Data Shaping Service erstellt wurde gibt dieser Wert an, ob untergeordneten Recordsets in einem Cache für die spätere Verwendung gespeichert werden.|
|Cursor-Engine-Version (DBPROP_ADC_CEVER)|Gibt die Version des Diensts Cursor verwendet wird.|
|Änderungsstatus (DBPROP_ADC_MAINTAINCHANGESTATUS) verwalten|Gibt den Text des Befehls für erneutes Synchronisieren von einem ein oder mehrere Zeilen in einen Join mit mehreren Tabellen verwendet.|
|[Optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Gibt an, ob ein Index erstellt werden soll. Bei Festlegung auf **"true"** , wird das temporäre Erstellen von Indizes, um die Ausführung bestimmter Vorgänge zu verbessern.|
|[Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Gibt den Namen des der **Recordset**. Kann auf die verwiesen wird in der aktuellen oder nachfolgenden Befehle für die datenstrukturierung sein.|
|[Resync-Befehl](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Gibt eine Zeichenfolge von benutzerdefinierten Befehl, mit dem die [Resync](../../../ado/reference/ado-api/resync-method.md) Methode bei der [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) Eigenschaft gültig ist.|
|[Eindeutige Katalogressource](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Gibt den Namen der Datenbank, die die Tabelle enthält die **eindeutige Tabelle** Eigenschaft.|
|[Eindeutiges Schema](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Gibt den Namen des Besitzers der Tabelle verwiesen wird, der **eindeutige Tabelle** Eigenschaft.|
|[Eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Gibt den Namen, der eine Tabelle in eine **Recordset** erstellt, die aus mehreren Tabellen, die von einfügungen, Updates oder Löschvorgänge geändert werden können.|
|Aktualisieren der Kriterien (DBPROP_ADC_UPDATECRITERIA)|Gibt an, welche Felder in der **, in denen** Klausel werden verwendet, um Konflikte, die während einer Aktualisierung auftreten zu behandeln.|
|[Aktualisieren Sie die erneute Synchronisierung](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Gibt an, ob die **Resync** Methode wird implizit aufgerufen, nachdem die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode (und sein Verhalten), wenn die **eindeutige Tabelle** Eigenschaft gültig ist.|

 Sie können auch festlegen oder Abrufen eine dynamische Eigenschaft durch Angabe seines Namens als Index für die **Eigenschaften** Auflistung. Beispielsweise erhalten und drucken Sie den aktuellen Wert des der [optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) dynamische Eigenschaft, klicken Sie dann einen neuen Wert festlegen, wie folgt:

```vb
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Verhalten der integrierten Eigenschaft
 Der Cursor Service für OLE DB wirkt sich auch das Verhalten bestimmter integrierte Eigenschaften.

|Eigenschaftenname|Description|
|-------------------|-----------------|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Ergänzen Sie die Typen der Cursor, die für die verfügbar sind ein **Recordset**.|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Ergänzen Sie die verfügbaren Typen von Sperren für eine **Recordset**. Aktiviert die batch-Updates.|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|Gibt an, eine oder mehrere Namen, die die **Recordset** sortiert wird und ob jedes Feld in aufsteigender oder absteigender Reihenfolge sortiert wird.|

## <a name="method-behavior"></a>Methodenverhalten
 Der Cursor Service für OLE DB aktiviert ist, oder beeinflusst das Verhalten von der [Feld](../../../ado/reference/ado-api/field-object.md) des Objekts [Append](../../../ado/reference/ado-api/append-method-ado.md) Methode und die **Recordset** des Objekts [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), und [speichern](../../../ado/reference/ado-api/save-method.md) Methoden.
