---
title: Record-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Record
helpviewer_keywords:
- Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ffc515350bfff4307da382c05aae50ed1930802
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917359"
---
# <a name="record-object-ado"></a>Record-Objekt (ADO)
Stellt eine Zeile aus einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder dem Datenanbieter oder ein Objekt dar, das von einem semistrukturierten Datenanbieter zurückgegeben wird, z. b. eine Datei oder ein Verzeichnis.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Datensatz** -Objekt stellt eine Daten Zeile dar und weist einige konzeptionelle Ähnlichkeiten mit einem einzeiligen **Recordset**auf. Abhängig von den Funktionen Ihres Anbieters können **Daten Satz** Objekte direkt von Ihrem Anbieter zurückgegeben werden, statt eines einzeiligen **Recordsets**, z. b. Wenn eine SQL-Abfrage ausgeführt wird, die nur eine Zeile auswählt. Oder ein **Datensatz** -Objekt kann direkt von einem **Recordset** -Objekt abgerufen werden. Oder Sie können einen **Datensatz** direkt von einem Anbieter an teilweise strukturierte Daten (z. b. den Microsoft Exchange OLE DB-Anbieter) zurückgeben.  
  
 Sie können die Felder, die dem **Daten Satz** Objekt zugeordnet sind, mithilfe der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung für das **Datensatz** -Objekt anzeigen. ADO ermöglicht Objektwert Spalten einschließlich **Recordset**, **SAFEARRAY**und skalare Werte in der **Fields** -Auflistung von **Datensatz** -Objekten.  
  
 Wenn das **Datensatz** -Objekt eine Zeile in einem **Recordset**darstellt, ist es möglich, mit der [Source](../../../ado/reference/ado-api/source-property-ado-record.md) -Eigenschaft zu diesem ursprünglichen **Recordset** zurückzukehren.  
  
 Das **Datensatz** -Objekt kann auch von semistrukturierten Datenanbietern wie dem [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)verwendet werden, um Struktur strukturierte Namespaces zu modellieren. Jeder Knoten in der Struktur ist ein **Datensatz** -Objekt mit zugeordneten Spalten. Die Spalten können die Attribute dieses Knotens und andere relevante Informationen darstellen. Das **Datensatz** -Objekt kann sowohl einen Endknoten als auch einen nicht-Blattknoten in der Baumstruktur darstellen. Nicht Blattknoten haben andere Knoten als ihren Inhalt, aber Blattknoten haben keinen solchen Inhalt. Blattknoten enthalten in der Regel binäre Datenströme, und auch nicht Blattknoten können über einen standardmäßigen binären Stream verfügen. Eigenschaften für das **Datensatz** -Objekt identifizieren den Knotentyp.  
  
 Das **Datensatz** -Objekt stellt außerdem eine alternative Möglichkeit zum Navigieren hierarchisch organisiert Daten dar. Ein **Datensatz** -Objekt kann erstellt werden, um den Stamm einer bestimmten Unterstruktur in einer großen Struktur darzustellen, und neue **Daten Satz** Objekte können geöffnet werden, um untergeordnete Knoten darzustellen.  
  
 Eine Ressource (z. b. eine Datei oder ein Verzeichnis) kann durch eine absolute URL eindeutig identifiziert werden. Ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt wird implizit erstellt und auf das **Daten** Satz Objekt festgelegt, wenn der **Datensatz** mithilfe einer absolute URL geöffnet wird. Ein **Verbindungs** Objekt kann explizit auf das **Datensatz** -Objekt über die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft festgelegt werden. Die Dateien und Verzeichnisse, auf die über das **Verbindungs** Objekt zugegriffen werden kann, definieren den *Kontext* , in dem **Daten Satz** Vorgänge auftreten können.  
  
 Daten Änderungs-und Navigationsmethoden für das **Datensatz** -Objekt akzeptieren außerdem eine relative URL, die eine Ressource mit einem absolute URL oder dem **Verbindungs** Objekt Kontext als Ausgangspunkt verwendet.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Jedem **Datensatz** -Objekt ist ein **Verbindungs** Objekt zugeordnet. Daher können **Daten Satz** Objekt Vorgänge Teil einer Transaktion sein, indem Verbindungsmethoden für **Verbindungs** Objekte aufgerufen werden.  
  
 Das **Datensatz** -Objekt unterstützt keine ADO-Ereignisse und antwortet daher nicht auf Benachrichtigungen.  
  
 Mit den Methoden und Eigenschaften eines **Datensatz** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Legen Sie das zugeordnete **Verbindungs** Objekt mit der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft fest oder geben Sie es zurück  
  
-   Geben Sie Zugriffsberechtigungen mit der [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft an.  
  
-   Gibt ggf. die URL des Verzeichnisses zurück, das die durch den **Datensatz** dargestellte Ressource mit der Eigenschaft " [Parser-URL](../../../ado/reference/ado-api/parenturl-property-ado.md) " enthält.  
  
-   Gibt die absolute URL, relative URL oder **Recordsets** an, aus denen der **Datensatz** mit der [Source](../../../ado/reference/ado-api/source-property-ado-record.md) -Eigenschaft abgeleitet wird.  
  
-   Gibt den aktuellen Status des **Datensatzes** mit der [State](../../../ado/reference/ado-api/state-property-ado.md) -Eigenschaft an.  
  
-   Geben Sie den Typ des **Datensatzes** - *einfach* *, Auflistung*oder *strukturiertes Dokument* mit der [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)-Eigenschaft an.  
  
-   Beenden Sie die Ausführung eines asynchronen Vorgangs mit der [Cancel](../../../ado/reference/ado-api/cancel-method-ado.md) -Methode.  
  
-   Trennen Sie den **Datensatz** aus einer Datenquelle mit der [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode.  
  
-   Kopieren Sie die durch einen **Datensatz** dargestellte Datei oder das Verzeichnis mithilfe der [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) -Methode an einen anderen Speicherort.  
  
-   Löschen Sie die Datei bzw. das Verzeichnis und die Unterverzeichnisse, die durch einen **Datensatz** mit der [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md) -Methode dargestellt werden.  
  
-   Öffnen Sie ein **Recordset** , das die Zeilen enthält, die die Unterverzeichnisse und Dateien der Entität darstellen, die durch den **Datensatz** mit der [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md) -Methode dargestellt wird.  
  
-   Verschieben Sie die Datei bzw. das Verzeichnis und die Unterverzeichnisse, die durch einen **Datensatz** dargestellt werden, mit der [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) -Methode in einen anderen Speicherort.  
  
-   Ordnen Sie den **Datensatz** einer vorhandenen Datenquelle zu, oder erstellen Sie eine neue Datei oder ein Verzeichnis mit der [Open](../../../ado/reference/ado-api/open-method-ado-record.md) -Methode.  
  
 Das **Daten Satz** Objekt ist für die Skripterstellung sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Record-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Datensätze und Streams](../../../ado/guide/data/records-and-streams.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
